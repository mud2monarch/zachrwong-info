+++
title = "A short exploration of Solana MEV data"
description = "Data analysis of Solana MEV activity during September 2024."
date= 2024-10-22
tags= ["crypto", "mev", "data"]
keywords = ['crypto', 'Solana MEV', 'MEV', 'MEV analysis', 'Solana automated trading']
draft=false
+++

[Ghost](https://tryghost.xyz/graph) is a company that allows developers to create custom blockchain indexes using Solidity. They [recently published](https://x.com/0xGhostLogs/status/1843770831245050159) a dataset that contains 1.06m Solana transactions from September 2024 that they identified as atomic arbitrage\* transactions containing SOL/WSOL. This article quickly analyzes that dataset. Thanks to Ghost for making this available!

{{< callout type="custom" emoji="🕵️" title="\"Atomic Arbitrage\"" text="Atomic arbitrage is a type of arbitrage that takes place within a single set of transactions. For example, someone may notice that the SOL <> USDC and USDC <> USDT and USDT <> SOL prices provide an arbitrage opportunity, and closes it in a single block/slot. This would NOT include CEX-DEX arbitrage, which does not/cannot occur atomically." style="background-color: transparent; border: 3px solid #d340e0;" >}}

_The notebook for this article is available on [my Github.](https://github.com/mud2monarch/personal-projects/blob/main/Solana_atomic_arbs/Solana_atomic_arbs.ipynb)_

### Background and Dataset Schema

As some background on the Solana network operation/MEV landscape, Jito Labs develops an alternative Solana node implementation that adds new features to the original "Agave" client developed by Solana Labs ([now Anza](https://www.theblock.co/post/275156/former-solana-labs-members-form-anza-developer-shop-prepare-to-unveil-agave-validator-client)). The most relevant features for this article are the ability to submit transaction "[bundles](https://jito-labs.gitbook.io/mev/searcher-resources/bundles)," where the client executes transactions received sequentially and atomically, and add [Jito tips](https://jito-foundation.gitbook.io/mev/jito-solana/features#:~:text=Bundles%20can%20contain%20tips%2C%20which%20allows%20users%20to%20tip%20validators%20for%20priority%20treatment.) to transactions, which are side payments for priority inclusion.

Solana network validators can choose to run the Jito client rather than the Agave client, if they want to offer these features. They can also modify the client themselves, as it is open source. Likely because validators earn more revenue when they run the Jito client, 89% of Solana stake weight runs the Jito client as of 10/21/24, [according to Jito](https://www.jito.wtf/validators/). This makes the Jito client the de facto primary client implementation for the Solana network. You can see in [the Jito commit history](https://github.com/jito-foundation/jito-solana/commits/master/) that the Anza team contribute to Jito development.

While the Agave client has a concept of a priority fee, the need for Jito tips is described well [here](https://www.umbraresearch.xyz/writings/solana-fees-part-1#incentive-compatibility). At a high level, Jito takes 5% of tips ([corroboration](https://drive.google.com/file/d/1V_Ppv2IwzuKej9PTYd7DlksuI9INFfJZ/view?usp=sharing)), validators take a discretionary commission (market commission appears to be 7-10% according to [Stakewiz](https://stakewiz.com/)), and SOL stakers receive the rest. (as an aside, I believe validators can choose what txns to include. I don't think consensus requires inclusion based on priority fee, or intrablock ordering based on priority fee).

With that background, here is the schema for Ghost's dataset, with some analogies to EVM transactions, if helpful.

| Field | Description |
| --- | --- |
| sig | Signature (akin to tx hash) |
| slot | Slot number (akin to block number) |
| date\_cet | Date in Central European Time |
| in\_bundle | Whether the transaction is part of a Jito "bundle" |
| jito\_tip\_sol | The tip to the validator running the Jito client included with the transaction, in SOL. Akin to a priority fee. |
| revenue\_sol | The revenue from the arbitrage, calculated by Ghost |
| signer | The signer of the txn, or the wallet that sent the transaction. |
| program | The smart contract (called a "program" on Solana) with which the transaction interacted. |

*Note that everything in this article simply takes the dataset at face value. It may be possible that what is in the dataset may not be strictly the same as what happened **on Solana** itself (i.e., if the dataset is not accurate for some reason). That said, I have no reason to think the dataset is inaccurate! I just don't know :)*

### Basic interesting facts
- The total amount of atomic arbitrage revenue earned by arbitrageurs was 26,991 $SOL, or about $4.5m at current day constant price (10/22/24).
- The total amount of tips paid to validators running the Jito client was 5,141 $SOL, or about $856k at current day prices.
- This equates to just 19% of arbitrage opportunity paid to Jito proposers, which may indicate a relatively uncompetitive market. If the market were more competitive, proposers should receive more of the arbitrage opportunity because the slot leader is a monopolist on the economic opportunity.
- Additionally, just 33.7% of the transactions are included in a Jito bundle at all. I know that it is common practice for searchers to send a Jito transaction AND an Agave transaction, but this is still surprising, especially given Jito's 89% market share.
- For transactions sent to Jito, 47.6% of arbitrage opportunity is paid to Jito proposers.
- The total revenue from transactions in a bundle was 10,800 $SOL, or about $1.8m. This is equivalent to 40% of arbitrage revenue.

These datapoints indicate an interesting and surprising market structure in Solana atomic arbitrage. First, it appears relatively uncompetitive. If the market were more competitive, arbitrageurs would need to tip closer to the total arbitrage profit for a transaction (or else a competitor would tip higher and capture the opportunity). Second, although Jito has high penetration, and a product feature that seems great for atomic arbitrage (bundles), it doesn't end up being used as much as one might think.

### Short exam of opportunities

- There are 52 unique programs (i.e., smart contracts/apps) present in the dataset. A Solana "program" is like a smart contract in the EVM.
- The most-used program is `JUP6Lk...`, [the Jupiter aggregator](https://solscan.io/account/JUP6LkbZbjS1jKKwapdHNy74zcZ3tLUZoi5QNyVTaV4). It was arbitraged against 307k times (1/3rd of txns).
- The next-most arbitraged-against program is `E8uB9x...`, with 99k transactions (1/10th of txns).

Here's a histogram showing the number of transactions per program in the dataset. It's hard to say that much about these stats.

{{< figure
  src="/2024/sol_txn_count_vs_program_id-1-1024x477.png"
  alt="Histogram of transactions vs. program ID"
  class="img-caption" >}}

And some additional scatter plots for number of transactions vs total revenue and total tips per program.

{{< figure
  src="/2024/sol_txns_vs_rev_bipanel.png"
  alt="Scatter plots"
  class="img-caption" >}}

And probably the most interesting scatter, total tips vs total revenue.

{{< figure
  src="/2024/sol_scatter_tips_vs_rev_per_program-1.png"
  alt="Scatter plots"
  class="img-caption" >}}

Low tips but high revenue are probably the best programs for an arbitrageur; it implies they are capturing most of the arbitrage value available. The "best" programs, circled in red above (the three which yielded >1200 SOL in revenue but required <250 SOL in tips) are described below.

| Program | Jito tips paid to validator ($SOL) | Total revenue ($SOL) | Aggregate % opportunity paid as tip | Number of txns |
| --- | --- | --- | --- | --- |
| `3JmzqBoDLvNTPapBGCN7x23kTE5o7zkQ2fQhuyU3j9x6` | 153.1 | 2,493.1 | 6.1% | 28,090 |
| `7PWnthtTsGnSpR4JLENYVoCJ5y5XwgELVbqgp6TkAFaH` | 0 | 2,241.5 | 0% | 38,406 |
| `bank7GaK8LkjyrLpSZjGuXL8z7yae6JqbunEEnU9FS4` | 25.4 | 1,339.1 | 1.9% | 95,013 |
| All bundled txns | 5,141 | 10,800 | 47.6% | 356,867 |
| Full dataset | 5,141 | 26,991 | 19% | 1,059,953 |

Another interesting finding is that Jito use for these opportunities is relatively low.

| Program | Aggregate % opportunity paid as tip | % txns in Jito bundle |
| --- | --- | --- |
| `3Jmzq...` | 6.1% | 14.5% |
| `7PWnt...` | 0% | 0% |
| `bank7...` | 1.9% | 8.3% |
| Full dataset | 19% | 33.7% |

One hypothesis for this phenomenon is that just one market participant is running the strategy. And indeed that's what we find:

| Program | Number of unique transaction senders |
| --- | --- |
| `3Jmzq...` | 3 |
| `7PWnt...` | 1 |
| `bank7...` | 1 |
| Full dataset | 414 |

Except for `3Jmzq...`, which has three unique senders in the month of September. Did competitors discover the strategy during the month? Here's the number of unique senders over time:

{{< figure
  src="/2024/sol_3jms_num_searchers_over_time.png"
  alt="Scatter plots"
  class="img-caption" >}}

Doesn't seem like it. Hmm, let's see how each signer/sender is performing.

{{< figure
  src="/2024/sol_second_to_last_pic.png"
  alt="Scatter plots"
  class="img-caption" >}}

Again, pretty consistent! No big changes in the market for this opportunity over time.

The last thing I wanted to check that might indicate a change in competitiveness was increased use of Jito tips. If the amount of tips increased over time, that could indicate the opportunity set was growing more competitive.

{{< figure
  src="/2024/sol_last_pic.png"
  alt="Scatter plots"
  class="img-caption" >}}

So interesting! `9VP2W...` (must?) uses tips to win its opportunities... and it still wins the least of the three addresses!

As to what the program actually does? I have absolutely no idea, I cannot read a Solana block explorer.

*Thanks for reading :) These are my independent thoughts and do not necessarily represent the views of my employer.*