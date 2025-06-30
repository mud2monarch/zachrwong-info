+++
title = "A lightweight introduction to TEEs and how they’re being used today"
date = 2025-05-15
draft = false
description = "A consumable introduction to TEEs with a non-technical-friendly walkthrough of how a TEE is being used for Ethereum block building."
tags = ['TEEs', 'explainers']
keywords = ['TEEs', 'ethereum block building', 'flashbots', 'buildernet', 'Intel TDX explanation']
featured = "/2025/tee_matching.webp"
+++
One of the most exciting areas of blockchain innovation is the use of “TEEs” to introduce *verifiability* in important systems. A “TEE” is a special kind of computer that has an embedded private key. The computer can use the private key to make verifiable attestations about its behavior.

As discussed prior in this blog (see [Gyges Lydias: Disaggregating Decentralization](https://paragraph.com/@mud2monarch/disaggregating-decentralization)), verifiability is one of the key goods provided by decentralization. In this case, even though a TEE may be run by a single party, it still provides valuable user protections worth pursuing.

In this article, I lightly explain what a TEE is and walk through a new initiative by Flashbots and BeaverBuild to introduce verifiable priority ordering within L1 blocks. We will:

1. Learn how a TEE introduces verifiability
2. Explain the Flashbots/BeaverBuild initiative
3. Verify one component of the initiative (priority ordering on ETH L1)

*These are my independent thoughts and do not necessarily represent the views of my employer.*

---

### **How a TEE works**

A TEE is a special computer processor, typically manufactured by Intel, that contains an embedded private key. For modern TEEs like Intel’s TDX, the TEE is functionally the same as the CPU. The CPU can be made available in cloud environments like Google Cloud or on bare metal providers. "TEE" stands for "Trusted Execution Environment" because users can trust the chip after verifying the attestation as described below.

The private key in the TEE is used in the same way we use private keys everyday: to prove the authenticity of some claim through a cryptographic signature. When we connect to our bank account, our browser authenticates the HTTPS connection with the bank’s server and verifying that the internet traffic is encrypted. When we send ETH to a friend, our wallet is signing transaction calldata with our private key which tells the network the transaction could only have been signed with our key.

For our purposes, a TEE produces a verifiable attestation by taking a “measure” of the virtual machine and programs deployed to the TEE, including the operating system kernel and all software loaded in, and signs and publishes an attestation of the hash of that software. You can think of this as putting all of the code into a string and hashing that string to produce a unique, deterministic, shorter signature.

{{< figure
  src="/2025/tee_matching.webp"
  alt="Diagram showing TEE verification"
  caption="Rebuild the same machine locally, produce an attestation, and compare it to the remote attestation to verify that the same code is running on the TEE."
  class="img-caption" >}}

To verify the signature, users, e.g., you and I, can rebuild the entire kernel and software from open source code and produce a hash of our local build. If we can produce the same hash provided by the TEE operator, then we know we have have verified exactly what software is being run on the TEE. This is very similar to how we verify open source smart contracts today — we compare the deployed bytecode of a smart contract, which is available onchain to anyone running a full node, to the source code provided by the publisher. If the bytecode of the source code matches that which is onchain, we can verify it is accurate.

In sum, using a TEE provides the quality of *verifiability* — an essential benefit of decentralization. If we can reproduce the hash then we know the source code we see is the source code in use. And once we know the source code that is in use, we can review the code to see exactly what is happening.

### Flashbots/BeaverBuild’s BuilderNet

Flashbots is a research and development organization focused on mitigating the negative externalities posed by MEV. They develop and operate MEV-Boost, a key component of ETH L1’s block building system that processes ~90% of ETH L1 blocks. BeaverBuild are one of two major ETH L1 block builders, and they also run a powerful “searching” operation, which means they compete to arbitrage economic opportunities on ETH L1.

{{< figure
  src="/2025/tee_builder_marketshare.webp"
  alt="Chart of Ethereum builder marketshare with beaverbuild in second place"
  caption="BeaverBuild typically builds ~35% of blocks."
  class="img-caption" >}}

Builders on ETH L1 construct blocks, which they send to validators through MEV-Boost. Because they send full blocks to validators, builders [have significant control](https://decrypt.co/298176/tornado-cash-dev-charges-dropped-sanctions-illegal#:~:text=He%20highlighted%20that%20%E2%80%9Cmajor%20builders%20actually%20censor%20ethereum%20transactions%20that%20are%20sanctioned.) over which transactions are included on ETH L1.

[BuilderNet is a new initiative](https://buildernet.org/blog/introducing-buildernet) to build a distributed system that will decrease the control builders have over transaction inclusion, and other important characteristics of ETH L1. The general idea is to construct a more verifiable, fair, resilient system that still offers competitive economics to profit-maximizing validators.

In order to achieve strong economics for validators, BuilderNet makes certain promises about how transactions sent to BuilderNet will be processed. For example, a user can send a transaction to BuilderNet and receive a rebate if her transaction generates MEV. Importantly, though, the user needs to trust that BuilderNet *will* provide the rebate prior to submitting her transaction. This is where TEEs come in: by running BuilderNet within TEEs (many of them; the system is distributed), users can verify that the code being run *will* provide the rebate that is promised. Hopefully you can see how the introduction of verifiability on arbitrary code expands the design space for decentralized systems.

### Priority ordering and censorship resistance

Most people think of the value of censorship resistance in the context of a nation-state conflict: perhaps a powerful country like Russia wants to [censor payments to dissidents like Alexei Navalny](https://www.coindesk.com/policy/2020/07/15/russian-activists-use-bitcoin-and-the-kremlin-doesnt-like-it). But it is also important for a more benign — but still important — application on blockchains: fair auctions.

One way to mitigate MEV is to use strict priority ordering: transactions within a block will be ordered based on descending priority fee paid by the transaction submitter. Because only one transaction can capture an available economic opportunity, priority ordering amounts to an implicit auction: the block builder is effectively ‘selling’ the opportunity to the highest bidder. For a more eloquent explanation, see [Priority Is All You Need by Dan Robinson and Dave White](https://www.paradigm.xyz/2024/06/priority-is-all-you-need).

One failure mode for a priority ordering auction is that the auctioneer, i.e., the block builder, is colluding with a bidder — or, in fact, is a bidder itself. This is not theoretical: this happens on ETH L1 today because BeaverBuild and Titan Builder are integrated searcher-builders. In this failure mode, the builder might position their own transactions ahead of other searchers’ transactions. This would break the priority ordering auction which would render the mechanism almost useless.

By running a block builder within a TEE, as BuilderNet is working on doing, searchers could verify that BuilderNet *will* order transactions by descending priority fee. If searchers can verify that the claimed behavior will actually be followed, they will be more likely to participate, and the system will be more efficient, with welfare accruing to all blockchain users in a well-designed system.

### How to verify BuilderNet is ordering transactions by priority fee

As discussed above, there is a two-step process to verify the behavior of a TEE:

1. Rebuild the TEE locally and compare your local attestation to the attestation provided by the TEE operator → this allows you to verify that the code that the operator claims is being run is actually being run
2. Examine the source code you built locally to see what it is doing → this allows you to verify that the code is doing what the operator says the code is doing

We’ll leave the first step to a later exercise; but today, we will audit the BuilderNet code to see if the code orders transactions by priority fee.

Flashbots [claim that BuilderNet uses rbuilder](https://buildernet.org/docs/os-services-builds#key-services), which, if you’re at all familiar with the typical naming conventions of Rust aficionados, is a block builder written in Rust. Again, we can only verify their claim by verifying their attestation, which is out of scope for this exercise. The rbuilder code, however, is [available on Github](https://github.com/flashbots/rbuilder/).

I will now attempt to explain Flashbots’ code in natural language for someone unfamiliar in Rust. Rust is pretty… f&🤖ked, for lack of a better word, so bear with me. I’ve stripped out a lot of the code, but I share the filepath and code line for each block if you want to read the full thing. For those of you who know Rust, the terminology will not be correct (I am writing for a Rust-unfamiliar audience), but I hope you will agree it is accurate.

*The code that shows rbuilder uses priority ordering*

We enter the block building process through the `build_block()` function. The function has a different behavior based on the `OrderPriority` parameter we use (that’s what the `<OrderPriorityType: OrderPriority>` angle brackets mean). Remember this.

```rust
// flashbots/rbuilder/crates/rbuilder/src/building/builders/ordering_builder.rs#227

// call build_block():

pub fn build_block<OrderPriorityType: OrderPriority>() {
	// [..some code..]
	
	// As part of building a block, we need to fill_orders():
	self.fill_orders(&mut block_building_helper, block_orders, build_start)?;
}
```
This kicks us to `fill_orders()` immediately below. In `fill_orders(),` we loop through all the “orders” (i.e., pending transactions) that can go into the block. 

```rust
// flashbots/rbuilder/crates/rbuilder/src/building/builders/ordering_builder.rs#261

// call fill_orders():

fn fill_orders<OrderPriorityType: OrderPriority>() {
	// [..some code..]
	
	// This kicks off a loop. It's saying "while we have a valid "sim_order",
	// keep calling pop_order() on block_orders."
	// "pop" is an intuitive verb if you think of block_orders as a "stack" of block orders.
	// We're "popping" the next order off the top of the stack.
	// pop_order() is defined in a different file...
  while let Some(sim_order) = block_orders.pop_order() {
	  // [..code which processes the order..]
  }

// flashbots/rbuilder/crates/rbuilder/src/building/block_orders/prioritized_order_store.rs#59

// When we call pop_order(), we call pop() on main_queue.
// Keep going...
pub fn pop_order(&mut self) {
    let (id, _) = self.main_queue.pop()?;
    
    // [..more code..]]
}

// flashbots/rbuilder/crates/rbuilder/src/building/block_orders/prioritized_order_store.rs#26

// main_queue is a PriorityQueue that is built with the OrderPriorityType that we flagged before.

pub struct PrioritizedOrderStore<OrderPriorityType> {
    main_queue: PriorityQueue<OrderId, OrderPriorityType>,
}
```

`PriorityQueue` , despite what it’s name might indicate in this context, is a non-Flashbots-specific function that implements a very high-performance data structure for sorting things. It is an open source and widely used primitive. In [the docs for that data structure](https://docs.rs/priority-queue/latest/priority_queue/priority_queue/struct.PriorityQueue.html#method.pop), we see that `pop()` pops the “item with the greatest priority.” 

{{< figure
  src="/2025/tee_pop_function.webp"
  alt="Documentation from the PriorityQueue library"
  class="img-caption img-600" >}}

Okay, we’re popping orders off a stack of block orders that sorts the stack based on “the greatest priority.” Now, we need to check if that priority is based on priority gas fee in our specific implementation!

***If we setup our block builder with OrderPriorityType of “OrderMevGasPricePriority” then we will pop orders based on priority gas fee.*** Let’s move over there.

The `PriorityQueue` library lets developers define the behavior based on the developer’s implementation of `cmp()`, which is short for “compare”. So Flashbots need to define comparison behavior for their specific use case. Let’s get back to rbuilder.

And we find the money line:

```rust
// flashbots/rbuilder/crates/rbuilder/src/building/block_orders/order_priority.rs#67

impl OrderMevGasPricePriorityCmp {

	// a function that defines the "cmp" function for this Type.
  fn cmp(a: &SimulatedOrder, b: &SimulatedOrder) -> Ordering {
      a.sim_value.mev_gas_price.cmp(&b.sim_value.mev_gas_price)
  }
}
```

It might not look like it 😭 — as I said, Rust is pretty wonky. But In Rust, this function returns an `Ordering`  which is [like a shorthand for *either*](https://doc.rust-lang.org/std/cmp/enum.Ordering.html) `Greater`, `Equal`, or `Less`.

So *if* `a.sim_value.mev_gas_price` > `b.sim_value.mev_gas_price` *then* the function will return `Greater` . It’s probably *approximately* clear that we’re comparing gas prices of two different orders, but let’s just double check here.

The `cmp()` function takes in two variables, `a` and `b` of type `SimulatedOrder`. We find `SimulatedOrder` in `primitives/mod.rs` , which is intuitive: these are the “primitive” types used throughout the codebase.

```rust
// flashbots/rbuilder/crates/rbuilder/src/primitives/mod.rs#L1089

// Define a "struct," which you can think of as a "thing" called SimulatedOrder
// Each SimulatedOrder has a field called "sim_value" which is itself a "thing" called SimValue.
// Scroll down.
pub struct SimulatedOrder {
		// [..other fields..]
    pub sim_value: SimValue,
    // [..other fields..]
}

// flashbots/rbuilder/crates/rbuilder/src/primitives/mod.rs#L1053

// Define a "struct" SimValue
// Each SimValue has an mev_gas_price that is of type U256, which is an
// "unsigned integer of size 256 bits."
// This is an integer that can be a max size of 2^256 (1.1579209e+77).

pub struct SimValue {
    // [..other fields..]
    // This is computed as coinbase_profit/gas_used so it includes not only gas tip but also payments made directly to coinbase
    pub mev_gas_price: U256,
    // [..other fields..]
}
```

Okay phew! We can now see that when we compare `a.sim_value.mev_gas_price` to `b.sim_value.mev_gas_price` , we are comparing two very large integers and that the function `cmp()` tells us whether the value for `a` is `Greater` than, `Less` than, or `Equal` to the value for `b`.

WOW! If you’ve made it this far without knowing Rust, great job. At this point, you can see if we configure rbuilder to sort by `OrderMevGasPricePriority` , then, when the block builder calls `pop_order()`, it will first pop orders that have the greatest `mev_gas_price` and process those first. That means that orders will be ordered within the block by `mev_gas_price` — exactly what we expect.

Therefore, the last thing we need to check is how the configuration is set. If we can verify that the config file in-use (i.e., by checking that the TEE attestation covers the config file (suffixed `.toml`, see `rbuilder/config-live-example.toml` for an example) has what we expect, then the block builder will sort orders by priority fee. One last go…

```toml
# flashbots/rbuilder/config-live-example.toml

[[builders]]
# [..configurations..]
sorting = "mev-gas-price"
```

In Rust, we use a library called `serde` (short for “serialize - deserialize”) to parse string arguments into the strict types that Rust needs in the program.

```rust
// flashbots/rbuilder/crates/rbuilder/src/building/mod.rs#L356

#[derive(Debug, Clone, Copy, PartialEq, Eq, Hash, Serialize, Deserialize)]
#[serde(rename_all = "kebab-case")]
pub enum Sorting {
    MevGasPrice,
    // [..more options..]
}
```

This is really, really confusing (I warned you…), but the `#[` blocks are like auto-transforms. What these say in natural language is something like “take a text input in kebab-case (e.g., “word-next-word-with-hyphens-looks-like-a-kebab”) and deserialize (parse) it into CamelCase (e.g., “CapsLookLikeACamelWhichIsRustStandardConvention”). If the text input ends up matching “MevGasPrice” then our `Sorting` setting will be MevGasPrice.

If we go to the `ordering_builder` , we see how the builder is initialized:

```rust
// flashbots/rbuilder/crates/rbuilder/src/building/builders/ordering_builder.rs#L42

// Our defined Sorting config goes into an OrderingBuilderConfig.
// Then scroll up..
pub struct OrderingBuilderConfig {
	// [..other fields..]
  pub sorting: Sorting,
}

// flashbots/rbuilder/crates/rbuilder/src/building/builders/ordering_builder.rs#L68

// when we run_ordering_builder(), we define our "builder" to use our config
pub fn run_ordering_builder<OrderPriorityType>(
	// this means that "config" must be of type OrderingBuilderConfig
  config: &OrderingBuilderConfig, 
) {
  let mut builder = OrderingBuilderContext::new(
      block_state.clone(),
      input.builder_name,
      input.ctx,
      config.clone(), // LOOK HERE
  );
```

Whew. As a final review, here’s what we know happens in the code:

- The builder builds blocks based on an `OrderPriorityType`
- If the `OrderPriorityType` is set to `OrderMevGasPricePriority`, then when we `pop()` orders off the stack, we will first pop orders with the greatest `mev_gas_price`
- We set the builder to use `OrderMevGasPricePriority` by passing the argument `sorting = "mev-gas-price"` into our `config.toml` file.

Therefore, what we need to verify from the TEE attestation is that:

- The BuilderNet TEE is running the same rbuilder code that we’ve reviewed here.
- The builder running in the TEE used a `config.toml` file that has the `sorting = "mev-gas-price"` line.

If we can verify all of that, then we ***know*** that transactions on BuilderNet ***will be*** sorted in priority order.

### Verifiability as a central good of decentralization

I’ve claimed before that decentralization may not be important for its own sake; instead, it seems good *for other things.* In this article, I’ve shown how TEEs introduce verifiability: by producing an attestation that can be locally verified against source code which any user can verify. I’ve also shown how users can take the next step and *actually verify* the behavior of the source code.

While much of this discussion is still somewhat theoretical — for example, I’m not currently aware if or where BeaverBuild publish TEE attestations to the code they’re running — I hope you can see the future design space for TEEs and a plausible pathway to get there.

*Verifiable* systems are important for fair, transparent, immutable, and censorship financial markets, and I’m more optimistic than ever that Ethereum DeFi is on the way to achieving that goal.