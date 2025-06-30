+++
title = "Cryptography to Cryptocurrency: Lessons on Privacy and Policy from Steven Levy’s “Crypto”"
date = 2022-07-28
draft = false
description = "An article drawing parallels between the development and political fight for cryptography and the same events happening again for cryptocurrency."
tags = ["crypto", "policy", "explainers", "stablecoins"]
keywords = [
  "public key cryptography",
  "privacy",
  "NSA",
  "Phil Zimmerman",
  "PGP",
  "cryptography history",
  "crypto privacy",
  "blockchain privacy",
  "crypto regulation",
  "Clipper Chip",
  "digital privacy",
  "cryptocurrency policy",
  "crypto advocacy",
  "crypto adoption",
  "government surveillance"
]
featured = "/2022/crypto_imageONE.webp"
+++
> The practice (of preserving anonymity) was crucial in the formation of the United States itself, and was arguably as American as apple pie. As cypherpunk historians loved to point out, the model for the Ender’s Game debate may have been the Federalist Papers, with parts written by James Madison, John Jay, and Alexander Hamilton but published under the pseudonym Publius. And when Thomas Paine wrote Common Sense, he originally signed it “An Englishman.” As the Supreme Court would note, “Anonymous pamphlets, leaflets, brochures, and even books have played an important role in the progress of mankind,” a role the Court has sustained in consistent ruling.

*Steven Levy in "Crypto: How the Code Rebels Beat the Government Saving Privacy in the Digital Age," pg. 222*

---
Before COVID-19, Bitcoin had its own “lab leak” hypothesis. The NSA, the story goes, created Bitcoin, built in a backdoor, mined one million coins, and then released the experiment onto the world to track everyone/preempt the dominance of another country’s currency/fund black ops/etc. While probably untrue, you could be forgiven for finding it plausible: the NSA developed its own version of public key cryptography years before Diffie and Helman published their first research paper. Instead of publishing the idea, though, it kept the technology sequestered inside its secretive lab at Fort Meade.

This anecdote from Steven Levy’s “Crypto: How the Code Rebels Beat the Government Saving Privacy in the Digital Age” is just one of many instances in which the development of consumer-grade internet cryptography — followed by its ubiquitous use now— seems eerily similar to the situation in which crypto*currency* finds itself today. The book is a nonfiction documentation of the public development of public key cryptography, its first commercial implementations, and the US Government’s constant attempts to suppress it. The fact that Levy wrote the book in 2005, three years before the NSA published the Bitcoin White Paper, makes the parallels even more compelling.

See for yourself. Below are select passages from Crypto with some commentary about modern day parallels. All quotes are verbatim, although I’ve disposed of some ellipses for convenience.

*These are my independent thoughts and do not necessarily represent the views of my employer.*

{{< figure
  src="/2022/crypto_imageONE.webp"
  alt=""
  class="img-caption"
  caption="Ron Rivest, Adi Shamir, and Leonard Adleman, the creators of RSA cryptography. RSA used a one-way function to enable public key cryptography." >}}

Ray Ozzie was the lead developer for the Lotus Notes program, one of the first commercial implementations of public key cryptography. Notes users were imagined to be businessmen and women who needed to send messages over the internet that potentially contained highly sensitive trade secrets. The impetus for adding cryptography to Notes was the same for developing Bitcoin:
>Ozzie continued to describe the way a traditional computer security system would deal with the problem, that is, via a central authority — essentially, a mandatory hub through which all traffic passed. If the central authority screwed up, turned cooked, or turned you in, the whole system failed. Its very spirit was locked into an age that was destined for the junk heap.
>Ozzie saw Notes not only as a pioneering project but also as a seminal example of the networked future, where the masses would have their own computers and not have to check in with some massive digital Big Brother. Like the phone system, communications would be one-to-one, people communicating directly with their peers.

Satoshi said, “the problem with centralized systems is all the trust that is required for it to work.” Reliance on a central intermediary exposes valuable data and sensitive information, and if the intermediary fails, your valuables are suddenly out in the open. It was the same problem in 1984, and Ozzie replaced the intermediary with cryptography, substituting mathematical truth for trust.

---
Not everyone was on board. Ozzie had to bat down bad proposals.

>“We believe this is a bad approach,” wrote Ozzie of the central-authority model. “It changes the distributed nature of the network back into the old ‘centralized data’ approach of mainframes… It also resurrects the problems with the ‘traditional solution,’ that is, trust in people and/or mechanisms that are completely understood.”

Trusted, centralized systems are the model we already have. *Public* key cryptography and *public* blockchains are the innovation. Sharing this paragraph with every Fortune 500 CEO could have saved billions in R&D spend over the past decade.

