+++
title = "Comparing and contrasting PayPal balances with USDC from first principles"
date = 2022-02-03
draft = false
tags = ["crypto", "policy", "explainers", "stablecoins"]
description = "A first-principles comparison of PayPal balances and USDC, examining their similarities, differences, and the regulatory implications for stablecoins in the U.S. financial system."
keywords = ["USDC", "PayPal", "stablecoins", "digital dollars", "money transmission", "crypto regulation", "consumer protection", "CFPB", "Circle", "payment networks", "financial regulation", "asset-backed stablecoins", "permissionless payments"]
featured = "/2022/comparison_imageONE.png"
+++

>For if the people are not equal, they will not have equal things. Rather, from this arises fights and accusations, either when people who are equal have or are distributed unequal things, or when people who are unequal have or are distributed equal things…
>
>*The Nicomachean Ethics*, 1131a, trans. Bartlett and Collins

Since stablecoins have started to receive scrutiny by US federal regulators, it’s been increasingly popular to compare them to other types of nonbank digital dollars such as PayPal, Cash App, or Venmo balances. This comparison makes intuitive sense because (centralized) stablecoins are a dollar-denominated corporate liability that can be used on a proprietary payments network. If the products are very similar, there exists a nice template for regulation, provided a “like for like” standard is applied. In this post, I compare and contrast PayPal balances with USDC and provide preliminary thoughts on regulatory steps.

*These are my independent thoughts and do not necessarily represent the views of my employer.*

### Similarities

*Network Character*
PayPal is a proprietary digital payments network. Consumers buying things and merchants selling things use PayPal to transfer value using Paypal’s internal settlement network. While users can choose to pay with ACH or card, for the purposes of this comparison, we’re primarily interested in situations in which a user makes a transaction using his PayPal balance. A PayPal balance is a liability that PayPal issues to the user, and it is convertible to private bank money at any time. When a user makes a payment, he directs PayPal to transfer dollars from his account to the merchant’s account, a transfer that occurs entirely on PayPal’s internal ledger.

USDC is a stablecoin, which is a tokenized dollar liability that circulates on a public blockchain. Consumers use USDC to transact on public blockchains, whether for trading or other purposes. Users hold USDC in a third-party wallet and then settle USDC transactions on a blockchain such as Ethereum. US consumers that wish to convert their USDC liability to private bank money have a two-step process which involves converting USDC to USD via an exchange (free on Coinbase, at least) then converting the exchange liability to private bank money. USDC issuer Circle does not offer redemption or issuance services to consumers.

