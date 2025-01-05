+++
title = 'The Hawk Case for API3'
date = '2024-07-15'
description = 'July 2024'
summary = "July 2024"
featured_image = '/2024-07-15-the-hawk-case-for-api3-expanded.jpg'
images = ['/2024-07-15-the-hawk-case-for-api3-expanded.jpg']
featured_image_caption = 'Wang Cheng, A dangerous locking of eyes, 2020.'
tags = ['API3']
+++

The defining challenge of building oracles is to juggle the wants of vaguely interested sides well enough to get them all to participate in a use case.
On top of that, one has to do this better than all the other suitors.
As a result, we see oracle projects converging to the same plan:

1. Spend funds to get partnerships
1. Use partnerships to shill the token
1. Dump the overvalued token

Needless to say, this is a prolonged exit scam.
And a bad one at that, because it predicts no adversaries.
As soon as multiple oracle projects start doing the same, the whole thing turns into a race to the bottom.
Having built up a warchest of funds doesn’t really help here, as the competition is an unlimited number of latecomer projects that throw around IOUs for tokens that aren’t in circulation or don’t even exist yet.

<div style="text-align: center"> — </div>

You may think that I will say "[OEV](https://blog.benligiray.com/post/2022-11-01-oracle-extractable-value-oev/) solves this", but that’s not the case.
Yes, it enables API3 to have a viable business model, but this doesn’t stop other oracle projects from recycling the old plan with a twist:

1. Spend funds to washtrade OEV
1. Use OEV volume to shill the token
1. Dump the overvalued token

Here, _OEV washtrading_ refers to OEV extraction activity that has no net positive effect on the oracle project tokenomics.
What makes OEV washtrading viable is that profitability is easy to fake when the oracle project governance is centralized and the balance sheet is private.
If the general public doesn’t know that you’re spending $200 to create $100 of OEV revenue, you can sell them on the idea that your oracle project is hugely profitable and they should buy the token.

So what can we do in a situation where moats don’t exist and all relevant sides will eventually be ground down to zero?
My answer is the same since [our whitepaper](https://github.com/api3dao/api3-whitepaper/blob/master/api3-whitepaper.pdf).
Moats can be built, but they require relinquishing the middleman status of the oracle project.
Since this is a hard pill to swallow, oracle projects prefer to bet on that no one else will manage to build moats either.
A good example of this is how [our first-party oracle narrative](https://medium.com/api3/the-race-to-first-party-oracles-87fab596e906) has been received.
Chainlink doubled down on third-party oracles, while Pyth decided to claim their third-party node operators to be first-party.
Both of these responses are favorable, as they indicate that we can run the race to disintermediation alone—finishing it will be enough to win.

<div style="text-align: center"> — </div>

Let’s dig deeper into strategic parties in the context of OEV.
Who are they?
The easiest way to tell them apart is their ability to bring the roof down simply by walking away.
Let’s start with an easy one:
Can a validator of a decentralized network do that?
No, because by definition, their lack of participation wouldn’t have a noticeable effect.
What about the chain team, or a centralized sequencer?
Nowadays, it’s largely understood that chains have to behave identically to take advantage of the ever-growing benefits of existing ecosystems.
Any novel features have to be behaviorally transparent or optional.
As a side effect, any attempt to disrupt OEV extraction activity on a chain would face a significant challenge: strategic parties could migrate seamlessly to an equivalent chain.

The OEV auction platform must be open to everyone in a permissionless way to maximize (non-washtraded) OEV extraction.
A side effect of this is that searchers remain pseudonymous.
This allows them to follow the strategic parties wherever they go, unfettered by any attempt to stop them (an oracle project trying to lock searchers down with exclusivity contracts comes to mind).
Therefore, a profitable searcher is not a strategic party (and an unprofitable searcher is a washtrader, and thus is of no concern to us).

First-party oracles still have as much unrealized potential (for bringing the roof down) as the day the term was coined for our whitepaper.
On the flip side, oracle projects enlist third-party oracles in the hundreds specifically to obscure their total reliance on API providers.
Under these circumstances, an oracle is a strategic party to the degree that they’re willing and able to exercise their rights of first-partyness.

Finally, there is the most elusive of them all, the dApps.
We have already [announced](https://blog.benligiray.com/post/2022-11-01-oracle-extractable-value-oev/) that we will kick back the OEV auction proceeds to the dApps.
This is not only because it’s the right thing to do, but also because the dApps are the party with the most strategic position.
After all, a dApp stops using API3, and the respective OEV proceeds go to zero.
It is then implied that we should specifically think about who can make or break the API3 integration.
Can an individual user of the dApp affect if the dApp uses API3?
Maybe—if they provide enough liquidity.
What about the community?
Again, maybe, if they’re convincing enough.
Same issue with the team, maybe they are a democratic collective, or maybe they are puppeteered by a VC.
Ultimately, our entire business development effort can be boiled down to this: accurately modeling the strategic decision-making mechanism of the dApp and working that.

<div style="text-align: center"> — </div>

In conclusion, this is a proposal to systematically focus on the strategic parties to build and enforce a moat.
This needs to be done with such transparency that it can scale up to the magnitude of [our TVS](https://defillama.com/oracles/API3) while keeping API3 tokenomics crystal clear.
Furthermore, the method needs to be of laser precision to enable us to overpower oracle projects that are willing to burn their treasuries in competition, all the while yielding a significant tokenomic benefit to API3.

We’re at a point where API3 has all kinds of good things going for it with its TVS increasing at an unprecedented rate and OEV being launched with every other oracle project scrambling to imitate.
However, we’re eventually bound for the same downward spiral as the other oracle projects if we follow their footsteps.
Therefore, at a time that elicits our timidness, I advise ferocity to be the direction of API3.
