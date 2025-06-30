+++
title = "Four Takeaways from the Fourth NY Fed Conference on Fintech"
date = 2023-10-01
draft = false
description = "A short writeup of the Fourth NY Fed Conference on Fintech, which took place in September 2023."
tags = ['crypto', 'policy']
keywords = ['NY Fed', 'crypto policy', 'benefits of automated market makers']
+++
On September 29th, [the Federal Reserve Bank of New York hosted a conference on fintech](https://www.newyorkfed.org/research/conference/2023/Fintech) with a special focus on the use of artificial intelligence and digital assets in financial services. I attended in-person and thought the agenda was excellent in both areas. In particular, I thought the morning presentations on crypto market structure were some of the best research and discussion I had seen in a long time. In this post, I record four takeaways from the conference:

1. Cryptoasset scholarship is mature, serious, and fascinating.
2. Innovation from public blockchains will lead the evolution of traditional finance.
3. At this point, crypto policy advocates need to go deep on details.
4. When it comes to artificial intelligence, "the girls that get it, get it. The girls that don’t, don’t."

*These are my independent thoughts and do not necessarily represent the views of my employer.*   

### Takeaway #1: Cryptoasset scholarship is mature, serious, and fascinating.

The highlight of the conference for me was the 10:30 - noon session on crypto. The format was a paper author would present his paper then another academic would offer comments. When the speakers didn’t run over time, audience questions were solicited.

When I first got into crypto, I was surprised at the depth of multi-disciplinary intellectual investigation I encountered. While not always at the forefront of the industry’s attention, I’m consistently impressed by not just the _quantity_ of interesting economic, social, political, regulatory, and philosophical questions prompted by this strange technology but also the _quality_ of people thinking about them. I felt that again last Friday.

*Paper 1: Using AMMs for equities*

The most policy-relevant paper will be Katya Malinova and Andreas Park’s [“Learning from DeFi: Would Automated Market Makers Improve Equity Trading?”](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4531670) The answer is yes: Malinova and Park show that implementing AMMs in U.S. equities markets would **save liquidity demanders $8.8bn per year in transaction costs**. Liquidity demanders are those who buy or sell without discretion at market price; likely or often retail investors. The benefits are greater for low- and mid-cap equities where liquidity is thinner and attention is scarcer. Said differently, the benefit of an automated market maker is greater in market segments where there are fewer un-automated market makers (firms/humans).

This is a paper with immediate application. As the discussant, Fahad Saleh of Wake Forest, pointed out, the paper demonstrates that crypto innovations have relevancy for traditional markets, even if removed from public blockchains or cryptoassets. AMMs are a genuinely new market mechanism that can reduce costs for U.S. investors and businesses by approximately 30% per year, among other benefits (another benefit is that investors in a company could earn a return on their passive holdings of equity). This ought to be compelling even for people who want nothing to do with crypto. The barriers to implementing such a technology are not technical; they are legal and political. By quantifying the potential benefit that could be achieved using historical U.S. equities data, Malinova and Park help us understand whether the potential benefit might be worth the cost of engaging those legal and political barriers. It seems like it would be.

The full paper is technical, but I would encourage interested parties to read it, [perhaps with the assistance of generative AI](https://zachrwong.info/learn-anything-in-the-world-gen-ai/), or watch the recording of Park’s presentation when it’s made available on the conference website. The authors demonstrate that an optimal fee can be derived from market characteristics (liquidity providers must be compensated for liquidity provision at a level sufficient to overcome implicit loss to informed parties) then model an AMM structure against historical data for every U.S. equity to obtain their results.

_Paper 2: Economist's critique of U.S. crypto regulation_

The next most policy-relevant paper is Joshua Gans' paper ["Cryptic Regulation of Crypto-Tokens."](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4473488) It is essentially an economist’s critique of the current state of U.S. crypto regulation. Stepping back from specific debates, he contends that regulators’ proper role in a capitalist system is to 1\) identify potential market failures, next 2\) isolate regulatory tools that could address such market failures, and finally 3) assess potential welfare improvements that could be brought about by regulation. I find this convincing. Gans works through each step in this regulatory process, suggesting market failures, regulatory tools, and potential welfare improvements that are relevant to the crypto industry.

Today, U.S. regulators appear to have focused on other questions than the ones above, such as what risks could emerge if public blockchain technology proliferates. At least theoretically, this is not the role of a regulator: in an efficient market (i.e., one that has no market failures), risks should be properly priced by market participants according to their preferences. I wonder if regulator incentives are misaligned: it may be the case that regulators’ primary motivation is a political one: they are mostly concerned with not being blamed for something bad that happens. This is understandable, and I imagine the incentives have been reinforced by the political fallout of the March bank failures. Their main incentive may be to avoid such public critiques.

Regardless, Gans’ paper is approachable (non-quantitative) and written in a colloquial style that is entertaining. I thought it was a refreshing exposition of an economist’s perspective on crypto regulation — a field that is so often led by lawyers (and therefore, generally oriented towards the identification of risk).

_Paper 3: Frontrunning and MEV dynamics on Ethereum_

The last paper presented was fascinating, but it’s unlikely to be as policy-relevant as the former two. Agostino Capponi, Jia, and Wang’s “[Allocative Inefficiencies in Public Distributed Ledgers](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3997796)” paper models efficient behavior of Ethereum validators, transaction submitters, and transaction frontrunners to determine whether private mempools (like Flashbots) will be adopted. The allocative inefficiency is that the presence of frontrunning in blocks is inefficient because such transactions are overpriced transfer payments.

The key tradeoff driving the analysis is that transaction submitters (i.e., DEX users) want to use private mempools that are not susceptible to frontrunning, but when doing so they take on execution risk if private mempools are not widely adopted (i.e., they submit a transaction to a private mempool but there is no validator in the mempool — or not enough validators — to actually execute their transaction in a timely manner). If all validators adopt private mempools then users will benefit; however, in such a situation, validators are _disincentivized_ to adopt private mempools because they then lose out on MEV revenue that could be obtained in public mempools. To overcome this unstable equilibrium, the authors propose out-of-protocol payments to validators that compensate for lost MEV revenue, which would achieve allocative efficiency. It is a really fascinating paper for me as I am interested in MEV and [validator economics](https://zachrwong.info/exploration-gas-fees-and-validator-payments-on-ethereum-pt-1/), but it’s likely too complex and niche to have immediate policy implications.

I hope readers gather that the papers presented are serious academic examinations of blockchain economics that have policy relevance. It’s gratifying to see significant attention paid to the complex problems that exist in the ecosystem, and hats off to the conference organizers for recognizing this vibrancy.

### **Takeaway #2: Innovation from public blockchains will lead the evolution of traditional finance.**

My fundamental thesis for the importance of public blockchains is that in a permissionless financial system, innovation occurs 10x — 1000x faster than in the uncompetitive, bank-dominated, lethargic traditional financial system that exists in the United States. History has shown that providing humans with the ability to access free and open systems unlocks incredible ingenuity, creativity, and entrepreneurship that benefits the whole world.

For example, the creation of the printing press enabled the Protestant Reformation, the Enlightenment, and the Scientific Revolution. The internet has led to the creation of Wikipedia, Google, Uber, Amazon, YouTube, smartphones, and this website (in rough order from least to most valuable to society). Some of that innovation has been negative — the printing press probably helped hate speech proliferate more quickly — but it seems obvious that the benefits of both technologies significantly outweigh the negatives. Public blockchain technology is the equivalent of these past movements, for value.

However, it’s unlikely that the entire financial system will adopt the DeFi ecosystem as it exists today. Instead, I think that the traditional financial system will only change when there is an innovation _good enough_ to force changes. Traditional fintechs have created new and better ways to provide financial services before, but they haven’t been widely adopted because of the market structure issue. New technologies will need to have _so much_ consumer demand or reduce risk _so greatly_ or offer _large enough_ cost savings to overcome the barriers to innovation. That’s how the financial services industry will change.

Presentations during Friday’s conference repeatedly vindicated that for me. In addition to the Malinova and Park paper, Cecilia Skingsley of the BIS Innovation Hub was the BIS’ Project Mariana, which uses a three-asset automated market maker to facilitate foreign exchange between SGD, EUR, and CHF. Because automated market making is a step improvement over traditional market making (e.g., [because it is available at all times](https://uniswap.org/OnchainFX.pdf), pg. 11), the benefit is sufficient to incentivize slow-moving institutions to experiment (today) and adopt (soon) these technologies. But don’t get lost in the evolution: these innovations can only be applied to traditional markets because they emerged on public blockchains in the first place. AMMs were not - and would not have been - created in a bank.

In their book _How Google Works_, Eric Schmidt and Jonathan Rosenberg assert that the most successful startups are built around a unique technical insight. For Google that was the search algorithm created by Page and Brin. For crypto right now, a clear technical insight is the creation of automated market making. We may not know what will emerge next (if you do, you should start a company and become a billionaire!), but based on the structure of public blockchains, we can be confident that new technical insights and innovations will come about.

### **Takeaway #3: At this point, crypto policy advocates need to go deep on details.**

One of the afternoon sessions was about the state of crypto regulation. Presumably wary of repeating a panel that has been run many times over the past two years, moderator [Austin Campbell](https://twitter.com/CampbellJAustin/) seemed intent on pushing panelists for _specifics_ about why blockchain-based financial services are different, or what _specific_ regulations are purportedly incompatible with the public blockchains. Audience questions were in the same vein.

While it may have been reasonable to keep debate broad when many policymakers were getting up to speed on the contours of public blockchains, most baseline concepts are pretty well-understood today. Now, I think crypto policy advocates need to be able to provide specific examples to maximally convince audiences. On Friday, two examples stood out.

_“What’s an example of a specific regulation that is fundamentally incompatible with the technology of cryptoassets?”_

The crypto industry claims that cryptoassets are _so new_ that new regulations are needed. I agree. However, at times, industry folks decline to identify specific regulations that are incompatible which I think is a mistake. Every crypto policy advocate should be able to answer this question. [Vy Le](https://twitter.com/TuongvyLe12) of Bain Cap Crypto brought up the issue of custody, which is also my go-to. If you’re in the industry, feel free to use this:

1. [SEC Rule 15c3-3](https://www.govinfo.gov/content/pkg/CFR-2010-title17-vol3/pdf/CFR-2010-title17-vol3-sec240-15c3-3.pdf) requires that broker-dealers “promptly obtain and shall thereafter maintain the physical possession or control of all fully-paid securities and excess margin securities carried by a broker or dealer for the account of customers.”

3. To the extent that a crypto firm wants to facilitate activities with crypto-asset securities and therefore seeks to register as a broker-dealer, it must comply with this rule.

5. However, how can one maintain physical possession or control of a crypto-asset? That’s a fundamental incompatibility.

7. Even under a relaxed standard, such as interpreting “physical” to mean “exclusive,” additional clarity is required for custodians to understand how they can satisfy the requirement and provide secure custody services for investors.

_“What’s one way that the integration of blockchains into financial services could improve outcomes for consumers or the financial system?”_

[Gordon Liao](https://twitter.com/gordonliao/) of Circle has a great answer to this question. Rehashing [an argument he’s made before](https://www.circle.com/blog/tradfi-cefi-defi-a-balance-sheet-journey-through-financial-alchemy), he pointed out the issue that balance sheet constraints have played in contributing to market instability in traditional finance, such as the funding market turmoil of September 2019. By disaggregating financial functions using DeFi, financial regulators could reduce the reliance on bloated intermediaries with necessary liquidity constraints. For example, [the proliferation of blockchain payments](https://www.barrons.com/articles/svb-circle-payments-stablecoins-crypto-8ffba659) could reduce U.S. payments system reliance on bank intermediaries, which must hold Federal Reserve Bank balances solely to facilitate payments. Bank reserves could be redeployed into better avenues, and non-financial companies could reduce their reliance on a few mega-banks. This is a great, specific thesis for why blockchains would improve the financial system, and is much more convincing than simply saying, “we can disintermediate finance!”

### **Takeaway #4: When it comes to artificial intelligence, "the girls that get it, get it. The girls that don’t, don’t.**"

Earlier this year, there was a Tik Tok trend centered around the audio “The girls that get it, get it. The girls that don’t, don’t” ([semi-NSFW link with examples](https://www.youtube.com/watch?v=VUx3RH2bHls)). The audio was used as the background for very niche, hard-to-explain commentaries or observations in the various Tik Tok genres: beauty, fashion, dating, etc. I think the audio applies to AI today: I increasingly believe that there is a dichotomy in society between people who grok the power of artificial intelligence and those who don’t. That was my takeaway from the first panel where the participants often seemed to be talking at different levels, with some panelists having a sophisticated understanding of the technology and others taking a more limited and less nuanced approach.

As with almost anything, the best way to “get it” is to actually use something. The viral audio was powerful because, like so much on Tik Tok, it was used to describe phenomena that are incredibly hard to articulate. If I tell you, “artificial intelligence will fundamentally change knowledge worker productivity in the next ten years,” it’s hard for you to understand exactly what I mean if you haven’t had an experience where ChatGPT has accelerated your productivity on an important task by an order of magnitude or more. Talking with someone who has had that experience is wildly different than the merely theoretical conversations you have with people who have only scratched the surface of AI.

I would strongly encourage any reader to set aside just a couple of hours to deeply experiment with ChatGPT. Think of it this way: given claims from credible people about how useful this technology is, isn’t it worth spending $20 and four hours to evaluate those claims for yourself? [Start here](https://zachrwong.info/learn-anything-in-the-world-gen-ai/), and think of ChatGPT as a way to _augment_ your existing skills, not replace them.

### **Conclusion**

Hats off to the conference organizers, Messrs. Pablo Azar and Asani Sarkar, for a fantastic, serious day of discussion about two vitally important topics. Thank you to the Program Committee, the Bank, and the participants for the wonderful venue, intellectual stimulation, and invitation to attend. I left energized about the state of the crypto industry and encouraged by the seriousness and novelty of the ideas presented. I’m excited about continuing to participate in one of the most interesting, multidisciplinary movements I’ve ever come across and thankful that the Federal Reserve System is taking seriously the questions raised by crypto.

_These are my independent thoughts and do not necessarily represent the views of my employer._