+++
title = "My first foray into performance benchmarking"
date = 2025-09-01
draft = false
description = "Quick blog about fine-tuning performance benchmarks with Rayon."
tags = ['personal-projects', 'coding']
keywords = ['Rust', 'Rayon', 'Rayon optimization', 'performance benchmarking', 'parallelism']
featured = "/2025/perf_over_time_line.png"
+++

In my free time I've been working on a Rust project, so-far named "txngraphs", to find, visualize, and measure token transfers in a graph-based format. You can read more about it [on the repo homepage](https://github.com/mud2monarch/txngraphs), and I presented [slides on the problem, with a POC,](https://docs.google.com/presentation/d/1j2BoZv-iszDs88wIsYS2kxomsdlOZNqOSjNmQhSGiKk/edit?usp=sharing) during Paradigm's recent Frontiers conference. One key component of the project is the ability to read directly from a [reth node database](https://reth.rs/), which unlocks the ability to conduct tolerably fast data analysis on token transfers.

My goal is to release a v0.1 of the tool. Relevant to this post, I'd like it to be as performant as reasonably possible.[^1] I'm not interested in maximizing performance to its theoretical limit (and potentially not yet skilled enough), but data analysis tools are more likely to be used when they're faster. My goal is only to pick the low-hanging fruit.

[^1]: I'd also like to expose a Python API, support ETH L1 and all Superchains, and add utilities for visualization and algorithmic analysis. Stay tuned.

Over the past two days I've been working on performance optimization, and I wanted to share my experience doing so as I've found it quite fun.

### Optimization Techniques
At its heart, `txngraphs` starts at a root address and looks for all ERC20 transfers of a specified token within a specified block range. If it finds a matching token transfer, it adds it to a list of addresses and will then look at all of *that* address's transfers within the block range. The program can be configured to stop at a `max_depth`, e.g., after two hops from the root address. In programming terms, this is a "breadth-first search."

To implement this feature, we need to iterate over every transaction in the block range and check if it's a matching token transfer. You can see why this tool is read-intensive, and why having local database access is crucial for making it usable.

As I said, my goal is only to pick the low-hanging fruit, and the lowest of low-hanging fruit is to chunk database reads and process them with [Rayon](https://docs.rs/rayon/latest/rayon/). Rayon is a Rust library with an incredibly simple API that allows you to parallelize iterators with just a single-line code change.

{{< figure
  src="/2025/perf_rayon_docs.png"
  alt="Snapshot of Rayon documentation showing a single-line change from iter() to par_iter()."
  class="img-caption"
  caption="Changing your function call from iter() to par_iter() slaps on parallelism."
 >}}

In my POC implementation, all work took place serially -- the program opened a single connection to the database and completed its work. This was a simple and straightforward approach, but it wasn't very performant. To improve performance, we can split the database reads into 'chunks' and use Rayon to give chunks to different CPU threads at the same time.

```rust
    // Define chunk size
    let chunk_size: u64 = 50000;
    // Split up the block range into chunks
    let chunks: Vec<(BlockNumber, BlockNumber)> = (*block_start..=*block_end)
        .step_by(chunk_size as usize)
        .map(|start| (start, std::cmp::min(start + chunk_size, *block_end)))
        .collect();
    // Process each chunk in parallel
    let all_transfers: Result<Vec<Vec<Transfer>>> = chunks
        .into_par_iter() // <- this parallelizes the processing
        .map(|(start_block, end_block)| {
            Self::process_chunk( // <- this is my business logic
                self.factory.clone(),
                *address,
                token_addresses.to_vec(),
                start_block,
                end_block,
            )
        })
        .collect();
```

### Benchmark suite
I wanted to make sure that I was measuring the performance of any changes to my code, so I wrote a [benchmark program](https://github.com/mud2monarch/txngraphs/blob/main/txngraphs/src/examples/benchmark.rs) and a [simple bash script](https://github.com/mud2monarch/txngraphs/blob/main/txngraphs/bench/bench-script.sh) that runs the benchmark multiple times across different workload sizes. That allowed me to test the performance of my code on multiple runs in a reproducible way.

To keep it simple, I tested the entire benchmark file end-to-end rather than running microbenchmarks of some kind (e.g., timing within the code). I just used the `time` command to measure the wall clock, CPU, and IO time.

I also wrote [some python scripts and other utils](https://github.com/mud2monarch/txngraphs/tree/main/txngraphs/bench) to parse the raw output, average results, and convert to CSV.

### Results from a naive rewrite

My first rewrite from serial/sequential processing to parallel processing saved about 25% (wall clock time). Pretty good for a quick change![^2]

[^2]: Admittedly, it took me like 2-3 hours... I started off thinking I should be using Tokio, didn't see any speedup, then realized I was CPU bound and should be using Rayon instead. Tokio says this in the docs 🤦. Oh well, good way to learn concurrency/parallelism and IO-bound/CPU-bound!

**Baseline results (commit eb31916)**

| Workload | Blocks | Real Time |
|----------|--------|-----------|
| Small    | 5K     | 0.32s     |
| Medium   | 20K    | 1.45s     |
| Large    | 100K   | 20.0s     |

**Naive Rayon re-write (commit 4d12ed1)**

| Workload | Blocks | Real Time |
|----------|--------|-----------|
| Small    | 5K     | 0.33s     |
| Medium   | 20K    | 1.06s     |
| Large    | 100K   | 14.66s    |

*Workloads are single-depth; only vary by number of blocks.*

Very nice!! We will definitely take a small refactor that yields a 25% improvement.

### Results from adjusting chunk sizes
The first thing to play around with is chunk size. In our code, we're splitting the workload into chunks of size *n*. There is some overhead to starting on a new chunk, so we need to find the right balance between chunk size and overhead. A larger chunk size can mean less overhead paid, but it might also mean that some threads finish their work sooner (e.g., if there are no token matches).

My initial implementation had a chunk size of 5,000 blocks. Here is how wall clock time changes with respect to chunk size:

{{< figure
  src="/2025/perf_chunk_one.png"
  alt="Line graph showing wall clock time vs chunk size."
  class="img-caption"
  caption="Y axis is wall clock time (i.e., the literal time to complete) in seconds, X axis is chunk size in number of blocks."
 >}}

As you can see, the sweet spot for chunk size appears to be between 50k and 75k blocks. That means we most efficiently balance our overhead (e.g., cloning items in memory, opening DB connections, etc.) when we ask a single thread to read 50k-75k blocks at a time.

### Results from adjusting Rayon threads
Rayon exposes another configuration option that we can adjust: the number of threads used for parallel processing. By default, Rayon will use the number of available CPU cores (in my case, on a MacBook Pro with the M1 Pro chip, eight performance cores), but we can specify a different number of threads to use by setting an environment variable `RAYON_NUM_THREADS` for our run.

Here's the same chart as above, but running with 6 threads rather than the default 8:

{{< figure
  src="/2025/perf_chunk_two.png"
  alt="Line graph showing wall clock time vs chunk size."
  class="img-caption"
  caption="Y axis is wall clock time (i.e., the literal time to complete) in seconds, X axis is chunk size in number of blocks."
 >}}

Pretty cool! We don't see much improvement moving from 8 threads to 6, but we do see a flatter curve (perhaps because fewer threads more evenly balances overhead cost vs. idle threads). We do see small performance improvements in the 100k and 200k task sizes, on average. Worth looking at!

### Results from Rayon auto-chunking
I also learned about Rayon's semi-auto-chunking feature, which can try to optimize work-stealing by adjusting chunk size automatically, within a provided range. You can do this by combining the `chunks()`, `with_min_len()`, and `with_max_len()` methods. Here's our rewrite:

```rust
    // Define a default chunk size
    let chunk_size: usize = 10000;
    // Typically you do not need to collect the Range into a Vec, but Rayon specifically
    // requires it for Range<u64> and larger (u)int Ranges (BlockNumber is an alias for u64).
    let block_range: Vec<BlockNumber> = (*block_start..=*block_end).collect();
    let all_transfers: Result<Vec<Vec<Transfer>>> = block_range
        .into_par_iter()
        // new code begins here
        .chunks(chunk_size)
        // setup the chunks such that each chunk is between [5000, 40000] elements.
        .with_min_len(5000)
        .with_max_len(40000)
        .map(|chunk| {
            let start_block = chunk[0];
            let end_block = chunk[chunk.len() - 1];
            Self::process_chunk(
                self.factory.clone(),
        ...
```
Here are the results:

| Workload   | Real (s) | User (s) | Sys (s) | std dev (real) |
|------------|----------|----------|---------|---------|
| 10K blocks | 0.58     | 0.53     | 0.03    | 0.01   |
| 40K blocks | 3.86     | 3.63     | 0.05    | 0.18   |
| 100K blocks | 19.30     | 18.59     | 0.18    | 0.45   |
| 200K blocks | 43.91     | 42.58     | 0.49    | 0.36   |
| 200K blocks, 2 depth | 87.83     | 84.90     | 1.08    | 0.43   |

Unfortunately that is much slower ☹️. I think the auto-chunking feature must have significant overhead for work-stealing. There may also be a performance hit to materializing the block range into a vector, although it's only up to 200k u64s, so I would think it's quite small ((64 bits/8 bytes) * 200k = 1,600KB/1.6MB).

### Conclusion
Pretty fun! I know I'm not "supposed" to do computer work on a sunny, 75 degree Labor Day, but it's what I enjoy 🙂. This was a cool "mini golf" in performance optimization. Here's where we ended up for the 100k task:

| Pass | Wall time | as % of OG |
|------|-----------|------------|
| Original implementation    | 20.0s      | 100%       |
| First Rayon re-write    | 14.66s      | 73.3%       |
| 8 threads @ 20k block chunks | 12.71s     | 63.5%      |
| 6 threads @ 20k block chunks | 12.44s +/- 0.22s     | 61.6%      |

I'm sure someone else can extract 5-10x perf, but not me, today, yet!