---

Phil Zimmerman founded PGP, a way to encrypt and authenticate communications, and released it to the public. Levy on Zimmerman…

>Zimmerman was also a sophisticated political activist who had twice been dragged off to a holding pen for asserting his opinion. He now understood that in the computer age, government had an extremely powerful tool for monitoring dissent: electronic surveillance. Not only could Big Brother types stick their collective ear into phone conversations, but they could pluck the increasingly popular e-mail messages out of the digital ether and read business plans and shameful secrets to their black, black hearts’ content. While electronic mail was a terrific thing, it actually represented a step backward in privacy: even with relatively insecure physical mail, people had sealed envelopes to protect the privacy of their messages.

Do I have to be the one to say it? Transactions on public blockchains right now are a privacy nightmare. All of your on-chain activity is publicly recorded for use and collection by anyone interested enough to try, and it can easily be connected to your real-life profile by anyone who has (or ever obtains) the requisite information, such as your exchange or a merchant. But on-chain privacy is in the same state as our electronic communications were back in the 1990s. Soon, everyone realized that it was imperative to encrypt messages — at least during transmission — and encrypted email is now the default. If crypto financial systems are going to become mainstream tools for everyday commerce and financial activity, privacy-preserving tools and protocols *must* become mainstream.

Privacy-preserving technologies for crypto assets are needed and legal. The ability to use a mixer, a zero-knowledge protocol, or a privacy coin should be as much of an afterthought as the ability to use email, Signal, or encrypted data storage. When this happens, some law enforcement and bad actors may not be happy, but it doesn’t matter: privacy ought to be our right.

Separately, from a policy and advocacy perspective, I believe we need to move away from the “blockchains are always more traceable” talking point. What happens when blockchains aren’t traceable? The argument can’t be that users on blockchains have no privacy; it must be that we prefer to liberally preserve rights, even if bad actors may sometimes exploit that generosity.

---

When the public developed public key cryptography, the NSA attempted to shut it down, alleging it was a national security concern. The NSA threatened businesses like Jim Bidzos’ RSA Data Security Inc. (the company formed by Rivest, Shamir, and Adleman to monetize RSA public key cryptography) with all manner of threats in an attempt to stop the proliferation of the technology.

>According to Bidzos, the final NSA attempt at sabotaging the deal came when an agency official called (Microsoft CTO Nathan) Myhrvold and said, basically, “Don’t do (the deal with Bidzos).”
>
>Bidzos was furious. As he recollects now, he dialed up the highest ranking person he knew and laid out what he had heard. Then, before his contact could utter a word in reply, he demanded that the official fix the problem and call Microsoft back to tell them that the agency had made a big mistake. “If that doesn’t work, you’re going to answer to the congressman in my district,” he said. “If that doesn’t work, you’re going to answer to a district attorney, because I’m going to file a complaint. If that doesn’t work, I’ll try the New York Times. But one way or another, if you don’t fix this, I’m gonna make you answer for it.” Bidzos more or less expected his contact to deny everything, or at least insist that he knew nothing of the sabotage. Instead, Bidzos claims, the man said, “I’ll call them.” And, according to Bidzos, his contact called Microsoft and recanted.

While I don’t know of any parallel in the ongoing cryptocurrency saga, I like this passage because it showcases Bidzos’ excellent sense of all of the political tools at his disposal. Politics is incredibly complex, and outcomes are not linear (e.g., the president wanted a policy, so that’s what happened). There are thousands of levers to pull to get what you want — Act of Congress, congressional oversight, agency rulemaking, corporate comms, talking to the press, working through political elections, local politics, and many other strategies.

---

Separately, Zimmerman was promoting PGP.

>Zimmermann talked, and generated publicity. He seldom failed to note that Burmese rebels reportedly used PGP to avoid the deadly consequences of being discovered in antigovernment activities in testimony he also noted that he’d received an effusive thank-you from a Latvian patriot. When confronted with the charges from law enforcement agencies that PGP was particularly useful to criminals — in one Sacramanto case, the cops couldn’t read a pedophile’s diary encrypted with Zimmermann’s software — he argued that all technology has trade-offs.
>
>Perhaps the highlight of Zimmerman’s odd celebrity came one day in San Francisco. The young lady lap dancing in proximity to Zimmermann asked casually what he did. (He told her).
>
>The lapdance stopped in midgyration. “You’re Phil Zimmermann?” she asked in awe. “I know all about PGP!”

Rebels abroad; dissident patriots (branded as terrorists); sex workers; and, yes, despicable groups such as pedophiles. The first adopters of cryptography and cryptocurrency.

---

