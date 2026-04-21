+++
title = 'The Self-Executing Whitepaper'
date = '2026-04-16'
description = 'April 2026'
summary = "April 2026"
summary_image = '/2026-04-16-the-self-executing-whitepaper-long-downscaled.png'
featured_image = '/2026-04-16-the-self-executing-whitepaper-longer-downscaled.png'
images = ['/2026-04-16-the-self-executing-whitepaper-longer-downscaled.png']
featured_image_caption = 'Trudy Cooper, Ouroboros.'
tags = ['Api3']
+++

The year is 2016. I need to pick a PhD subject, and I can already see that if it isn't deep learning, it will soon become irrelevant.
One problem though: I need lots of compute for that, and I'm a solo researcher with no lab.

At the time, the most cost-effective way to obtain parallel compute is to get as many top-of-the-line Nvidia gaming GPUs as one can—in this case, the GTX 1080 with 8GB of VRAM.
I apply for a grant, which affords me a quad GTX 1080 rig.

{{< figure src="/2026-04-16-the-self-executing-whitepaper-gpu.jpg" caption="The beginning of an arms race that I would concede early on." >}}

Not long after that, my setup starts falling short of being able to train the state-of-the-art models with the largest architectures.
I realize that my hardware will age even faster than expected, and that I should keep stacking GPUs if I want to continue playing in the big leagues.
I apply for another grant to add two of the new GTX 1080 Ti cards with 11GB of VRAM to my system.

Once my grant is approved, I kick off the procurement process.
This coincides with Turkey detaining an alleged American spy and Trump tweeting in response, triggering an exchange rate shock for the TRY.
An administrator at the university halts my GPU procurement as an austerity measure.

Desperate to salvage my academic career, I print my recent paper on power line avoidance, published in a prestigious aerospace electronics journal, along with news clippings about Turkish military helicopter crashes caused by power lines, and visit the administrator at his office.
The implication is clear:
While trying to score points by cutting costs, he could find himself in the position of blocking research that could benefit our domestic military industry and protect our soldiers.
A middle ground is reached.
I get one GTX 1080 Ti.

That I had to resort to theatrics must have betrayed that I had no leverage to follow through.
Nevertheless, any risk of appearing unpatriotic is absolutely dreadful to a careerist civil servant.

<div style="text-align: center"> — </div>

The anatomy of this maneuver is worth spelling out.
Most people like to believe that proposals succeed on intrinsic merit—that they only need to be factually correct and logically sound.
Savvier people have game theory in their toolbox:
The audience of the proposal must have something to gain from accepting it, and something to lose from rejecting it.
That's closer to the truth, but often still not enough.
In reality, the audience is irrational, and the most effective way to ensure that a proposal gets carried through is to leverage the desires and aversions of the audience.

{{< figure src="/2026-04-16-the-self-executing-whitepaper-writing-science.jpg" caption="Even when the subject is hard science, the reader is human. This book explains that well." >}}

Because a successful proposal is a reflection of the psychological states of its audience, it ends up being more a product of its audience than of its author.
The idealistic alternative, where the author refuses to compromise, is dead on arrival.

<div style="text-align: center"> — </div>

The original insight that led to the founding of Api3 is that if smart contract platforms were ever to serve real-world (i.e., non-financial) use cases, they would depend on APIs—and therefore on the businesses providing them.
Those businesses would then be positioned to capture most of the value generated.
The oracle architecture most aligned with this is one where each API provider operates as a micro-oracle project that monetizes its on-chain services itself.
Api3 would provide tooling for this and act as a cooperation layer for these micro-oracle projects.

