+++
title = "New developments in crypto payments policy, Consensus 2023"
description= "An overview and analysis of PayPal's statements at Consensus 2023 regarding liability coverage for crypto transfers, and what they reveal about the potential application of CFPB’s Regulation E to cryptocurrency payments."
date= 2023-04-29
tags = ["crypto", "policy", "explainers", "stablecoins"]
keywords = ['PayPal', 'Regulation E', 'Reg E crypto', 'CFPB and crypto', 'crypto liability coverage', 'unauthorized crypto transfers', 'consumer protection in cryptocurrency', 'Consensus 2023 crypto', 'cryptocurrency regulation', 'financial regulation', 'electronic fund transfers']
draft=false
featured = "/2023/paypal_imageONE.webp"
+++
The most important regulatory news from Consensus 2023 will likely go uncovered. In an interview announcing a new product at Consensus, PayPal SVP Jose Fernandez da Ponte said that PayPal currently covers $50,000 of consumer liability for crypto transfers, which is in line with the requirements of the CFPB’s Regulation E.[^1]
[^1]:No one reads Terms & Conditions, so that’s why this is news today and not when the T&C were changed.

Enforcing Reg E for crypto payments has always been the most natural way for the CFPB to start regulating the crypto market, but the agency has to this date declined to ever do so (to my knowledge). Therefore, I’m always on the lookout for new developments in crypto-Reg E. PayPal’s voluntary semi-compliance is an important development in the state of crypto consumer payments regulation.

*These are my independent thoughts and do not necessarily represent the views of my employer.*