Some have pushed back against the idea that a stablecoin such as USDC is just another proprietary payments network such as PayPal, [likening one’s choice of stablecoin to one’s choice of email client](https://apnews.com/article/cryptocurrency-technology-business-blockchain-bitcoin-abbe14fba1dfc5e5cb97bb9bb8f15ca7). Respectfully, I don’t think the analogy holds. Your choice of email client is more analogous to your choice of crypto wallet than it is to your choice of stablecoin. The asset is like the email protocol, and both rely on network effects for value. Wallets and email clients plug into the common network; they are not the network. Email clients can build nice features that allow you to use different email protocols (like using a web service or a desktop client with the same email address), but that would be analogous to a digital wallet allowing you to seamlessly switch between stablecoins (like how FTX treats all stablecoins and US dollar deposits as a single asset). On the backend, though, the clients are switching networks on your behalf.

I likewise think it’s most sensible to think of USDC on different blockchains as separate products. It is possible to transfer USDC across blockchains, but it is a multi-step process, at least for consumers. While the products may be very similar, i.e., because the credit and liquidity risk of Solana USDC vs Ethereum USDC don’t differ significantly, they seem similar to, e.g., PayPal vs Venmo balances. PayPal and Venmo are not natively interoperable, and neither are Solana- and Ethereum-based USDC.

***Revenue Model***

Someone I know is fond of saying about new payments products, “it’s all about the interchange, baby” (this applies to most fintechs, too). Interchange is the fee that the card networks charge merchants for payments using cards. According to [research by the Kansas City Fed](https://www.kansascityfed.org/research/interchange-fees/), merchants in the US pay on average 1.5–2% for the service of accepting card payments. In practice, this figure may be higher because of card processing fees layered on top of interchange costs. Interchange revenue is split between the card networks, card-issuing banks, and other parties involved in the transaction.
{{< figure
  src="/2022/comparison_imageTWO.webp"
  alt=""
  class="img-caption"
  caption="Flow of fees from a $40 retail purchase. [Source.](https://www.federalreserve.gov/econresdata/feds/2014/files/201477pap.pdf)" >}}

Just like the card networks, PayPal’s primary source of revenue is fees on transactions settled via PayPal. While they appear to be pursuing a more diverse revenue base by building out a general purpose financial services experience, 90% of PayPal’s revenue came from transaction fees in [Q3 2021](https://s1.q4cdn.com/633035571/files/doc_financials/2021/q3/PYPL-Q3-21-Investor-Update.pdf). The more people transact on PayPal, the more money PayPal makes.

USDC issuer Circle, by contrast, is not involved in transactions settled with USDC, so they take no transaction fee. Instead, Circle revenue comes primarily from interest earned on reserve custody. Market competition and regulatory scrutiny has pushed Circle into a very conservative investment portfolio, but since it is full reserve, its assets under management is very large. For Circle, the more USDC in circulation, the more money Circle makes. Additional revenue models are available to Circle as well, especially if they can acquire a banking license in the next few years.

***Asset backing***

The reserve allocation (and counterparty credit risk) of stablecoin issuers has received a lot of attention in the past year, perhaps because of Tether’s missteps in the past. In [February 2021](https://www.coindesk.com/markets/2021/02/23/ny-ags-850m-probe-of-bitfinex-tether-ends-in-an-185m-settlement/), as part of its settlement with the New York Attorney General, Tether agreed to provide a breakdown of its reserve composition. [The result](https://www.coindesk.com/markets/2021/05/13/tethers-first-reserve-breakdown-shows-token-49-backed-by-unspecified-commercial-paper/), first published in May 2021 was… disappointing, revealing that just 5.1% of Tether was backed by cash or US treasuries. In response, Circle expanded [its May 2021 reserve attestation](https://www.centre.io/hubfs/pdfs/attestation/Grant-Thorton_circle_usdc_reserves_07162021.pdf?hsLang=en) to include a breakdown of its reserve allocation. No good deed went unpunished. Competitor Paxos came out with a [blog post](https://paxos.com/2021/07/21/a-regulated-stablecoin-means-having-a-regulator/) that blasted Circle for being purportedly “unregulated” and backed by shoddy reserves. Next, [a Bloomberg article](https://www.bloomberg.com/news/articles/2021-08-11/coinbase-drops-promise-of-token-s-cash-backing-that-wasn-t-true?sref=25rnPxpS) in August 2021 pointed out that Coinbase’ claim that USDC was backed 1:1 by dollars “in a bank account” was not true. Soon after, Circle [announced](https://www.circle.com/blog/evolving-usdc-reserves-to-100-cash-and-short-duration-us-treasuries) that the entire USDC reserve would be held in cash and short-term treasuries, which remains the case today. This reserve mix, arrived at due to market competition (and, perhaps, a fear of regulatory scrutiny), is *safer* than what is required by Circle’s state money transmitter licenses.

PayPal also operates under a state money transmission license but has not been subject to the same level of public scrutiny or competitive pressure regarding reserve reinvestment. According to industry participants, nationwide money transmitters conventionally follow the liquidity and credit risk guidelines of the strictest state, apparently Texas, which [requires](https://txdob.ctspublish.com/texas/browse/txdobset/texas/z20001870) that 50% of account holders’ assets be held in “permissible investments” [^1]. The result is that PayPal likely uses a higher yielding, more risky asset allocation than what Circle maintains. PayPal does not disclose its reserve allocation, but it is a public company subject to public reporting and independent audits.
[^1]:If anyone who has helped companies set this up wants to weigh in on reserve management requirements & common market practices, please DM or comment! I am not an expert on this.

***Usage Metrics***

As I pointed out [in November](https://twitter.com/mud2monarch/status/1465460186437586953?s=20&t=BEgtYEgK-Swf4922y0hSYg), USDC recently passed PayPal in two significant, and roughly comparable, usage metrics. In Q3 2021, PayPal’s Total Payment Volume was $310b while USDC users settled $348b of transactions in the same period. Additionally, at the end of Q3 2021, PayPal reported $37.8b in outstanding consumer balances, and USDC had approximately $38b in total supply at the same time. [^2]
[^2]:Data from Coin Metrics/The Block and PayPal earnings. PayPal TPV is a headline figure reported in a number of places. For PayPal customer balances, I’m using the “funds payable and amounts due to customers” liability on pg. 8 of [its earnings release](https://s1.q4cdn.com/633035571/files/doc_financials/2021/q3/Q3-21-PayPal-Earnings-Release.pdf).

Of course, the use of PayPal vs. USDC may be different. Consumers regularly use PayPal for everyday purchases, and PayPal reported an Average Purchase Value of $63 at the end of Q3 2021. Meanwhile, the average transfer value for USDC was $96,665 (the median transfer value was $2,079). [^3] And PayPal certainly has a bigger network: as of Q3 2021, PayPal reported 416mm accounts worldwide whereas ~0.5mm addresses had USDC balances in excess of $10. [^4]
[^3]:Data from Glassnode, retrieved 1/30/22: [https://i.imgur.com/IN1N9qk.png](https://i.imgur.com/IN1N9qk.png). 90 day simple moving average.
[^4]:Data from Coin Metrics, ["State of the Network: Issue 122"](https://coinmetrics.substack.com/p/coin-metrics-state-of-the-network-a0e). I’m not sure what the best, comparable figure for “accounts” would be for USDC, so I just use what Coin Metrics reports in their free weekly update. If anyone has any thoughts on what would be better, please leave a comment or send me a DM on Twitter.

{{< figure
  src="/2022/comparison_imageTHREE.webp"
  alt=""
  class="img-caption"
  caption="Stablecoins have very high average transfer sizes, in line with their primary reported use as trading & institutional tools. Very different than PayPal, which has an average transaction value of $63. [Source](https://coinmetrics.substack.com/p/state-of-the-network-issue-140)." >}}

### Differences

The comparison of USDC with PayPal balances is apt because both are assets that establish proprietary payments networks. However, the networks do differ in two important ways which, in my opinion, reveal the new paradigm created by public blockchains. First, use of USDC is permissionless whereas all users wishing to use PayPal must register. Second, the services required for consumers to use USDC are disaggregated whereas in PayPal they are consolidated.

Public blockchains are so named because they are publicly readable and writable by anyone, with no prior qualification. USDC, therefore, can be used by anyone in a permissionless way, whether as a consumer or merchant or developer. This contrasts with PayPal, which requires account registration prior to any use of its platform. Additionally, some PayPal privileges, such as the ability to authorize transactions on behalf of another party, are restricted to paid customers. Finally, PayPal implements US KYC and AML regulations which require network participants to provide sensitive identifying information, subject funds to [withholding](https://mud2monarch.medium.com/comparing-and-contrasting-paypal-balances-with-usdc-d39ff1cff4f7#:~:text=The%20comparison%20of,increase%20UX%20friction.) or audit, and increase UX friction.

The second important difference is that the service stack to facilitate USDC use is disaggregated whereas for PayPal it is wholly contained. Circle issues USDC, but wallet services and transaction validation are provided by third parties. In contrast, PayPal serves as the issuer, wallet, network, and custodian for all PayPal funds. Wallet services is a good example of the different ecosystems: Circle CEO Jeremy Allaire [reported recently](https://twitter.com/jerallaire/status/1488314662261125120?s=20&t=7nfoIWA2BdtzCFz2UwlRnQ) that 223 digital wallets on iOS and Android support USDC. For PayPal, there is just one digital wallet, and it is the PayPal app.

{{< figure
  src="/2022/comparison_imageFOUR.webp"
  alt=""
  class="img-caption"
  caption="Public blockchains natively encourage service disaggregation, promoting consumer choice and innovation." >}}

The cumulative effect of permissionless access and disaggregated services is that innovation built on top of USDC thrives. New PayPal features must be created by PayPal, and developers must work within the confines of PayPal’s API. Consumers, businesses, and developers working with USDC, on the other hand, are free to use USDC in any way that they can imagine and make work technically. The burden to experiment is lower because potential network participants don’t have to go through a lengthy onboarding and vetting process. And public blockchains’ internet native, cross-border nature allows wide discussion & collaboration with “strangers” that people have only met on Twitter, Telegram, or Discord. Finally, because USDC implementation is open source, anyone can fork the contract and improve the service if they believe there is a substantive improvement to be achieved and significant market demand to meet.

{{< figure
  src="/2022/comparison_imageONE.png"
  alt=""
  class="img-caption"
  caption="A young Aristotle, arm outstretched, explains to his mentor Plato that it would be unjust to require stablecoins to be issued by banks when PayPal has a similar character and risk profile and operates uncontroversially under a money transmission regime; Boomer Plato, left, growls that crypto is a ponzi reminiscent of the Dutch Tulip bubble." >}}

### Regulatory Implications
If two products are the same, they should be regulated the same. And if they are different, they should be regulated differently. This is not just equal treatment under the law but also an intuitive conception of what is right, as Aristotle explained in the *Ethics*. Based on the similarities and differences between PayPal balances and USDC, then, there seem to me to be some clear regulatory implications.

First, USDC issuance should not be confined to depository institutions. PayPal is not a depository institution, yet it has the same quantity of customer liabilities as Circle does (or it did; USDC supply has grown an additional $12b since the end of Q3 2021). In fact, because USDC issuance is limited to businesses — which generally require fewer protections than consumers — PayPal balances could be considered more risky than USDC.

Second, the federal consumer protection regulations that PayPal follows should be followed by financial institutions working with USDC. For example, [CFPB regulations require](https://www.consumerfinance.gov/rules-policy/regulations/1005/6/#b) PayPal to refund consumers when they are hacked or defrauded. Likewise, custodial digital wallets facilitating USDC transactions should probably follow these regulations as well. As I explained above, because the USDC service stack is disaggregated, Circle only issues USDC, and this particular regulation likely does not apply to them.

I don’t think there are any regulatory implications for reserve requirements. Both Circle and PayPal follow state money transmission guidelines, which require at least 50% of customer liabilities to be held in very safe, very liquid assets. It doesn’t seem particularly compelling to require a full asset reserve, either. Separately, though, if there is *market competition* that demands a full reserve of low-risk assets, that seems perfectly reasonable to me.

The last point I’ll make is that the primary federal regulator of PayPal is the CFPB, not the SEC or the CFTC or one of the banking agencies. The CFPB implements consumer financial protection regulations; for example, the regulations that require refunds for defrauded or scammed consumers. So far, the CFPB has not made any moves in crypto, but it looks like [that](https://www.consumerfinance.gov/about-us/newsroom/statement-cfpb-director-chopra-stablecoin-report/) [may](https://www.americanbanker.com/news/complaints-about-crypto-are-soaring-is-a-cfpb-crackdown-imminent) [change](https://www.bloomberg.com/news/articles/2022-01-26/progressive-crypto-skeptic-set-to-join-consumer-finance-watchdog) under its ambitious new Director.

Want to know more about what the CFPB could do in crypto? Subscribe, I’m writing about that next.

*These are my independent thoughts and do not necessarily represent the views of my employer.*