That was the vision, but proposing it plainly would have failed to land.
In fact, I had already written [that whitepaper](https://github.com/chainapi/honeycomb-whitepaper), and found this to be the case.
A rational argument alone is not enough.

Our aim was to create oracles unlike any that had ever existed to enable real-world use cases of smart contracts.
At the same time, Chainlink had just sacrificed their original vision to achieve product–market fit.
They let two early DeFi projects dictate the spec for what became "data feeds"—a product built to arbitrary requirements and then pushed to the entire industry as a standard.
Even though Api3 and Chainlink were pursuing fundamentally different objectives, the whitepaper plausibly argued that API-centric oracles would also be better suited to provide data feeds.
This narrative resonated with investors and was crystallized by the moniker ["Chainlink killer."](https://www.coindesk.com/business/2020/11/12/chainlink-killer-api3-closes-3m-funding-round-with-placeholder-and-pantera)

<div style="text-align: center"> — </div>

That addressed the desires.
Now for the fears.
Although the pitch sounded attractive and we weren't showing any red flags, people were uneasy about handing us the reins because we didn't tick enough boxes to overcome a baseline of distrust.
The solution was to introduce DAO governance.
This would hamstring us in carrying out the proposed vision, but only until we could establish the necessary trust.
In return, it eliminated every "but what if?" lurking in the minds of the audience.

DAO governance was particularly well-suited here; it was gaining traction as a general concept when I was writing the whitepaper, and was also beginning to be seen as a solution to Chainlink's governance shortcomings.
To illustrate: below is an exchange with a fellow Chainlink node operator from two weeks before the whitepaper was made public.

{{< figure src="/2026-04-16-the-self-executing-whitepaper-tg.png" caption="While venting about Chainlink, the first thing he arrives at on his own is \"make a DAO.\"" >}}

<div style="text-align: center"> — </div>

As a result of these finishing touches to the whitepaper, Api3 received a dual mandate: "API-centric oracles" but also "better Chainlink with a DAO."
I figured this was workable if we just built the API-centric oracles, which could naturally serve data feeds among other use cases.
My expectation was that the DAO would eventually deprioritize data feeds once it recognized that they were an unprofitable market to begin with, and that we could be serving a blue ocean of use cases instead.
DAO governance would legitimize the divergence, since it would be the token holders' own decision.

As the first order of business, I built the DAO so that every decision made post-whitepaper would be ratified by it.
Its implementation is fully trustless, even forgoing centralized security features that could be abused.
The API3 Foundation is controlled by the DAO and owns any off-chain assets such as intellectual property and domains, giving the DAO an unusually wide reach.

For this to hold in practice, I proposed frameworks for governance participation beyond voting ([[1]](https://medium.com/api3/api3-builder-terminology-dd398fe447c3) and [[2]](https://medium.com/api3/fractal-scaling-of-api3-b3ba78c9dcb7)).
I also tried to establish a high standard of accountability with the core technical team proposals I made, writing [monthly progress reports](https://blog.benligiray.com/post/2023-08-31-api3-core-technical-team-reports/) and detailed financial reports upon each delivery.

The effort that went into this is worth pointing out because it's out of the ordinary.
In the case of projects with significant operational workload, the teams undertaking the work often implement DAOs in a way that allows the team to undermine them in case of disagreement, essentially performing "decentralization theater."
In our case, DAO governance was a fundamental ingredient that elevated the whitepaper by neutralizing distrust.
Beyond ethical considerations, failing to follow through with implementing the DAO as described would have undone what the whitepaper accomplished.
This put us in a position that necessitated building a true DAO, and this difference is what makes the rest of this story interesting.

<div style="text-align: center"> — </div>

The whitepaper was designed around three principles:

1. The audience has irrational desires and aversions, and an optimal whitepaper must address these to maximize support, which is often a requirement to get off the ground.
2. Failing to follow through with the whitepaper will result in losing the support that it garnered.
In other words, a bait-and-switch is a self-defeating strategy.
3. If the whitepaper mandates governance by a true DAO, the project can course-correct for any suboptimal aspects in its original conception.

Unfortunately, the third one backfires in practice, because the DAO proposals are considered by the same irrational audience that the whitepaper was written for.
This results in a self-sealing system that is only able to execute the original whitepaper.
Furthermore, the system is selective:
It particularly wants to execute aspects of the whitepaper that appeal to impulses.
In our case, this meant that the DAO increasingly latched on to the ideas of competing with Chainlink and minimizing delegated authority, and continually strayed from the goal of building API-centric oracles.

<div style="text-align: center"> — </div>

The tension between the mandates created two major fault lines throughout the history of the project.
After launching the current version of the DAO in July 2021, I started making quarterly proposals that focused the core technical team's efforts on [Airnode,](https://medium.com/api3/airnode-the-api-gateway-for-blockchains-8b07ff136840) the node that would enable API-centric oracles.
Once Airnode was mature enough, I planned to put it to work serving data feeds, among other things.
Building an all-purpose oracle node takes a lot of time.
Not wanting to wait, the DAO passed another proposal as early as August 2021 to implement data feeds using the non-feature-complete version of Airnode.

In addition to seeing Airnode as a prerequisite for data feeds, I had a more practical reason to defer the latter:
Operating a data feed was about 1000× more costly than it is today, mostly due to the obscene Ethereum gas prices at the time.
Subsidizing data feeds even just long enough to establish a credible track record would have blown through our treasury.
The problem was recognized not long after the premature data feed proposal passed.
The team pivoted to implementing a random number generation solution and disbanded soon after.

This chain of events proved my original thesis:
Data feeds weren't viable as a business at the time.
That should have liberated us from the "better Chainlink" mandate and let us focus on API-centric oracles.
Yet that did not happen.
The DAO continued insisting that data feeds were overdue and that no meaningful work could be done on the business development and marketing side without them, even though we were building a unique and potentially impactful piece of infrastructure in Airnode.

At this point, I was leading the core technical team and acting as its sole senior blockchain developer, mainly because good blockchain developers were effectively unhireable in 2021—rather than join a team, they could just as easily launch their own projects into a bull market and take a founder's allocation, or so it seemed.
The only other technical co-founder was occupied building his own team from scratch for a parallel effort—ChainAPI—leaving me to do the same for the core technical team.
This gave me complete veto power over the technical direction despite not having a controlling vote in the DAO, because realistically, anything that I didn't choose to work on wasn't going to be built.
Call it selflessness or a martyr complex, but I decided to help the DAO see data feeds to completion.

<div style="text-align: center"> — </div>

Towards the end of 2022, data feeds and the first version of the market interface went live.
By this time, DeFi activity had started spilling over to Layer 2s and alternative Layer 1s, which meant we could subsidize data feed operation gas fees without breaking the bank.
We finally had data feeds, yet selling them proved to be more challenging than the DAO anticipated.
Instead of conceding that their lobbying had rested on a false premise, a sizable group convinced themselves that we should "do OEV" to make data feeds viable as a business model, threatening to spin off (i.e., fork the project) if we didn't.

What they meant by "doing OEV" was auctioning off the right to perform data feed updates so that third parties could extract value from the transaction ordering.
I had a solid counterargument:
It was already technically possible for third parties to frontrun our updates without paying anything, yet they were not doing so.
(My explanation is that the opportunity cost of running such an operation is much greater than what most people estimate.)
It was illogical to assume that people would compete in an auction for something they could have for free—the lack of product–market fit seemed self-evident.
We didn't have to discard the idea, though, as this very well could have been the future of data feed monetization.
We could simply monitor for frontrunning activity and start building OEV auctions as soon as we detected any.
Nevertheless, the general position of the DAO was "building data feeds should have worked, the fact that it didn't must mean we didn't build enough, and this OEV thing sounds promising."

An OEV fork of Api3 didn't make sense in practice.
The people behind it wouldn't have been able to operate data feeds reliably, let alone build a workable OEV auction solution.
And even if they had, the revenue would have been negligible for all but a handful of the largest DeFi protocols, none of which would have used their fork.
Nevertheless, they would have had at least a year to run the narrative and appear to be working on it publicly, and that would have been poisonous for Api3.
Once again, I found myself choosing between doubling down on data feeds and walking away.
I made the same choice as before:
I took the OEV auction project under the core technical team's wing, and even [authored](https://blog.benligiray.com/post/2022-11-01-oracle-extractable-value-oev/) an article for its announcement.

<div style="text-align: center"> — </div>

In early 2023, the OEV work had just started, and I didn't intend to let the DAO lead me into a second death march.
I had the dAPI team split off from the core technical team to manage data feed operations independently.
Later, I asked for a separate monitoring team to be stood up to audit their performance.
The core technical team focused on the OEV auction implementation—the initial, subpar design that was lifted wholesale from Flashbots—and I only managed them.
I was basically checked out at this point.

2023 was a slump for crypto markets, which caused the DAO to grow increasingly apathetic.
Towards the end of the year, I was approached by two trusted DAO members.
Their complaints were mainly:

- The governance scheme with parallel proposal tracks was highly inefficient, failing to operate in unison and wasting funds.
- The lack of data feed usage was a failure in business development, and not having launched OEV auctions yet was not a valid excuse.
- The data feed operation team was using clunky, brittle workflows, which caused concern even though nothing had actually failed.

The offer was to unite all proposals under a single one, get the business development team in shape, and pursue more users without waiting on OEV auctions.
I was asked to actively lead the technical team as I had before to improve data feed operations.
I pushed for a concrete, public target, and we agreed on integrating 20 new chains and having $1B in value protected by our data feeds by the end of 2024, hence the proposal name "1B20N24".

I kicked off an internal project, "Operating data feeds effortlessly."
This included redesigning the node for data feeds, building a static Api3 Market with an automatic user flow (the one at [market.api3.org](https://market.api3.org/) today), and designing standardized integration workflows with multisig tooling that prevented integration speed and security from being at odds.
I hired and trained a data feed operations team from scratch and replaced the underperforming monitoring team.

Seeing that we had the capacity, I also scrapped the previous OEV auction design and had a robust and fully transparent one built.
I had the product reframed as "Oracles that pay you," which sidelined auctions as an implementation detail and focused on the user value.
Despite OEV not being part of the 1B20N24 scope, the on-chain auctions also went live in July 2024, after which I entrusted data feed and OEV operations to the respective team leads and stepped down again.
I had hit every target I set, considered the architecture optimal, and had nothing left to contribute technically if the direction remained data feeds and OEV.

While the technical team did years' worth of work in months, the renewed business development team held up their end of the bargain and then some.
We reached $1B TVS (total value secured) as early as May 2024, up from $10M when the first 1B20N24 proposal was made.

{{< figure src="/2026-04-16-the-self-executing-whitepaper-1b.png" >}}

We had targeted $1B TVS as a credibility signal for prospective users, but there was no revenue case for inflating it further.
So we immediately shifted gears to apply the same blueprint to OEV.
We spent the rest of 2024 iterating on the OEV auction implementation through dogfooding, then aimed for $1M in OEV Rewards in 2025—again, a highly ambitious target.
Our implementation captured available OEV almost perfectly, but adoption was bottlenecked by agency problems within prospective users.
A [technical solution](https://blog.benligiray.com/post/2024-07-15-the-hawk-case-for-api3/) was developed to address what was essentially a sales problem, but was never put to use.
Total OEV Rewards reached a respectable $400K but fell short of the $1M target.

Instead of looking for alternative methods to convert users, the unified proposal team trimmed down for a strategic pivot.
It decided to further expand the vertical integration, curating OEV-boosted lending markets with Api3 data feeds and creating complete DeFi products based on these markets.

<div style="text-align: center"> — </div>

The framing above treats the DAO as an atomic entity, but its actions emerge from the agency of individuals who staked their API3 tokens in the DAO pool.

People like to think of Api3 DAO governance as dominated by a voting bloc composed of the founding team.
It is true that the team was cohesive before there was an API3 token and an Api3 DAO, as the trust-based social contract implied that significantly failing to cooperate would have meant exclusion from the group.
In contrast, once API3 tokens were allocated and members had an independent vote in the DAO, any member could wholly disagree and refuse to contribute without suffering any personal consequence.

I'm not mourning this, as it was an unavoidable aspect of the radically decentralized governance design that we were forced to adopt.
Rather, I'm trying to clarify that all founders and team members were governing no differently from any other API3 token holder, and thus there was no coordinated bloc that could enact unpopular (even if beneficial) policies.
This meant that not only did the public prefer the "better Chainlink with a DAO" mandate over the "API-centric oracles" one, but so did the people who had been allocated tokens and held significant voting power as a result.

The DAO doesn't need a benevolent elite voting bloc in the first place, assuming stakers rationally vote or delegate their voting power to maximize token holder value.
However, due to the directives laid out by the whitepaper, the governance participants are conditioned to act in a way so as to undo any concentration of authority, regardless of demonstrated competence and benevolence.
This is quite irrational, as the core technical team proposal and the subsequent unified proposal carried out countless operations that could not have tolerated any mistakes.
The job of these proposals was to perform open-heart surgery on the project, so withholding governance support never provided meaningful security.
It only enabled other proposal tracks to take the project hostage and burn out its momentum.

Api3 spent years lurching between competing priorities at great expense and with little to show for the effort, then had an unexpected mini golden age starting in September 2023.
One might say, then, "the DAO worked after all."
I would argue the opposite:
1B20N24 was like the Roman Senate begrudgingly yielding to a triumvirate dictatorship.
The contrast between what it delivered in months and what years of friction-heavy governance produced speaks for itself.
However, the DAO is still ultimately in power, and whether it will encourage the unified proposal or anyone else—through voting support and delegations—to pursue greater changes such as revamping the tokenomics remains to be seen.

<div style="text-align: center"> — </div>

Regular startups pivot.
Centralized crypto projects pivot.
A whitepaper and a true DAO create a soft-locked system that makes pivoting nearly impossible.
Would I have done things differently?
No, because the configuration was born out of necessity.
Perhaps I would have had an easier time if I had realized the nature of it all earlier, but I'm proud of the quality of the work and grateful for the lessons it taught me all the same.

The story so far is one where money was abundant, but what the project needed was not up for sale.
There were people who could have put the money to use, but they were not fully trusted to do so.
This pattern recurs in every aspect of our lives, which is also why ["programmable money" fails to produce any useful use cases.](https://blog.benligiray.com/post/2025-01-02-the-case-against-commercial-building-blocks/)
Programmable money needs oracles, oracles need to be trusted (even if based on formal criteria), yet money is a tool invented to enable untrusted parties to do business.
The loop fails to close.

This insight presents a way out of the paradox of the self-executing whitepaper:
If raising funds is not particularly helpful for coordinating talented people toward a shared objective, then the binding concessions required to raise those funds are not necessary in the first place.
What coordinates people more effectively than currency is interpersonal debt, backed by reputation that is rooted in a community.
This enables trust-rich, money-poor organizations to run circles around trust-poor, money-rich ones like DAOs when it comes to creating impact.