>In a draft of Senate Bill 266, introduced January 1991, Biden (then the chair of the Senate Judiciary Committee) inserted some new language:
>
>“It is the sense of Congress that providers of electronic communications services and manufacturers of electronic communications service equipment shall ensure that communications systems permit the government to obtain the plaintext contents of voice, data, and other communications when appropriately authorized by law.” [Emphasis added].
>
>That sentence was included at the explicit request of the FBI. And what a sentence it was! It plunged a virtual dagger into the heart of the crypto revolution.
>
>To Zimmerman, S. 266 was the ultimate deadline. If he didn’t get PGP out into the world now, the government might prevent its very existence.

Phil Zimmerman and his friends uploaded PGP to the internet, where it spread across the world instantly.

>Ironically, Joseph Biden’s offending language, the impetus for Zimmerman’s extraordinary step, met a much less enthusiastic response than PGP did. Senator Biden had been taken by surprise at the huge expression of public outrage (fueled by civil liberties groups) at the stealth antiprivacy language he had introduced. By June, he had quietly withdrawn the clause.

The United States has already debated the validity and merit of privacy-preserving technologies. And? We decided that they are valid and meritorious. The legitimate interest of the people in protecting their communications trumped any government interest in stopping theoretical bad guys, real or not. [The same protections ought to extend to our rights to transact.](https://www.coincenter.org/the-case-for-electronic-cash/#the-moral-case-for-electronic-cash:~:text=Even%20when%20the%20government%20might%20know%20that%20one) In 1991, it was a strong, coordinated public reaction and political coalition that prevented a harmful US Government stance from developing.

But equally, it required Phil Zimmerman to build and launch a product that people loved and found useful. PGP is still used today. If millions — hopefully billions — of people onboard to crypto products, the public policy case gets a lot easier to make.

---

Seeking a compromise, the NSA proposed a “Clipper Chip,” a proprietary encryption microchip that would encrypt data for commercial users but featured a backdoor ostensibly only accessible to the NSA. Levy writes,

>The very basis for the scheme — a government means by which to flip the “descramble” switch for its own purposes — was offensive to most people. All opponents had to do was use a simple analogy — What if you had to leave a copy of your front door key at the police station? — and even a Joe Sixpack who didn’t know encryption from a forward pass would be an anti-Clipper convert. “The idea that government holds the keys to all our locks, even before anyone has been accused of committing a crime, doesn’t parse with the public,” explained Jerry Berman of the EFF. “It’s not America.”

Call me naïve, but I agree. It took advocacy and hard work to push back, but the Clipper Chip never had a shot. That’s not America.

>The government did its best to defend the scheme. (NSA General Counsel) Stewart Baker briefed industry figures… Your view of privacy, he told them, reflects a hopelessly naïve view of the world. “By insisting on having a claim to privacy that is beyond social regulation, we are creating a world in which [crooks and terrorists] will flourish and be able to do more than they can do today,” Baker warned.

Same old same old.

---
We won, and the Clipper Chip was never implemented. Instead, export control rules regarding commercial cryptography were relaxed by an Act of Congress.

>By 1999, an emboldened Congress was finally rallying around the SAFE bill, the three-year-old proposed legislation to relax the export rules.

Given these eerie similarities, perhaps the timeline for cryptography’s acceptance can inform our understanding of where we are in the cryptocurrency policy evolution. Diffie-Hellman key exchange was published in 1976. The NSA immediately took notice and attempted to contain the technology, working behind-the-scenes in the government and directly with private companies. Lotus first attempted to introduce encryption to a major commercial product in 1986. Major legislation concerning cryptography first emerged in 1992, and it took until 2000 to pass a law loosening the export restrictions, 24 years after the first paper on cryptography.

Now cryptocurrency: While other experiments predate Bitcoin, the White Paper was published in 2008. At a high level, I think it is reasonable to say that “broad” adoption of cryptocurrency has only started recently, mostly with [stablecoin payments and bitcoin savings](https://www.wsj.com/articles/turks-pile-into-bitcoin-and-tether-to-escape-plunging-lira-11641982077) serving people around the world. While advocates in Washington have been fighting the good fight for almost a decade, major attempts by the government to regulate cryptocurrency outside of AML and tax exploded in Fall 2021. 24 years after the Bitcoin White Paper is 2032.

While it may not feel like it in the whirlwind of our industry, adoption and regulation take time — a lot of time. That is just one way in which the story of the emergence of commercial encryption can inform our advocacy for cryptocurrency today. It should also firm our resolve on important topics: privacy-preserving technologies have been villainized before; commercial demand for such technologies **will emerge**; and the United States thoroughly litigated the issue in the past, and we decided for personal liberty.

*These are my independent thoughts and do not necessarily represent the views of my employer.*