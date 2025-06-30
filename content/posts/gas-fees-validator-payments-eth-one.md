+++
title = "Exploration: Gas fees and validator payments on Ethereum"
date = 2023-08-30
draft = false
description = "A short data analysis of gas fees on Ethereum in 2023."
tags = ['data']
keywords = ['Ethereum block building', 'gas fees']
+++

Ethereum validator revenue [consists of three things](https://eth2book.info/capella/part2/incentives/#p_4): native protocol issuance, priority fees, and MEV. Native protocol issuance is well-understood and [scales with respect](https://eth2book.info/capella/part2/incentives/issuance/) to the square root of the number of validators. From what I can find, priority fees are less well-understood, and MEV even less so.

Understanding validator revenue is important because a number of exciting financial products are being built on top of validator yield. Most straightforwardly, [Compass-ft’s STYETH index](https://www.compassft.com/indice/styeth/) and the new [Compound Ether Staking Rate](https://coinfund.io/cesr/) (“CESR,” pronounced like the former Roman dictator), created by CoinFund and published by CoinDesk Indices, measure historical ETH validator yield. When it comes to tradeable products, blockspace futures from [Alkimiya](https://alkimiya.io/documentation/) are a related product where the price of a future (currently called a Silica) should vary with ETH validator yield.

More basically, liquid staking tokens (“LSTs”) such as Lido’s [stETH](https://help.lido.fi/en/articles/5230610-what-is-steth) or Rocket Pool’s [rETH](https://docs.rocketpool.net/guides/staking/overview.html) are a corporate liability for one ether staked in a validator where staking rewards (less fees and operating costs) are returned to the token holder automatically. Yield-bearing products such as stETH and rETH can be further broken down with protocols such as [Pendle Finance](https://www.pendle.finance/), whose technology offers pure markets for fairly pricing the yield of any asset (i.e., in the case of LSTs, speculating on the return/rebase component). Establishing fundamental measurements of ETH validator yield as well as, to the fullest extent possible, methods for predicting future ETH yields, may be a useful resource for capitalizing on market inefficiencies or preserving capital when using any of these projects.

This blog post is part one of an ongoing exploration of various metrics related to Ethereum staking yields. I want to more effectively document the behavior of components of ETH validator yields to 1\) learn for myself, 2\) increase public awareness of market dynamics, and 3\) spur ideation for the financialization of ETH validator yields.

### Priority fee dynamics

