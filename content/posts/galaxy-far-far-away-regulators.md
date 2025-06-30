+++
title = "A Galaxy Far, Far Away: The Cryptonative’s Guide to US Financial Regulators"
date = 2022-03-09
draft = false
description = "An overview of the U.S. financial regulatory structure for cryptonatives."
tags = ["crypto", "policy", "explainers", "stablecoins"]
keywords = ["US financial regulators", "crypto regulation", "SEC", "CFTC", "Federal Reserve", "OCC", "FDIC", "NCUA", "CFPB", "FTC", "FinCEN", "IRS", "cryptocurrency policy", "financial regulation", "crypto compliance", "stablecoins regulation", "banking supervision"]
+++
{{< figure
  src="/2022/galaxy_imageONE.webp"
  alt=""
  class="img-caption"
  caption="**A New Hope**: Satoshi Nakamoto, center, surveys the financial services landscape in 2008. He sees central banks debasing the currency, banks lending money in waves of credit bubbles, and massive overhead costs that make micropayments impossible. He creates Bitcoin, a 3720-to-1 longshot to start a neutral, distributed monetary system with no single point of failure." >}}

If asked to describe who regulates cryptocurrency at the federal level, I suspect most cryptonatives would only be able to name the SEC and the CFTC, and maybe the Fed. In some ways, that’s no surprise because builders are focused on building, and crypto sometimes feels like a whole different world. But the reality is that the US financial regulatory system is much more extensive, and all of the agencies are important. As cryptocurrency mainstreams, each agency is thinking about how to accommodate (or not) the crypto-ecosystem within their existing frameworks. This post guides the cryptonative through the Galaxy of the US financial regulatory structure and explains how each regulator might interact with crypto. [^1]
[^1]: This post discusses US federal agencies only. To the audience: be aware that financial regulation happens at the state level, too. [See here](https://www.realclearmarkets.com/articles/2021/11/03/a_federal_power_grab_over_the_future_of_stablecoins_801886.html).
Additionally, this post only discusses financial regulators. Other agencies may in the future regulate the non-financial applications of blockchain and cryptocurrency, although such applications still seem far away to me (if they ever emerge). But see [here](https://twitter.com/BillRockwood2/status/1484004973792923651) and [also note](https://twitter.com/mud2monarch/status/1501383154988306433?s=20&t=Y3zh-S1OEV7d711a_i0cfw) that the recent Biden Executive Order directs non-financial agencies to examine cryptocurrency and blockchain.

*These are my independent thoughts and do not necessarily represent the views of my employer.*

---

### Macro Structure
{{< figure
  src="/2022/galaxy_imageTWO.webp"
  alt=""
  class="img-caption"
  caption="The federal financial regulators and their responsibilities. [Source.](https://crsreports.congress.gov/product/pdf/R/R44918)" >}}

Show this chart to anyone working on financial policy in DC, and I bet they’ll be able to tell you exactly from what report it comes. The US financial regulatory structure is convoluted, complex, and delicate, and many have waded through the above to figure out [Who Regulates Whom](https://crsreports.congress.gov/product/pdf/R/R44918). For our purposes, though, I think you can intuitively separate agencies into three categories: prudential regulators, regular person-protectors, and Treasury bureaus.

**Prudential regulators** look out for the safety and soundness of the financial system, i.e., whether it’s going to collapse or not. Generally, this involves supervision of banks: monitoring banks’ capitalization ratios, performing stress tests, double-checking security practices, and conducting other exams.

**Regular person-protectors** look out for regular people (as opposed to businesses or professionals) *in their capacity* as something. For example, the SEC protects regular people in their capacity as investors. The CFPB protects regular people in their capacity as financial product consumers. And so on.

Finally, there are various **Treasury bureaus** that implement other rules and regulations such as anti-money laundering regulations (FinCEN) and tax requirements (the IRS).

There are so many regulators that I think it’s more important to understand the macro structure of financial regulation than the specific authorities and charters of each agency.

Let’s dive in.
{{< figure
  src="/2022/galaxy_imageTHREE.webp"
  alt=""
  class="img-caption"
  caption="Crypto is an improbable Rebellion against legacy financial services. The fatal weakness, the exhaust port in their Death Star? The truth that the legacy system has failed people: failed to provide equal access; failed to protect civil liberties; failed to innovate to meet the modern world; and more. Crypto is taking its shot." >}}

### Prudential Regulators

Prudential regulators are tasked with preserving the safety of the banking and financial system. This generally means making sure that financial institutions are well-capitalized, appropriately-risked, and operating well. Prudential regulators have examiners that go to banks to watch what they’re doing, review financials, and talk to executives.

*The Federal Reserve Board (FRB)*

The Federal Reserve is best known for setting monetary policy, but a branch of the Federal Reserve System also serves as an important prudential regulator. The Fed has supervisory jurisdiction over bank holding companies and state-chartered banks that are part of the Federal Reserve System. The Fed also operates key payments systems like Fed Wire/Fed Now and benefits from the expertise of the regional Fed banks. While the structure is convoluted, [^2] Fed policy staff are knowledgeable, their resources and authorities are vast, and their leaders are very influential.
[^2]:The Federal Reserve *Board* is part of the Federal Reserve *System*, which also includes the Federal Reserve *Banks* and the Federal *Open Market Committee*. The Federal Reserve Board is the prudential regulator. The Federal Open Market Committee sets the federal funds rate, a component of monetary policy.

**A crypto question that could be answered by the Fed: should Wyoming Special Purpose Depository Institutions such as Kraken Bank and Custodia (née Avanti) be allowed access to a Fed Master Account?**

*The Office of the Comptroller of the Currency (OCC)*

The OCC supervises nationally chartered banks. In general, these are the largest consumer banks in the US — the OCC oversees almost twice as many assets as the FDIC and the FRB combined.

**A crypto question that could be answered by the OCC: should nationally chartered banks like JP Morgan Chase be allowed to hold crypto assets on their balance sheet, e.g., for trading, or would that threaten the stability of the depository institution?**

*The Federal Deposit Insurance Corporation (FDIC)*

The FDIC supervises state-chartered banks that are not part of the Federal Reserve System and also custodies the FDIC deposit insurance fund. These tend to be smaller banks that focus on a region of the country. It also has nominal backup authority over all banks due to its duty to custody the insurance fund. The FDIC also has resolution authorities in the event of a bank failure.

**A crypto question that could be answered by the FDIC: should federal deposit insurance be extended to stablecoin balances?**

{{< figure
  src="/2022/galaxy_imageFOUR.webp"
  alt=""
  class="img-caption"
  caption="A breakdown of the institutions, assets, and deposits supervised by each prudential bank regulator. Source. This is not a very well-organized graphic, but the takeaway is that OCC-supervised banks tend to be the largest (e.g., JPMC), Fed-supervised Banks are mid-size/regional (e.g., Signature Bank, which focused mostly on NYC/the Northeast), and FDIC-supervised banks are very small (e.g., maybe one branch or a single-state focus)." >}}

*The National Credit Union Association (NCUA)*

The NCUA supervises credit unions. Credit unions are a [special type of depository institution](https://www.mycreditunion.gov/about-credit-unions/credit-union-different-than-a-bank) that generally have a specific population focus (e.g., employees of the State Department or people living in the Mountain West) and are technically owned by their depositors (called members). Because of this structure, credit unions are supposed to pay more generous interest and make loans at more favorable rates.

The credit union construct is a bit convoluted to unpack, but you can think of the NCUA as similar to the FDIC but due to American Exceptionalism, is somehow not the same thing (🙃). Deposits at credit unions totaled $1.75 tn at the end of Q3 2021 — not as much value as is stored at banks, but a substantial amount nonetheless.

**A crypto question that could be answered by the NCUA: should credit unions be allowed to facilitate the buying and selling of crypto assets for their members?**

{{< figure
  src="/2022/galaxy_imageFIVE.webp"
  alt=""
  class="img-caption"
  caption="**The Empire Strikes Back**: Legacy financial services smuggle the US away, knowing full well that policymakers could accomplish their statutory and policy objectives by embracing crypto products and services that address longstanding issues still present in the failing, increasingly obsolete model of legacy financial services." >}}

If it’s hard to distinguish between the different prudential regulators, don’t worry. The US financial regulatory system is very fragmented — we’re actually lucky to have just four prudential regulators!

The takeaway point for most people should be that there are four prudential regulators, and each is an independent actor which has significant authority to control the financial system. All four regularly examine their depository institutions and have a significant — effectively, final — say over their institutions’ business decisions and practices.

### Regular-Person Protectors

The driving idea of regular-person protection is that regular people either *can’t* or *shouldn’t have* to make the same analyses of costs, benefits, and risks as businesses or professionals. For example, in general, you shouldn’t have to worry about whether your bank will arbitrarily steal your money — there one day and gone the next — so there are rules that say banks can’t rug your savings account (paraphrasing). An example from the non-financial world might be even more compelling: if you buy a car, you shouldn’t have to worry whether the seat belt will work or not — or even if it has a seat belt.

*The Securities and Exchange Commission (SEC)*

The SEC is charged with protecting regular people in their capacity as investors. Most people know about the SEC because it’s been most active in the crypto space, in particular prosecuting ICOs and other crypto products as the unregistered issuance of securities. Investor protection at its most basic is trying to ensure that the people issuing securities don’t exploit asymmetric information about the value of the security.

**A crypto question that could be answered by the SEC: is the sale of a certain crypto-token a security, requiring registration or the assertion of an exemption?**

*The Commodity Futures Trading Commission (CFTC)*

The CFTC is charged with protecting regular people in their capacity as futures and derivatives traders. While commodities futures have been… ~funky~ recently, futures and derivatives are usually essential to global commerce because they allow businesses and individuals to efficiently price, buy, and sell risk. The notional value traded in the derivatives markets reaches into the trillions of dollars per year, far eclipsing that in the equities or crypto markets.

**A crypto question that could be answered by the CFTC: if a crypto-token is a commodity (like bitcoin), does the CFTC have the authority to regulate its spot trading on venues such as Coinbase?**

*The Consumer Financial Protection Bureau (CFPB)*

The CFPB is charged with protecting regular people in their capacity as consumers of financial products. These are the products most of us use on a daily basis: bank accounts, mortgages, credit cards, and the like. Due to its unique structure, such as receiving funding from the Federal Reserve instead of Congress, and authorities, such as the charge to prosecute unfair, deceptive, and abusive acts and practices (known as UDAAPs), it is a uniquely powerful regulatory agency. The CFPB has been virtually silent when it comes to crypto.

**A crypto question that could be answered by the CFPB: should crypto wallet providers be required to provide refunds to a consumer in the case of a hack or a scam?**

*The Federal Trade Commission (FTC)*

While not strictly a financial regulator, the FTC is an important consumer protection authority, especially in the areas of data security, privacy, and fraud. Similar to the CFPB, it is authorized to prosecute “unfair or deceptive acts or practices in or affecting commerce,” which is a broad authority. It also has antitrust authorities.

**A crypto question that could be answered by the FTC: is it permissible for exchanges to permanently track the flow of user funds once they are transferred off of the exchange and to use that information for commercial purposes, like advertising?**

{{< figure
  src="/2022/galaxy_imageSIX.webp"
  alt=""
  class="img-caption"
  caption="**Return of the Jedi**: The crypto community cradles the US, which has come to realize that crypto-assets’ unique bearer-style ownership, their radical transparency, and their permissionless systems make them a generational tool for financial inclusion. Policymakers and cryptonatives are on the same team. Photo taken August 2026." >}}
Since the Bitcoin white paper — and even before — crypto has promised consumer applications in payments, trading, value storage, and other areas. And now it seems like we may finally be seeing widespread consumer applications develop. As this continues, builders will need to continue paying attention to the rules and policies promulgated by the regular person protectors.

Fortunately, in the United States this often means just making proper disclosures. For the most part, provided a financial institution tells the consumer about the risks, terms, and conditions (and does so fairly and accurately), it is free to offer something to the consumer, who can then choose to use or not use the product. [^3]
[^3]: This may change — it seems there’s a growing skepticism of a regulatory regime based primarily on disclosure (e.g., for consumer privacy). I think that is one of the top regulatory trends to watch.

### Treasury Bureaus

The Treasury Department is best known as the cabinet-level agency that coordinates and implements the President’s economic and financial policy. The Treasury Secretary, generally one of the most important cabinet secretaries, also has important foreign affairs and national security responsibilities. But 98% of the Treasury Department’s employees work for its bureaus, semi-independent agencies that are charged with carrying out specific functions. Two Treasury bureaus are particularly important to the crypto-ecosystem: FinCEN and the IRS.

*The Financial Crimes Enforcement Network (FinCEN)*

FinCEN is responsible for investigating, preventing, and enforcing against illicit finance (often called AML/CFT, short for anti-money laundering and countering the financing of terrorism). In general, this is accomplished by requiring that financial institutions report suspicious activity to FinCEN, which then investigates. The prudential bank regulators supervise banks for AML/CFT compliance, and FinCEN requires non-bank financial institutions to register as federal money services businesses, maintain an AML compliance program, report suspicious activity, and submit to periodic (albeit infrequent, given limited resources) examinations on the sufficiency of their AML program.

**A crypto question that could be answered by FinCEN: what reporting are financial institutions obligated to make when a customer sends cryptocurrency to an unhosted wallet?**

*The Internal Revenue Service (IRS)*

As the United States’ tax authority, the IRS is implicated in most activities involving the gain, loss, or movement of value. Tax rules and reporting for cryptocurrency are complicated, and the rules can have serious implications for the crypto-ecosystem.

**A crypto question that could be answered by FinCEN: should individuals making transfers of cryptocurrency worth more than $10,000 be required to fill out a lengthy and burdensome §6050I report?**

### Conclusion

[At the end of the Original Trilogy](https://www.youtube.com/watch?v=fiqvBOfeVUM), Luke Skywalker towers over a vulnerable Darth Vader, lightsaber outstretched. The Emperor stalks behind, goading him to strike the killing blow. To do so would be warranted; in their last engagement, Darth Vader severed Luke’s hand, a fact which Luke considers with horror. Ultimately, though, he backs away. Together, Luke and Anakin overthrow the Emperor and free the Galaxy from the Empire.

While perhaps slightly strained, it’s an apt metaphor for the current moment. Crypto *has* been wronged by some incomplete or ill-considered regulation. But in order for crypto to achieve its maximum impact — if we want to extend **to the maximum number of people** monetary freedom and politically neutral payments and seizure-resistant stores of value and new forms of digital commerce and on and on and on — then **crypto must embrace and help craft sensible regulation in the US**. All of the regulators listed now care about crypto. And crypto should care about them. To do so is, fundamentally, to be hopeful and bullish on the industry’s potential and ability. The Galaxy awaits.

{{< figure
  src="/2022/galaxy_imageSEVEN.png"
  alt=""
  class="img-caption"
  caption="" >}}

*My sincere thanks to [Michael Mosier](https://twitter.com/m_mosier_) for his review & comments. These are my independent thoughts and do not necessarily represent the views of my employer. Don’t take the graphics too seriously.*