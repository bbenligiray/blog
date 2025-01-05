+++
title = 'The case against "Commercial building blocks"'
date = '2025-01-02'
description = 'January 2025'
summary = "January 2025"
featured_image = '/2025-01-02-the-case-against-commercial-building-blocks-downscaled.jpg'
images = ['/2025-01-02-the-case-against-commercial-building-blocks-downscaled.jpg']
featured_image_caption = 'Ludwig Meidner - Apokalyptische Landschaft - 1913.'
tags = []
+++

["Commercial building blocks"](https://blog.benligiray.com/post/2022-04-17-commercial-building-blocks/) emerged from my work on Airnode, ChainAPI, and Omnimarket.
Airnode and ChainAPI enable API providers to create low-level oracle services, which are to be used by developers to build dApps for end users.
Despite an abundance of potentially useful APIs, the limited pool of dApp developers limits this approach's potential to realize a post-smart contract world.
Omnimarket proposed to fill the gap by converting low-level oracle services into _commercial building blocks_—primitives barely sophisticated enough for end users yet still flexible enough for developers.

When I published the article, Omnimarket was conceived as a prediction market engine, and it later evolved into an assassination market engine.
Despite completing the contract for the latter version and having it audited, I've since changed direction.
This past year, I've solely worked on API3's [data feed](https://blog.benligiray.com/post/2022-31-05-dapis-apis-for-dapps/) and [OEV](https://blog.benligiray.com/post/2022-11-01-oracle-extractable-value-oev/) solutions, driven partly by growing doubts about the best case scenario for commercial building blocks.

My previous article rested on two claims: smart contracts are useless, and useful building blocks could solve this problem.
The first claim remains true—if smart contracts disappeared today, their absence would barely register.
However, the second claim assumes the viability of modularity, a core principle of traditional smart contract design.
Recent developments suggest otherwise, signaling a historic obsoletion of modularity.

<div style="text-align: center"> — </div>

My main criticism of "Commercial building blocks" stems from its reliance on modularity.
This design principle transcends computers—think IKEA furniture you can mix and match, or LEGO bricks that snap together perfectly.
Modular products share two key traits: flexible function and standardized interfaces.
When we build with modules, we can focus on the bigger picture without getting lost in component details, freeing our mental bandwidth for higher-level design challenges.

Naturally, modularity dominates software design today.
While CS students learn to build data structures and algorithms from scratch, real-world developers succeed by knowing which existing components to use.
Their own code must also work as modular building blocks, ready to be used in larger systems.

Deep learning now challenges this design philosophy.
By stacking non-linear functions, deep learning creates highly expressive models that, while being too complex to design by hand, can learn good-enough solutions from data.
Once an underdog in machine learning, deep learning shot to dominance after academics found heuristics to make it vastly outperform the competition.

<div style="text-align: center"> — </div>

How can a single deep model outperform an expert's modular solution? When we design building blocks, we make assumptions that often don't match reality perfectly.
These small mismatches compound into significant limitations.
That's why a unified deep model—one that handles everything previously split across modules—can work better.
As models improve at generalizing (a reliable trend), the scope of their role can be expanded, which reduces engineering complexity and improves overall performance at the same time.

While AI's future lies in end-to-end solutions, we're stuck in old habits for now.
Developers and companies still think modularly, treating AI as just another component—writing code snippets or replacing individual workers.
Yet the simpler path is to strip everything down to just client and model, letting the model's zero-shot capabilities and human-like interface meet our needs.

<div style="text-align: center"> — </div>

This revolution will take a decade to fully spread and will inevitably challenge the current smart contract paradigm.
Looking ahead, we can anticipate several critical changes:
- APIs will become less standardized, making it harder to build deterministic oracle integrations and smart contracts using these.
- EVM (and EVM-killers) will fall behind in this stochastic computation paradigm because they're inherently deterministic.
- The layers of protocols built on and between blockchains will fail to find real use beyond what is already available today.

Smart contracts will likely concede grander ambitions and retreat to their core functions: minting, swapping, and leverage-trading tokens.
While these may seem modest, they represent genuine, battle-tested value.
For API3, the strategic imperative becomes clear: excel at serving these established use cases rather than pursuing solutions to smart contracts' fundamental—and likely intractable—limitations.

<div style="text-align: center"> — </div>

In the [API3 whitepaper](https://raw.githubusercontent.com/api3dao/api3-whitepaper/master/api3-whitepaper.pdf), I examine the fundamental paradox of oracles in blockchain systems.
The concept of an oracle represents a theoretical ideal: a trustless mechanism for delivering off-chain data to smart contracts.
While such an oracle would enable truly trustless and useful smart contracts, this presents a crucial logical gap—the mere utility of a hypothetical solution tells us nothing about its feasibility.
The reality is stark: a perfectly trustless oracle cannot exist.
Given this constraint, I demonstrate that oracle services provided directly by API providers offer the most practical approximation to this theoretical ideal.

This limitation mirrors a deeper problem inherent in smart contracts themselves.
While we can envision theoretical scenarios where self-enforcing contracts would create value, the appeal of such scenarios says nothing about their feasibility.
More importantly, practical solutions to real-world trust problems might not require the deterministic, composable nature of blockchain-based smart contracts at all.
This suggests a fundamental trade-off: we may need to choose between the ideological purity of blockchain-based smart contracts and more pragmatic architectures that enable useful applications in practice.