Base fees get a lot of attention because they [adjust programmatically](https://ethereum.org/en/developers/docs/gas/#how-are-gas-fees-calculated) based on demand for blockspace. Following EIP-1559, they are the primary method by which the Ethereum protocol allocates blockspace. Additionally, because base fees are burned, they are apparently very interesting to ETH community members, who [care a lot about ETH token price](https://ultrasound.money/). However, _because_ base fees are burned, they are irrelevant to validator yields, except to the extent they affect priority fees or other sources of validator revenue.

Base fees make up the majority of fees paid by purchasers of Ethereum blockspace.

{{< figure
  src="/2023/validator_imageONE.webp"
  alt=""
  class="img-caption"
  caption="Total Ethereum fees broken into base fees vs. priority fees. Past three days as of 8-29-23, 5-min moving average. [Link to query](https://dune.com/queries/2981665/4944913)." >}}

I wanted to further investigate the behavior of priority fees, ideally in conjunction with an examination of behavior of other components of ETH validator yield. As such, I chose to examine the 7-day period when the $PEPE meme coin significantly appreciated in price and caused a large spike in gas fees. Based on personal recollection, I know that ETH transaction fees spiked during this period, and there was a lot of MEV activity on-chain, [in particular from MEV bot jaredfromsubway.eth](https://www.coindesk.com/tech/2023/04/19/ethereum-fees-spike-as-bots-spend-millions-to-frontrun-punters-of-pepe-chad/). Looking at the CESR rate, ETH validator yields also spiked during this period, validating that this will be a very interesting period to examine further.

{{< figure
  src="/2023/validator_imageTWO.webp"
  alt=""
  class="img-caption"
  caption="CESR elevated during PEPE price appreciation." >}}


At the beginning of the highlighted period, $PEPE was still a niche, long-tail meme coin with a market cap under $100m. During the highlighted period, the coin’s market cap grew rapidly to a peak of approximately $500m. It peaked at $1.5b the next week before cooling off. CoinDesk [covered](https://www.coindesk.com/markets/2023/04/18/pepe-the-frog-memecoins-rocket-as-crypto-twitter-moves-over-doge-obsession/) the phenomenon in mid-April.

{{< figure
  src="/2023/validator_imageTHREE.webp"
  alt=""
  class="img-caption"
  caption="First period of mainstream interest and significant price appreciation. You can see a concomitant increase in volume at the bottom. [Chart from Coinmarketcap.](https://coinmarketcap.com/currencies/pepe/)" >}}


### _Observation of general gas fee dynamics._

I extracted block data for the period, ranging from 4/27/23 00:00 UTC to 5/3/23 23:59 UTC. Originally, I thought there would be signal in pulling the gas limit, so I joined the `gas.fees` data, which has fee data, with `ethereum.blocks`, which has gas limit data. Interestingly, pulling all blocks from the time period only produced 49,734 blocks when there should theoretically be 50,400 blocks (12s blocks). I should probably investigate that 🙁.

{{< figure
  src="/2023/validator_imageFOUR.webp"
  alt=""
  class="img-caption"
  caption="I thought there would be signal in `gas_limit`, e.g., examining only blocks where gas limit is 300,000, but it turned out that all blocks had a gas limit of 300,000. I think I’m misunderstanding what the column is defining, although Dune documentation can be sparse. [Link to query.](https://dune.com/queries/2957517) " >}}

I then loaded the data into my Python IDE and used Pandas and Matplotlib to chart gas fees over the period. I noticed that gas fees seemed to spike regularly in what appeared to be 24h cycles, so I added highlighting for U.S. ET business hours and the period coincided with spikes!

{{< figure
  src="/2023/validator_imageFIVE.webp"
  alt=""
  class="img-caption"
  caption="30 minute moving average of total gas fees during the first PEPE wave. You can see how gas fees started low/typical then slowly increased as price and on-chain activity increased in the second half of the week. I think this chart could be improved by adding $PEPE price because they are correlated." >}}

{{< figure
  src="/2023/validator_imageSIX.webp"
  alt=""
  class="img-caption"
  caption="Gas fees broken out by priority vs. base." >}}

The data in this relatively basic analysis accorded with my anecdotal recollection of the period. $PEPE seemed to be a North American-driven phenomenon, and on-chain degen traders tend to stay up late and wake up late. One possible explanation of the data is that Americans (broadly, i.e., South and North Americans generally) began the trend then started staying up later; or, Asians picked it up. Dataalways.eth, who I greatly respect, [suggested](https://twitter.com/mud2monarch/status/1694730100556623878?s=20) that the trend observed in this period might be normal cyclicality of blockspace demand, augmented by an increased base load (i.e., from $PEPE trading). My intuition is that there isn’t enough price-inelastic, cyclical demand for Ethereum blockspace for this to explain the whole observed trend. They suggested a way to further explore (examine gas fees linked specifically to the $PEPE uniswap pools), so I probably can’t come to a full conclusion until undertaking that more precise examination.

### _Cross-correlation analysis of base fees vs. priority fees._

I moved on in my analysis. One hypothesis I have is that increases in priority fees will slightly lag increases in base fees. I think this will be the case because changes in base fees are [set by the protocol](https://twitter.com/mud2monarch/status/1694730100556623878?s=20) in response to past block use (relative to target block size) whereas priority fees are set by the user.

To test this hypothesis, I decided to run a cross-correlation analysis of base fees vs. priority fees. A correlation analysis tests the extent to which changes in one dataset align with another. The test offsets datasets repeatedly then calculates a correlation at each offset to test how correlations in the data might change based on the positioning of the data. A peak in correlation might indicate that one dataset leads or lags the other. In this analysis, for example, if I find a higher correlation when the priority fee dataset is shifted to a few blocks (rows) later than the base fee dataset, that may be evidence in support of my hypothesis.

The canonical way to run a cross correlation analysis in Python is to use `NumPy.correlate`. I tried this, but performance was atrocious (at least for my poverty, free-compute setup). With the “full” parameter, `correlate` runs a correlation for every single offset possible (with the “full” parameter), i.e., 100,000 correlations of a 50,000-point dataset. When using the “same” or “valid” parameter, it will run 50,000 correlations, measuring just one side of the lead/lag. There is no way to limit the correlations to surround 0-offset, which is where I suspect the most interesting data will be for me. That is, I expect any relationship to appear within, at most, a few hours of blocks. It wouldn’t make sense to find a correlation between block data that are offset by three days.

In research, this roadblock seems to be a longstanding complaint about `NumPy.correlate`. In 2015, someone [raised this](https://github.com/numpy/numpy/issues/5954) as an issue in the official NumPy documentation. Apparently, MATLAB has a way to limit cross correlations in the way I seek, and the developer sought to implement the same in NumPy. They proposed code, and the GitHub record claims it was addressed, but that doesn’t appear to be the case (because I can't find how to do it in `correlate`). There are some alternative methods proposed online, but many of them aren't full solutions, especially with a 50,000 point dataset.

Instead, I decided to just recreate the cross correlation analysis using a for loop and the shift function. While it’s probably not very efficient, it was surprisingly quick to run, which was great.

{{< figure
  src="/2023/validator_imageSEVEN.webp"
  alt=""
  class="img-caption"
  caption="Python code for a cross correlation analysis of a medium-size dataset when you want to focus the analysis around a zero offset." >}}

{{< figure
  src="/2023/validator_imageEIGHT.webp"
  alt=""
  class="img-caption"
  caption="Results from the cross correlation analysis. I ran the analysis for both base data and data with a 5 minute moving average." >}}

I ran the analysis with unmodified block data and with 5 minute moving average data. I think the 5 minute moving average is helpful because it smooths out data and may be helpful in more clearly identifying trends. For base data, correlations peak at a zero offset. On a 5 minute/25 block moving average, correlations peak at a 1m24s/7 block lag. This is shorter than what I would have expected but still seems meaningful.

The 5 minute moving average peak provides support for my initial hypothesis. The lag is shorter than what I would have expected, and obviously the base data has no offset. It could be the case that wallet software automatically adds a priority fee when it observes blockspace to be in high demand (either based on the mempool or on fees for previous blocks). To the extent that most people are setting priority fees programmatically, i.e., letting their wallet do it, it would make sense that priority fees and base fees don’t lag very much.

I think studying moving average correlation is useful because it captures aggregate behavior. While some users may be adjusting priority fees right away by letting their wallet set fees, other users may be resubmitting transactions or setting transactions manually.

The fact that there are elevated correlations in the blocks after the peak is additional evidence for the intuition that people may set priority fees manually, and differently. For example, imagine submitting a block and not having it included. Some people may be willing to continue paying the average fee and wait longer for inclusion, but some people may try to resubmit transactions with an elevated priority fee.

_Conclusion_.

I imagine there are weaknesses in my analysis, and I welcome them in the comments. First, I think I need to go deeper on the statistics to assess the significance of my findings. Second, it could also be interesting to more precisely quantify the predicted level of priority fees relative to observed or predicted base fees. It seems to me that there is an interesting mismatch between the timing of when base fees are set/known and priority fees are paid. That is, the base fee level is set at the beginning of the block whereas the level of priority fees is an empirical figure observed after the block is validated (or proposed? or built?). I imagine there is research on this somewhere (or it could only be proprietary to certain actors in the ecosystem, like searchers or large validators).

For me, I’m using this exploration as an opportunity to sharpen my SQL and Python skills, my capacity for on-chain analysis, and my understanding of Ethereum. More to come!

{{< figure
  src="/2023/validator_imageNINE.webp"
  alt=""
  class="img-caption"
  caption="_Bonus._ Flux trees related to this project. Flux is a generative AI power tool created by engineers at Paradigm that is super helpful for using generative AI in the most effective way possible. More information [here](https://zachrwong.info/tips-for-using-flux/)." >}}