---
### Background on Regulation E
***The CFPB has not yet enforced Reg E for crypto payments.***
The key legal question that must be resolved prior to the CFPB enforcing Reg E for crypto is whether cryptocurrencies constitute “funds” under the regulation. Reg E applies to “electronic fund transfers” (EFTs) which means “any transfer of funds that is initiated through (electronic means).”[^2] There are other federal financial regulations where the term “funds” has not been interpreted to mean cryptocurrencies, such as in the SEC’s Custody Rule.[^3]
[^2]:[12 CFR 1005.3(b)(1)](https://www.consumerfinance.gov/rules-policy/regulations/1005/3/#b-1).
[^3]:The Custody Rule currently requires that RIAs hold client “funds or securities” with a qualified custodian. [17 CFR 275.206(4)-2(d)(2)](https://www.ecfr.gov/current/title-17/chapter-II/part-275/section-275.206(4)-2#p-275.206(4)-2(d)(2)). The SEC has proposed to expand the requirement to also include “other positions held in a client’s account” which the proposal says “would expressly include certain assets that may not have previously been categorized as ‘funds’ or ‘securities’” such as cryptoassets. *See* [88 Fed. Reg. 14677 (Mar. 9, 2023)](https://www.federalregister.gov/d/2023-03681/p-148).

The CFPB has never resolved the question of whether Reg E applies to crypto payments.[^4] In 2016, when considering whether to apply the requirements of its new Prepaid Accounts Rule (Prepaid Rule) to crypto wallets, the CFPB said only that “application of Regulation E and this final rule to such products and services is outside of the scope of this rulemaking.”[^5] Which is one of the most beautiful ways I’ve seen to not resolve a legal question.
[^4]:In November of 2022, the CFPB disclosed that it was investigating Nexo for alleged violation of Reg E. The CFPB had issued a Civil Investigative Demand (CID) to Nexo requiring testimony, and Nexo petitioned the CFPB to set aside the CID (the petition was denied). This disclosure went unnoticed. We don’t at this point know, however, whether the CFPB is investigating fiat EFTs or crypto EFTs, so in my opinion Reg E has still not been enforced for crypto. [Petition here](https://www.consumerfinance.gov/enforcement/petitions/nexo-financial-llc/).
[^5]:[81 Fed. Reg. 83978 (Nov. 22, 2016)](https://www.federalregister.gov/d/2016-24503/p-618)
In purely my personal opinion, it seems to me that cryptocurrencies are obviously “funds” under a straightforward reading of Reg E. Therefore, it seems inevitable to me that Reg E will be enforced for crypto payments or need to be amended in some way. To solicit ideas for how to make the rule workable given crypto’s lack of network-determined liability allocation (as exists for cards, ACH, and other fiat networks), the CFPB could publish a narrow request for comment on the matter.

***Reg E limits consumer liability for unauthorized transfers.***

Reg E requires, among other things, that financial institutions limit consumers’ liability for unauthorized transfers (i.e., refund consumers’ losses) to a level determined by how quickly the consumer reports the unauthorized transfer.[^6] You may have benefited from this protection if your bank account, debit card, or digital wallet has ever been hacked or stolen. For example, a few years ago I noticed $400 had been withdrawn from my bank account through an ATM that I had not visited. I called my bank, and they refunded all of my money — not due to good customer service, presumably, but because of Reg E.
[^6]:[12 CFR 1005.6.](https://www.consumerfinance.gov/rules-policy/regulations/1005/6/)

Reg E specifies no maximum amount of reimbursement that may be required from a consumer’s financial institution. If I hold $1m in my bank and I am hacked for $1m, the bank would be responsible for refunding substantially all of my loss provided I reported the hack in a timely manner. Therefore, traditional financial institutions impose transaction limits and delays, or they require additional authorizations/verifications to move larger amounts of money to limit their potential liability. Some crypto companies may do the same, but I can’t think of any off the top of my head.

***Liability allocation is the central question for making Reg E workable, and it is very challenging.***

Regulation E initially places the responsibility for refunding all of a consumers’ hacked or stolen funds on the consumer’s financial institution only. For example, in the above scenario, the consumer’s financial institution would be solely responsible for refunding $1m. This is obviously a significant business hazard and may also be not right. Maybe the hacker’s financial institution, to which the funds were transferred, knew or should have known that the funds movement was suspicious. Therefore, what happens in practice is that financial institutions trace the unauthorized funds and allocate liability among themselves so that the consumer’s financial institution is not always 100% liable for the refund. This structure helps the consumer because he doesn’t have to negotiate with massive financial institutions on his own. Instead, financial institutions — who are more likely to have equal bargaining power and also have a recurring relationship — can settle out in the course of normal business.

In the traditional finance world, private network rules govern this process. For example, the ACH network has rules written by NACHA, the network’s administrator, and the debit card networks have their own network rules. Regulation E recognizes this reality and uses the existing structures to make its liability limitation requirement workable. It permits financial institutions to contract away liability to other financial institutions (i.e., to have private network rules) provided the consumer is made whole.[^7]
[^7]:*See* [12 CFR 1005.4(d).](https://www.consumerfinance.gov/rules-policy/regulations/1005/4)

In crypto, though, it’s less feasible for network participants to coordinate in the same way because communication is difficult, and additionally, there may not be a way to require participants in a transaction to refund unauthorized fund transfers (in the fiat world, the ACH or debit network can kick out financial institutions that don’t follow the rules). Therefore, if Reg E were applied to crypto payments today, without any supplementary work, it would likely result in an incredibly burdensome and unworkable regulatory regime.[^8]
[^8]:For a glancing discussion of this issue, *see* Jess Cheng and Amy Caiazza, "U.S. Banking Collapse Doesn’t Necessarily Make Crypto Trustworthy," CoinDesk (Mar. 16, 2023), [https://www.coindesk.com/consensus-magazine/2023/03/16/us-banking-collapse-doesnt-necessarily-make-crypto-trustworthy/](https://www.coindesk.com/consensus-magazine/2023/03/16/us-banking-collapse-doesnt-necessarily-make-crypto-trustworthy/), concluding, “The crypto community might consider developing clear, enforceable legal terms or system rules that leverage this fundamental loss-spreading principle — beyond operational losses and on an industry-wide basis.”
While beyond the scope of this blog, I don’t think this is either an unprecedented or impossible problem to solve. It’s not an unprecedented problem — a similar situation exists now for scam payments, which are authorized (and therefore not subject to Reg E’s protections) but fraudulently induced. I also don’t think it’s impossible to resolve with some combination of on-chain identity, on-shoring of activity, and novel legal frameworks.
---
### PayPal’s Announcement and its Reg E Coverage
PayPal yesterday [announced](https://www.coindesk.com/business/2023/04/28/paypal-to-enable-on-chain-transfers-from-venmo-accounts-including-to-on-chain-wallets/) that the feature it had enabled last year for PayPal customers enabling normal crypto network transfers was now being enabled for Venmo customers. To me, the announcement was pretty mundane, but the PayPal representative did point out that PayPal already offers $50,000 of coverage for EFTs. Looking at PayPal’s cryptocurrency account terms, PayPal [says](https://www.paypal.com/us/legalhub/cryptocurrencies-tnc#:~:text=applicable%20form%201099.-,Liability%20for%20Unauthorized%20Transactions%2C%20Errors%20and%20Support,-PayPal%20will%20protect) it will “protect you from unauthorized activity involving the purchase or sale of Crypto Assets in your Cryptocurrencies Hub, including for unauthorized sales used to Checkout with Crypto” and will reimburse customers for “up to a maximum lifetime cap of an equivalent of $50,000.00 U.S. dollars over the life of the accountholder.”

{{< figure
  src="/2023/paypal_imageTWO.webp"
  alt=""
  class="img-caption"
  caption="Selection from PayPal’s Cryptocurrency T&C detailing liability protection for unauthorized transfers." >}}

To my knowledge, this is the first instance of any company committing to refund consumer losses for unauthorized transfers. Cryptocurrency hacks can be [common](https://www.wsj.com/articles/sim-swapping-attacks-many-aimed-at-crypto-accounts-are-on-the-rise-11645227375) and [expensive](https://efalken.substack.com/p/my-340k-hack), so consumer protection in this space would certainly help consumers.

I thought of a few observations listening to the PayPal representative and reading the Terms, and I’ll go through them now.

***PayPal limits lifetime liability to $50k***

As discussed above, there is no limit on the liability a financial institution may be required to cover under Reg E. This indicates to me that PayPal is running their program voluntarily.

***PayPal says they are covering “purchases” or “sales” of crypto.***

Exempted from the definition of “EFT” are “securities and commodities transfers” which means, “any transfer of funds the primary purpose of which is the purchase or sale of a security or commodity” if the security or commodity meets certain conditions.[^9] Bitcoin and Ether may currently meet the conditions if a court would find that the assets themselves are “regulated by the (SEC) or the (CFTC),” but it’s not clear to me that the assets “may be sold by a registered broker-dealer or futures commission merchant.” However, it’s feasible that they will be at some point, so the assets themselves may fit the conditions in the ©(4) exemption.
[^9]:[12 CFR 1005.3(c)(4).](https://www.consumerfinance.gov/rules-policy/regulations/1005/3/#d0b279d265ee01329c7ed82449d8ce1053eea86dcb16f0e6ee50d343)

It’s less convincing to me that all payments made in cryptocurrency constitute a purchase or sale of a cryptocurrency. For example, if you buy a coffee with bitcoin, it seems to me that some English language contortions are required to call that a sale of bitcoin. Yet PayPal characterizes paying for things with crypto as “sales used to Checkout with Crypto.” I suppose you never give up a backup argument if you don’t have to.

***PayPal’s voluntary semi-compliance with Reg E mirrors the prepaid industry’s voluntary semi-compliance prior to the promulgation of the Prepaid Rule***

Prepaid cards are debit card-like products that are not connected to a checking or other “account” as defined in Reg E.[^10] Instead, prepaid cards are pre funded at the time of purchase, and some may be reloaded. Because the cards were not connected to an “account,” they fell outside the scope of Reg E, which only applied to EFTs “that authorize a financial institution to debit or credit a consumer’s account.”[^11] In 2012, given the growing popularity of prepaid cards and the potential risks for consumers associated with their use, the CFPB issued an Advance Notice of Proposed Rulemaking (ANPR) in which it announced its intention to develop rules to apply Reg E protections to prepaid accounts.[^12] The Bureau finalized the Prepaid Rule in 2016.[^10]:[12 CFR 1005.2(b).](https://www.consumerfinance.gov/rules-policy/regulations/1005/2/)
[^11]:[12 CFR 1005.3(a).](https://www.consumerfinance.gov/rules-policy/regulations/1005/3/)
[^12]:[77 Fed. Reg. 30923 (May 24, 2012).](https://www.federalregister.gov/documents/2012/05/24/2012-12565/electronic-fund-transfers-regulation-e)
[^13]:[81 Fed. Reg. 83934 (Nov. 22, 2016).](https://www.federalregister.gov/documents/2016/11/22/2016-24503/prepaid-accounts-under-the-electronic-fund-transfer-act-regulation-e-and-the-truth-in-lending-act)

Prepaid card issuers were already voluntarily providing some Reg E protections prior to the CFPB’s rulemaking. The 2012 ANPR noted, “many GPR card market participants offer contractual protections similar to those provided in Regulation E for payroll cards, though such provisions may vary, and are subject to unilateral change.”[^14] Prepaid card issuers figured that, given the similarity between prepaid cards, which were not federally regulated, and debit cards, which were federally regulated, that they should provide similar consumer protections — although perhaps limiting voluntary compliance to the most important protections and with some limits. They likely did this for both business/competitive reasons — consumer protections probably helped build consumer trust and confidence — and for political/regulatory reasons — voluntary compliance demonstrated their commitment to responsible practices. Sound familiar?
[^14]:[*Supra* note 12, at 30924.](https://www.federalregister.gov/d/2012-12565/p-22)

***PayPal is one of the few non-bank financial institutions subject to CFPB supervision due to its remittance business***

The Dodd-Frank Act gave the CFPB statutory authority to supervise depository institutions with assets over $10 billion, payday lenders, and private student lenders.[^15] It also authorized the CFPB to conduct a rulemaking to establish supervisory authority over “larger participants” (LPs) in markets which the CFPB regulates.[^16]
[^15]:[12 U.S.C. 5514–5516 (2018).](https://www.govinfo.gov/app/details/USCODE-2021-title12/USCODE-2021-title12-chap53-subchapV-partB-sec5514)
[^16]:[12 U.S.C. 5514(a)(1)(B) (2018).](https://www.govinfo.gov/app/details/USCODE-2021-title12/USCODE-2021-title12-chap53-subchapV-partB-sec5514)

In 2013, the CFPB promulgated a rule defining LPs in the international consumer remittance market. Consumer remittances (i.e., any cross-border payment sent for personal, family, or household purposes) are regulated under the Reg E provisions discussed above, and they are subject to additional rules such as remittance-specific disclosures (e.g., of the foreign exchange rate). The LP rule established a threshold of at least one million international transfers per year for an entity to qualify as a larger participant in this market.[^17] PayPal is a larger participant under the rule.
[^17]:[12 CFR 1090.107.](https://www.ecfr.gov/current/title-12/chapter-X/part-1090/subpart-B/section-1090.107)

Because PayPal meets the threshold, it is subject to the CFPB’s supervisory authority and may be subject to regular examinations. The kicker, though, is that once the CFPB establishes supervisory authority over an entity for its sale of one consumer financial product or service (e.g., international remittances), it may supervise the entity for its sale of any other consumer financial product or service (e.g., cryptocurrency payments).

I’m not aware of any other crypto company that provides any Reg E-like limitations on liability for unauthorized transfers aside from PayPal. Therefore, the business or competitive motivation for voluntarily offering Reg E protections may not be as compelling. However, given that PayPal is supervised by the CFPB, the political or regulatory motivation seems very compelling. What I think probably happened is that (1) PayPal believed that Reg E would eventually be enforced for crypto payments, despite best attempts to assert the exceptions discussed above, (2) knew it was a high profile consumer payments company subject to CFPB supervision, and (3) figured it should do its best to provide reasonable liability limitation for customers.

---
### Conclusion: Still Waiting
Applying Reg E for crypto payments in a workable way is a very tough intellectual and legal challenge. I’m thankful that the CFPB hasn’t rushed to enforce Reg E, and admittedly the use of cryptocurrencies for consumer payments is small relative to the total consumer payments market. A prudent and good-faith step to implement Reg E would be to issue an ANPR and seek feedback on the matter (including whether it’s timely and pressing to even begin a rulemaking on the topic) much as the CFPB did when it kicked off the process for writing rules for prepaid cards in 2012.

*These are my independent thoughts and do not necessarily represent the views of my employer.*