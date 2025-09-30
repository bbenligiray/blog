+++
title = 'API3 Core Technical Team Reports, December 2020–August 2023'
date = '2023-08-31'
description = 'December 2020–August 2023'
summary = "December 2020–August 2023"
featured_image = '/2023-08-31-api3-core-technical-team-reports.jpg'
images = ['/2023-08-31-api3-core-technical-team-reports.jpg']
tags = ['Api3']
+++

# API3 DAO Development Update, Operations Cycle #1

This post accounts for the technical development activities during the first operations cycle from December 17th, 2020 to January 31st, 2021.

## Airnode

This was an extremely exciting cycle for us, as we deployed a fully-functional Airnode on the cloud. If you want to find out what that is like, you can test it on a number of chains with our [starter project](https://github.com/api3dao/airnode-starter). We have also made integrations with a number of smart contract platforms, and even published a guide to “self-integrate”, as the demand is difficult to keep up with.

{{< figure src="/2023-08-31-api3-core-technical-team-reports-airnode-deployer.png" >}}

In addition to complete unit test coverage, an end-to-end test suite was implemented in this cycle and populated with fundamental test scenarios. The work on various API integration tooling (validator, OAS to OIS converter, etc.) is ongoing. We’ve also been exploring and analyzing various gas price strategies, and how they work with the unique way the Airnode fulfills requests.

## Authoritative DAO

We had provided dOrg with a [prototype of the pool contract](https://github.com/api3dao/api3-contracts/tree/master/packages/api3-pool) with significant scaling and UX issues that were going to be ironed out according to the [specs delivered at the end of undertaking #1.](https://github.com/api3dao/api3-governance/blob/main/monoliths/authoritative-api3-dao/undertaking-1/API3%20Specification%20%26%20Roadmap%20FINAL.pdf) We have determined that it was suspect that this was going to be achieved in a timely manner due to the pace of undertaking #2. Furthermore, the resulting ambiguity in the user flow was blocking the finalization of the frontend design, and consequently its development.

As a solution, we deployed significant development and design resources from our core team to refine the specs in a way that satisfies the business needs, is easy to implement, and gas-cheap and easy to use for the user. Although this distracted the core team, it was worth it because the project is back on track and is expected to follow a timeline comparable to the original.

{{< figure src="/2023-08-31-api3-core-technical-team-reports-dao-dashboard-1.png" caption="A DAO dashboard mock up. We are targeting an MVP in terms of the dashboard to ensure that the monolith is not being encumbered by redundant features." >}}

To prepare for the undertaking #3, we are in discussions with a number of companies for the security audit of the DAO contracts. Here, our goal will be to find options that deliver high quality audits that will be able to accomodate our timeline.

## ChainAPI

We have announced that we will start working on [ChainAPI](https://medium.com/api3/hello-chainapi-e1b386a74f1d) this cycle, and it’s probably apt to give an update. We’re pleased to say that the development has quickly hit its stride, and we are working on the integration platform undertaking, while laying the groundwork for the following undertakings as well.

## Scaling the team

We have made a total of 5 technical hires this cycle that will work on API3 business full-time. As the technical team, we are faced with two options: We either keep building full speed ahead, or we work on scaling up for a greater long term potential. The inherent potential of the project, as well as the interest from the public and potential users have directed us towards the latter. Therefore, recruitment was one of the major things that we have worked on in this cycle, and it looks like this will continue for a while.

In addition to looking for employees, we have started mobilizing some of the founding teams ([ChainAPI](https://chainapi.com/), [Curve Labs](https://www.curvelabs.eu/), [Curvegrid](https://www.curvegrid.com/)) to contribute to various development and integration efforts, and we expect these contributions to pick up speed in the following months. We are also exploring outsourcing opportunities; [dOrg](https://dorg.tech/) is already working on the [authoritative DAO](https://medium.com/api3/announcing-monolith-1-authoritative-api3-dao-ec9ca6d044f8) implementation, and we have recently started working with [LimeChain](https://limechain.tech/) on the protocol contracts.

As a note, we have a lot of technical community members on [our Discord](https://discord.gg/api3dao), enthusiastic to learn and contribute. Unfortunately, reaching out to each of you personally is not possible at this stage, but we are working on a model that will harness this potential. In the meantime, please be patient with us, read the docs, and tinker with the example projects. If you don’t feel like being patient, find a few like-minded peers and come up with a project!

## Conclusion

What we have cared about the most in this cycle was to keep the authoritative DAO undertaking moving along, and we have succeeded at this. While doing so, we were able to make significant progress with Airnode, make a decent number of hires, and kick off multiple projects with internal and external teams. These efforts are greatly increasing our momentum, and will have spillover effects in the following cycles.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports.jpg" >}}

# API3 DAO Development Update, February 2021

We were initially planning to publish a development update per-[operations cycle](https://medium.com/api3/api3-operations-a35c93a3a9d) (see the one for the first cycle [here](#api3-dao-development-update-operations-cycle-1)). However, we already have a lot of material built up, so a monthly schedule will serve us better at this point. Without further ado, let’s begin!

## Airnode

We are planning to apply some finishing touches to Airnode and its protocol before releasing our first stable version, v0.1.0 (this would be the Airnode-alpha monolith on our roadmap). However, the existing version is feature-complete and is quite robust (based on internal and external usage on a variety of chains). Because of this, we decided to freeze this version under the name [pre-alpha](https://github.com/api3dao/airnode/tree/pre-alpha), and are currently using it to prototype API, dApp, and smart contract platform integrations. If you want to use Airnode before the release, make sure that you’re using the pre-alpha version. The changes between pre-alpha and v0.1.0 will be functionally minor, which means that the transition will be easy.

We strongly [advocate](https://medium.com/api3/airnode-the-api-gateway-for-blockchains-8b07ff136840) for serverless hosting as the ideal solution for oracle nodes due to a variety of reasons such as failure resistance, easy redundancy, on-demand pricing, etc. Of course, the ideal workflow is to implement the integration while running your Airnode locally, then deploy it using the deployer once you are happy with the results. While this was available from the start, it was buried in an [obscure README.md file](https://github.com/api3dao/airnode/tree/pre-alpha/packages/node#invoking) in the monorepo. We have now [containerized](https://github.com/api3dao/airnode/blob/pre-alpha/Docker-client.md) the node too (the previous container was the deployer), which people can easily use to run an Airnode locally and read the node logs on their terminal. Although this is intended for development and debugging, we will be maintaining this container to be usable in production for hosting on premise or cloud providers that the Airnode deployer will not support (for example Digital Ocean, which doesn’t provide native serverless functionality). Since this configuration will share the same stateless architecture, we are expecting it to be similarly robust.

{{< figure src="/2023-08-31-api3-core-technical-team-reports-airnode-client.png" caption="I quickly spun up a clone of the airnode-starter node running locally on my machine for a screenshot. Note that this and the serverless deployment will work in tandem without stepping on each other’s toes, which shows how easy it is to add redundancy to Airnode across different hosting solutions." >}}

During this month, we have worked with LimeChain to have the pre-alpha version of the request–response protocol contracts audited. We are pleased to announce that it was confirmed that the contracts did not include any vulnerabilities. We will continue using this version for our early integrations, while scheduling a more comprehensive audit for v0.1.0. This was also planned to be the first step of further cooperation with LimeChain on building solutions based on the Airnode protocol contracts, which you will hear more about in the future.

Airnode has a novel way of broadcasting fulfillment transactions that is very responsive to the status of the current gas price market. Furthermore, the requester covering the gas costs and the requests being fulfilled by requester-specific node wallets present some unique solutions to the cost–performance tradeoff problem that is common with oracles. This month, we have done statistical analysis, live testing, and further statistical analysis based on the results of the tests to come up with a final gas price strategy that can be optimized for the specific use-case.

## Authoritative DAO

We’re happy to say that we’re on the final stretch with the authoritative DAO. The first audit is scheduled with Solidified for March 8–22. Following the revisions, a second audit is scheduled with Quantstamp for April 4–9. dOrg will be finalizing the dashboard implementation in the meantime, and barring an unforeseeable event, we are planning for the authoritative DAO to be live before April is out. Note that this is also when staking will go live, and we will be publishing posts, going over the tokenomic design and the related design decisions ramping up to that.

At the design side, the DAO dashboard UX design has been finalized (some mechanics were previously ambiguous). In the meantime, we have had the graphic design polished, and are hoping to have this version implemented before we go live.

{{< figure src="/2023-08-31-api3-core-technical-team-reports-dao-dashboard-2.png" caption="The revised graphic design of the dashboard." >}}

## Documentation

We are not only building a node for first-party oracles with Airnode, but also the protocol to integrate Web APIs to smart contract platforms. Since we are planning Airnode to become a very fundamental building block for smart contract use-cases that require secure, middleman-free data (which is quite a large audience), high quality documentation will be critical.

We have some special requirements:

- API3 interacts with a number of stakeholders (API providers, dApps, developers, DAO members, smart contract platforms, etc.) and the documentation requires a specialized facet for each of them.

- Our protocol has detailed specification formats both for integrating APIs and configuring Airnode. Since not all users will be on the same version, we need good versioning support at the documentation-side.

- Since API3 is a decentrally governed, open source project, we need the documentation tooling to fit that. This requires qualities such as easy local development, traditional git workflow and not depending on proprietary/paid services and frameworks.

After some shopping around and prototyping, we have decided that VuePress satisfies our needs after some customization. We are currently migrating the existing docs to the new format, here’s a sneak peek.

{{< figure src="/2023-08-31-api3-core-technical-team-reports-docs.png" >}}

## Conclusion

Actually, a lot more is going on, yet these developments are not at a stage where they can be showcased (especially visually), so we would rather not spoil them. One final thing: We have updated our open positions page on the website. Please take a look and make sure to share it within your network. See you in the next post!

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-march-2021.jpeg" caption="Andrea Marcias, Pyramid Altar." >}}

# API3 DAO Development Report, March 2021

To summarize last month’s development report, you currently can use the pre-alpha version of Airnode to integrate an API to a smart contract (see the related monorepo branch and docs).

This version of Airnode can be operated as:

- An AWS serverless function
- A Docker container (on cloud or locally)

The pre-alpha contracts have been audited by a third party, and this version is being used to prototype integrations. We are working on a v0.1.0, which functionally will be exactly the same, yet have a stable (read: unchanging) protocol and UX flow based on the feedback from the pre-alpha.

## Roadmap

In the most recent community call, there was a question about whether the roadmap is flexible. If you have referred to the roadmap more than a few times, you probably have noticed that [monoliths and undertakings](https://medium.com/api3/api3-builder-terminology-dd398fe447c3) move around. This reflects the fluidity of the roadmap, which is why we prefer to use a board instead of a static image or webpage. Such changes tend to be based on new data, and what we have found out is that not only first-party oracle-based dAPIs, but also stand-alone first-party oracles are very much in demand (and more importantly, in a way that cannot be substituted by third-party oracles in any feasible way).

In this paradigm, quantifiable security through insurance is the focus, and dAPIs are a tool to be used to maximize the amount of insurance that can be provided, which is redundant for a lot of untapped use cases. In other words, the dAPI concept is a tool to be able to provide a specific (even niche) level of security, and not the goal. Being able to purchase first-party oracle access and insurance is what creates the demand for the API3 token, so focusing on this aspect (instead of dAPIs specifically) will align the direction of the project with its tokenomics more directly and at a wider scale. In short, the roadmap is indeed fluid, and is coupled with the strategic direction at an abstract level.

## Authorizers

Let’s start with a related topic: The specifications for the authorizer contracts are established, followed by their [implementation](https://github.com/api3dao/airnode/tree/c95fe2db412052f5f244ea890605dbb616faec4f/packages/protocol/contracts/authorizers). To briefly explain what an authorizer contract is, it’s used to extend the Airnode request–response protocol to allow an Airnode operator (i.e., API provider) to manage access to their first-party oracle based on a customized policy.

We strive to design a flexible framework that will cover all potential use-cases, as we want to build the standard to integrate APIs to smart contracts. On the other hand, we’re not a fan of under-defining solutions under the guise of “giving the user freedom”, because that is often used as an excuse to dodge the more difficult problems (how do you decentralize oracle governance, how do you quantify security, how do you specify integrations, etc.). The solution is to implement the customizable authorization framework mentioned above, but also provide the user with ready-made authorizer contracts.

Authorization is about managing access, and access management is the primary tool for monetizing a service. This is why establishing specs for these ready-made authorizer contracts is difficult; it’s not a purely technical matter — nothing about oracles ever is — and requires strong assumptions about monetization both for API providers and the API3 DAO. Furthermore, one needs to consider the UX implications; if you need oracle node operators to reconfigure their node or make a transaction each time a new use-case will use their services, your solution will not scale.

Considering all these factors, we came up with two authorizer contracts: Api3Authorizer.sol allows one’s Airnode to be accessible with the usage of API3 tokens without requiring any API provider interaction (more details about this will be announced later on). This is the primary authorizer contract that will be utilized by the API3 partners the majority of the time. SelfAuthorizer.sol allows the API provider to whitelist users themselves based on any criteria they want, and [ChainAPI](https://medium.com/api3/hello-chainapi-e1b386a74f1d) (with its requester interface undertaking) will include an interface (essentially, a dApp) that will allow the API provider to do this (note that this will simply be an interface, the API provider can also do this by interacting with the authorizer contract directly). An Airnode operator is free to use a combination of these authorizers plus ones that they may have implemented to enforce more complex authorization policies that these ready-made contracts may not support.

## Airnode developments

- Work on dAPI contracts has started. The initial goal is to have a typical aggregating contract that will be integrated with the request–response protocol, with more novel features to be delivered in the future.

- The new deployment file specs and flow for v0.1.0 is established and are currently being implemented. This will support configurations that utilize [multiple simultaneous deployments across cloud providers](https://en.wikipedia.org/wiki/Multicloud) as first-class citizens, which will result in unmatchable resiliency.

- The OIS validator package is updated according to these new specs, and [will go into use with v0.1.0](https://github.com/api3dao/airnode/issues/136).

## Docs

We have moved [our docs](https://docs.api3.org/) to the [api3.org](https://api3.org/) navigation bar because it has reached a stable point. It has a lot of customized components such as a version selector (that only lists pre-alpha at the moment) and an extra table of contents on the right that makes navigation easy. The docs starting from v0.1.0 will be divided into sections according to roles. At the moment, a documentation page targeted at the API3 DAO members (hopefully you!) is being worked on.

## Authoritative DAO & Staking

In the last month’s report, we had left off where we were preparing for the first DAO audit on March 8th. I’m happy to say that we’ve received an approving report on March 22nd. The suggestions are largely addressed at the moment (with the addition of some significant gas cost optimization) and we’re doing our final tweaks before sending it off for the final stamp of approval. This will probably coincide with the start of our second audit on April 4th mentioned in the last month’s report.

The beginning of the first audit also marks [Curve Labs](https://www.curvelabs.eu/), one of the API3 founding teams, starting to play a much more active role in our DAO development. You can see their first proposal here, which covers the phases starting from the audit to the launch of the authoritative DAO. What is exciting about this development is that as mentioned in their proposal, they are planning to take ownership of the long-term development of the authoritative DAO and its extensions, which was something that was very much needed.

<div style="text-align: center"> — </div>

I’ll end this with some very significant news that may have gone under your radar. AWS has [announced](https://aws.amazon.com/about-aws/whats-new/2021/03/announcing-general-availability-of-ethereum-on-amazon-managed-blockchain/) that they now provide managed Ethereum nodes for public chains through Amazon Managed Blockchain. We knew that this was in the works as early as last Summer based on our communications and were designing the Airnode architecture accordingly, but it being delivered this early accelerated the timeline for API3. The implications are two-fold:

- On the practical side, a managed Ethereum node is the perfect complement to Airnode, the managed oracle node. As an alternative to using centralized service providers like Infura and decentralized service providers like [Pocket Network](https://medium.com/api3/announcing-the-api3-partnership-and-token-swap-with-pocket-network-f45420790b6c), this will allow an API provider to run their own Ethereum node with no effort. Since Airnode is already run on the cloud as a serverless function for maximum availability, operating the Ethereum node on the same platform doesn’t degrade security (and is even preferable).

- More importantly, public blockchains are starting to become a part of the cloud stack in the form of managed services, and we can expect this to be followed by integrations with more chains and cloud providers. This is bad news for the middleman node operator and solutions that depend on it as their moat, yet is perfectly in line with our vision for Airnode as the [API gateway for blockchains](https://medium.com/api3/airnode-the-api-gateway-for-blockchains-8b07ff136840), and positions API3 as the provider of this piece of technology.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-april-2021.jpeg" >}}

# API3 DAO Development Report, April 2021

This is the final development report for [cycle #2](https://github.com/api3dao/api3-governance/blob/main/teams/core-technical/cycle-2/core-technical-cycle-2-proposal.pdf), following the [February](#api3-dao-development-update-february-2021) and [March](#api3-dao-development-report-march-2021) reports. See the [DAO & Staking Part I](https://medium.com/api3/significance-of-the-dao-and-staking-b8feeaf93804) post for the state of the development on that front. I’ll be keeping this report brief and factual and focus on the rest of the DAO & Staking posts as there is a lot of material that needs to be covered.

## Airnode

In the March report, I had mentioned that the new Airnode deployment file specs and flow had been established that will support multiple simultaneous deployments across different cloud providers and regions. This month, the deployer package is updated to implement these. In addition, the RRP admin CLI is updated and a lot of additional minor updates were made towards the v0.1.0 release. (A note about the “v0.1.0 when” questions, pre-alpha is doing the job well for prototyping and there is no particular reason to rush the release.)

It has always been the plan for the Airnode deployer to be migrated to use bare Terraform (instead of Serverless Framework), as that would provide the optimal flexibility regarding using additional cloud infrastructure (VPCs, managed Ethereum nodes, etc.) and different cloud providers, yet it was approached as more of a long term plan. This month, we had additions to the team that could make that a reality much sooner. Therefore, this is now on the menu for v0.1.0.

## Authoritative DAO

The Aragon framework uses [MiniMe](https://blog.giveth.io/the-minime-token-open-sourced-by-giveth-2710c0210787) to implement governance tokens by default. The authoritative DAO was implemented with a similar approach. In [one of the audit reports](https://x.com/SolidifiedHQ/status/1387484187993600002), it was (rightly) suggested that this should be replaced because its access methods (based on [binary search](https://en.wikipedia.org/wiki/Binary_search)) require a variable amount of gas, which may end up being a problem. As a solution, we replaced all instances of these access methods with workarounds with deterministic bounds for gas costs, both defusing the risk and optimizing the gas costs.

Unrelated to the audits, we updated the DAO structure so that there are two levels of quorum that need to be reached to enact different types of proposals. This will allow us to better secure critical functionality such as API3 token minting rights management (by having it require a higher quorum threshold than day-to-day proposals), and will be explained in detail in one of the upcoming DAO & Staking posts. The DAO contracts are still undergoing audits at the moment.

## Open Bank Project

The big news of this month was the [announcement](https://medium.com/api3/api3-and-open-bank-project-initiate-a-10-year-development-partnership-to-bridge-open-banking-with-299b9f1384a3) of our long term development partnership with the Open Bank Project. As implied by the lifetime of the partnership, there is a long road ahead to solve the API connectivity problem for the banks, and there is no better reason to start working on it right away. This month, a combination of the core technical team and the integration people of the API BD team started familiarizing ourselves with the OBP solutions. In addition, we started having joint calls with OBP for exploration and to plan the following development steps.

## dAPIs

This month, we have conceptualized the RRP-based dAPI architecture, which ended up elegantly mirroring the Airnode RRP architecture (i.e., calling a dAPI or a single Airnode looks and feels rather similar to the user). Alternative reduction methods have been implemented in a very scalable way, both complexity and gas cost-wise. We are currently implementing a dAPI server contract that will use these [reduction](https://en.wikipedia.org/wiki/Reduction_operator) methods to create and serve dAPIs in a permissionless way.

Keep tuned-in for the DAO & Staking series posts as they will dive into the implementation details, which you should definitely be aware of if you are intending to stake and participate in governance.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-may-2021.jpeg" >}}

# API3 DAO Core Technical Team Development Report, May 2021

We’re at the end of the first month of our [third cycle](https://github.com/api3dao/api3-governance/blob/main/teams/core-technical/cycle-3/core-technical-cycle-3-proposal.pdf). This month has been a particularly productive one regarding DAO development, which has also interrupted the DAO & Staking series ([1](https://medium.com/api3/significance-of-the-dao-and-staking-b8feeaf93804), [2](https://medium.com/api3/lessons-from-daov1-da106f2f1fd9), [3](https://medium.com/api3/fractal-scaling-of-api3-b3ba78c9dcb7)). Although I’m planning to finish the series to serve as a definitive reference for the motivation of the authoritative DAO implementation details, this may end up happening after the authoritative DAO launch.

In the [previous month’s report](#api3-dao-development-report-april-2021), I had mentioned that replacing the Serverless Framework dependency at the Airnode deployer in favor of Terraform could have been feasible. This will allow us to port Airnode to other cloud providers and extend it with additional cloud infrastructure (or provide it as [a module to be added to existing infrastructure](https://medium.com/api3/airnode-the-api-gateway-for-blockchains-8b07ff136840)) a lot more easily. I’m glad to say that this is already achieved this month, which is quite a significant improvement.

The work on dAPI contracts mentioned in the previous month’s report was continued. Considering that dAPIs are a fairly isolated vertical in terms of implementation and operation, a dAPI team separate from the core technical team is being considered. Including having a separate DAO development team and the integration work being undertaken by the business development team members, this allows the core technical team to focus more of its efforts on Airnode, which should improve our efficiency.

The core technical team had to be very involved with DAO development this month, and I’m planning to post a report about the entire development process once we’re done. We had been conducting an additional audit with Team Omega (an auditing team composed of senior DAOstack developers) while waiting on the initial Quantstamp report, which allowed us to use this time efficiently. The audits from Solidified, Quantstamp and Team Omega ended up providing a broad coverage from different perspectives, and will result in a much more secure product.

We received the initial audit report from Quantstamp on May 21st, and the revisions were sent back on May 30th. While waiting for the final report Quantstamp, we will be preparing the revisions for the Team Omega audit. In parallel to this, we are finishing up on the implementation of the front-end and applying the audit-related updates. Overall, strong core technical team engagement resulted in the DAO development speed picking up significantly. This came at the price of slowing down the development of the core solutions, yet this is only temporary and the authoritative DAO is deemed important enough to warrant this.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-june-2021.jpeg" >}}

# API3 DAO Core Technical Team Development Report, June 2021

In the [previous month’s report](#api3-dao-core-technical-team-development-report-may-2021), it was mentioned that we were awaiting the final audit reports for the DAO contracts. We’re happy to announce that all three [audits](https://github.com/api3dao/api3-dao/tree/main/reports) from Solidified, Quantstamp and Team Omega are now finalized. This ended up being a usefully diverse combination, where Solidified gave an initial vote of confidence, Quantstamp provided a broad coverage, and Team Omega was much more DAO/governance-focused and went even beyond the scope of a regular security audit

We have achieved a feature-complete version of the DAO dashboard this month, which supports three main user flows:

- The user doesn’t have time to keep up to date with governance or they don’t want to vote actively. Then, the user stakes and delegates their voting power, and continually receives staking rewards without additional interaction.
- In addition to staking and receiving rewards, the user actively participates in governance by voting on proposals.
- The user is a contributor to the project and makes DAO proposals, for example to fund their efforts.

The DAO dashboard is hosted on IPFS and interacts with the DAO contracts directly, without depending on any intermediary services (in contrast to dApps depending heavily on caching solutions for a more Web 2.0-like user experience). This makes it fully decentralized and operationally robust. The resulting DAO is a very suitable template for subDAOs, as it will be able to scale in numbers easily due to not having to be maintained in any way (perhaps other than making sure that the dashboard is kept pinned on IPFS, which can trivially done in a completely trustless way through a variety of services).

The completion of the dashboard was followed by a closed test and user interviews with subjects chosen from the community. After applying updates based on this feedback, we started a public test on the Rinkeby testnet on June 28, which you can participate in right now. See the #public-dao-test channel on our [Discord](https://discord.gg/api3dao) for more information. We are currently focused on investigating any issues faced by the users and applying updates to improve the UX.

It has been a hectic last two months where a group composed of core technical team and ChainAPI developers took over the authoritative DAO development and worked very hard to deliver a high quality product, so I believe a credit roll is appropriate here. Emanuel and Andre worked on the frontend, Michal did our styling, Tamara designed the wireframes and Leandro did our graphical design. I should also include Ashar and Santiago for their contributions by testing, reviewing and documenting the contracts. They all did a fantastic job and I thank them here on behalf of the community. If you want to learn more about the development process of the DAO, and specifically why it ended up being finished later than expected, you can read my recent post here.

Of course, the rest of the team was making progress on their own endeavors in the meantime. Our docs are being built up constantly, we are supporting the BD team with technical help in Sovrynthon, working on a new contract that will have the API3 token gain a new utility that is not mentioned in the whitepaper and the ChainAPI development is continuing, steady as ever. However, the spotlight should definitely be on the public DAO test, and we’ll be back with a more oracle-focused development report next month!

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-july-2021.jpeg" caption="Bruno Liljefors, Havsörnar jagande en ejder, 1924." >}}

# API3 Core Technical Team Report, July 2021

In the [June report](#api3-dao-core-technical-team-development-report-june-2021), we have announced that the public DAO test started on June 28. After a fast-paced and fruitful test process (which we again thank the participants for), we announced the [mainnet launch](https://medium.com/api3/api3-authoritative-dao-staking-live-on-mainnet-4732d1e538cb), which was executed successfully on July 15. This has been the most financially ambitious achievement of the project, and surpassed the [public token distribution](https://medium.com/api3/the-api3-public-token-distribution-event-has-ended-644e984f50fc) in its scale. This is the second project-scale milestone that the core technical team has achieved after the delivery of the pre-alpha version of Airnode, and we see it to be our mission to deliver similarly long-running and mission-critical projects.

To give some context for governance purposes, I’ve published [an article](https://bbenligiray.medium.com/story-of-the-authoritative-dao-1153990a3eff), recounting the unanticipated development process of the authoritative DAO. The relevance of that to this report is that the [core technical team was only responsible for “overseeing and supporting” the development of the DAO contracts and dashboard](https://github.com/api3dao/api3-governance/blob/main/teams/core-technical/cycle-3/core-technical-cycle-3-proposal.pdf), yet we stepped up to undertake the entire development and operational tasks when it ended up becoming a necessity. To finalize the project in a timely manner, we had to deploy a total of five senior developers (three full-time, two part-time) and two designers from the core technical team and the ChainAPI team (distributed approximately 50–50 between the two teams).

This has two implications:
- The core technical team is willing to get the DAO out of trouble at the cost of diverging from its own plans. Furthermore, it’s quite successful at this. (Good intentions by themselves do more harm than good, taking over the project only to fail would have been disastrous.)
- The only reason we succeeded at this was that we had a number of senior developers across the core technical team and the ChainAPI team that could easily adapt to a project that they weren’t selected for in the first place, and we had the authority to make this call (i.e., “We will stop what we’re doing and will now take over this task that someone else was supposed to do.”)

Performing well when everyone else is doing their jobs perfectly is not a feat, it’s the bare minimum. Through this affair, the core technical team has proven that it can be trusted with turning funds into a general kind of problem solving capacity, which allows it to turn unexpected problems into wins.

<div style="text-align: center"> — </div>

It has been more than a year since we started working on [Airnode](https://medium.com/api3/airnode-the-api-gateway-for-blockchains-8b07ff136840), which is what makes the value proposition of API3 feasible. That’s because if you propose first-party oracles as a solution to the ecosystem building problem around oracles, you first need to answer [the question of why we don’t already have first-party oracles and how that will be possible going forwards](https://medium.com/api3/where-are-the-first-party-oracles-5078cebaf17). We released the pre-alpha version of Airnode towards the end of 2020, aiming to test it in real world conditions and iterate on it so that we have a much stronger foundation to build on. During this time, we received a lot of confirmation that it makes a lot of sense to the stakeholders by design and performs very reliably, but we also discovered some friction points that seem to consistently cause UX and business problems. In a similar way, some of the nice-to-haves that we have implemented at the cost of increasing complexity turned out to be not necessary at all.

During this month, it became clear that there is immediate demand for a future-proof (read: that won’t get breaking updates) and production-ready Airnode with all the new features that we have implemented since the release of the pre-alpha version to address the issues mentioned above. As a result, we started working on Airnode Beta (a working title) this month. We have greatly revised the protocol to simplify the UX and extended it to implement the monetization features that were omitted in the pre-alpha version. Following its audit and the implementation of these changes at the node-end, we’re planning to start using this internally with our partners and release it for the public to use to integrate APIs to smart contracts.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-august-2021.jpeg" caption="Şahkulu, “saz”-style illuminated manuscript, mid-16th century." >}}

# API3 Core Technical Team Report, August 2021

We [launched the DAO](https://medium.com/api3/api3-authoritative-dao-staking-live-on-mainnet-4732d1e538cb) in July, and have been maintaining it since:

- Fixed a frontend regression that broke the radio buttons
- Redirected [dao.api3.org](https://dao.api3.org/) to the DAO dashboard through an IPFS gateway as an alternative to [api3.eth.limo](https://api3.eth.limo) because it is not reliable due to the [distributed DNS infrastructure](https://blog.cloudflare.com/cloudflare-distributed-web-resolver/) it relies on (api3.eth.limo is still the recommended URL)
- Fixed a number of issues, most notably one that caused unstable WalletConnect experience

The [operations](https://medium.com/api3/api3-operations-a35c93a3a9d) proposals went by smoothly, with no technical issues. Furthermore, the feedback on the staking flow is overwhelmingly positive (apart from the connectivity issues addressed above), which validates the design and implementation. Currently, we have a list of nice-to-have features that we want to implement, yet they do not hold top priority on our to do list.

<div style="text-align: center"> — </div>

7 weeks after the DAO launch, [the DAO has met the staking target](https://x.com/API3DAO/status/1430570181374402564) of 50% of the total supply. Currently, the staking reward started decreasing slowly, while the staked amount still sits slightly above the target. The main caveat with such dynamic systems is that if they are not initialized well, it will take very long for them to stabilize. The current behavior indicates that the initial values for the staking reward parameters were estimated well, and it should be smooth sailing around the staking target going forwards.

The fact that the staked amount is increasing slowly despite the reward decreasing slowly can be attributed to the estimated smart contract risk decreasing more significantly, and accordingly, more people finding staking API3 to be a good deal. In a similar vein, DAOv1 started migrating her funds to the authoritative DAO. At the moment, the primary treasury holds 10 million API3, while the secondary treasury holds more than 3 million USDC (a proposal requires 50% quorum to use the funds from the primary treasury, and 15% quorum to use the funds from the secondary treasury). In the absence of incidents, the gradual migration will continue.

<div style="text-align: center"> — </div>

The DAO dashboard is very minimalist in what it does to provide the following:

- A very simple user experience, as it is meant for all token holders
- Being able to run it on fully decentralized infrastructure that can survive abandonment (in a DAO context, the [bus factor](https://en.wikipedia.org/wiki/Bus_factor) also applies at the team scale)
- Being able to run it on chains other than Ethereum mainnet (where certain dependencies in the form of decentralized protocols may not exist)

However, we were quickly let known that this wasn’t going to satisfy our power users. As we were planning to enrich the dashboard with a few additional features, Enormous posted the DAO Tracker on the forum. I recommend you to click around if you haven’t already, but in summary, it’s very good and makes any work by us towards the same end redundant.

The DAO Tracker contributes to API3 in a couple ways. We recently got two additional technical teams, yet this is one other that popped up in a permissionless way and managed to make a significant contribution without any coordination with the existing teams. This demonstrates that the scope of API3 is large enough that one can imagine an ecosystem of independent actors working on it and pushing it forwards. Another point is that the DAO Tracker is potentially a critical component of API3 governance, like the Telegram group, Discord, Twitter handle, DAO dashboard, representation at community calls, conferences and interviews, etc. It’s healthy for such channels to not be consolidated at the hands of a single team, and this was one of the reasons why we didn’t want the DAO dashboard to be a web application with a traditional backend (that the core technical team controlled). From this regard, the DAO Tracker being hosted by an entity independent from our team is desirable.

<div style="text-align: center"> — </div>

In [last month’s report](#api3-core-technical-team-report-july-2021), I mentioned that we’re back to focusing our attention on Airnode. We made a lot of progress this month, but we have yet to reach a milestone that would be appropriate to make an announcement at. In parallel to this work, we are overhauling our project management and release management strategy, which should increase the transparency of the state of development (essentially act as a team-scale roadmap), allow Airnode users to track when we will support certain features and help developers find out where their open source contribution would be most effective.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-september-2021.jpeg" caption="Popamania, album art." >}}

# API3 Core Technical Team Report, September 2021

We host our DAO dashboard on IPFS. There are a few ways to reach it:

- You can connect your Metamask to Ethereum mainnet and go to api3.eth/ This looks up the IPFS CID from the ENS contract and uses a public IPFS gateway to take you to the dashboard.
- You can go to https://api3.eth.limo.
- You can go to https://dao.api3.org to be redirected by api3.org to the public IPFS gateway.

In addition to some not always being available, all of these options require you to trust third parties. As a trustless alternative, we now provide [instructions](https://github.com/api3dao/api3-dao-dashboard?tab=readme-ov-file#running-the-dashboard-on-mainnet-in-a-docker-container) for building and running the DAO dashboard locally. In addition to being more secure, this method will always be available despite potential IPFS infrastructure outages.

<div style="text-align: center"> — </div>

In the [July report](#api3-core-technical-team-report-july-2021), we have mentioned that demand for a new Airnode release was building up, and after the DAO launch — which was most imperative — we finally had the opportunity to focus on it. We responded in three main ways: (1) Design a project management and release management flow to support rolling releases (mentioned in the [August report](#api3-core-technical-team-report-august-2021)), (2) start working towards a fast initial release, which can then be iterated on, (3) finalize the request–response protocol and have it audited.

We have made a lot of progress on all three of these items, but I will focus on (3) specifically. We have [released the pre-alpha version at the start of this year](#api3-dao-development-update-operations-cycle-1) both as a POC to demonstrate that we can feasibly achieve a large number of first-party oracles, and also to collect feedback from internal and external stakeholders. The contracts of this version were [audited](https://github.com/api3dao/api3-governance/blob/main/teams/core-technical/cycle-2/2021-02/API3%20-%20Software%20Review.pdf), and additional review and usage did not uncover additional issues. Therefore, despite its name, the pre-alpha version is actually quite solid.

One issue with the pre-alpha version is that it keeps the authorizer implementation out of the scope, and expects the user to implement it based on their needs (or make all endpoints public, which is quite fine in most cases due to how the [protocol is designed to have the requester pay for all gas costs](https://medium.com/api3/airnode-the-api-gateway-for-blockchains-8b07ff136840)). As described in the [March report](#api3-dao-development-report-march-2021), the authorizer is where the first-party oracle business model is implemented. This is why we refrained from locking in the authorizer design prematurely, yet we are now at a position where we have a clear understanding.

This month, we implemented authorizers, finalized RRP and are currently undergoing an audit by Certik. Once we pass the audit, we will publish an in-depth article about what has changed in the protocol since pre-alpha, but in short, it’s a much more streamlined user flow + ready-made authorizers.

<div style="text-align: center"> — </div>

As a final note, we would like to showcase the Airnode RRP Explorer, a tool to search for and decode requests and responses submitted through the Airnode protocol (specifically, the pre-alpha version, though updating it should be simple). To explain roughly, for the same reason that a regular Ethereum user needs to refer to Etherscan frequently (and developers a lot more), it’s not possible to imagine widespread adoption of the Airnode protocol without this kind of a tool being available. Therefore, it’s difficult to overstate the importance of this tool, and we’re excited to see how its development will continue.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-october-2021.jpeg" caption="Wolf of Chazes, shot by M. François Antoine de Beauterne in 1765, displayed at the court of Louis XV." >}}

# API3 Core Technical Team Report, October 2021

We are happy to announce that we have released Airnode v0.2! If you have been following our reports, you should know that we have focused our efforts on [Airnode](https://medium.com/api3/airnode-the-api-gateway-for-blockchains-8b07ff136840) since the [DAO launch](https://medium.com/api3/api3-authoritative-dao-staking-live-on-mainnet-4732d1e538cb), but we didn’t share further details. The development of Airnode is the most critical aspect of API3 operations, as almost the entirety of our efforts — technical and non-technical — depend on the existence of this [oracle node that will enable first-party oracles at scale](https://medium.com/api3/where-are-the-first-party-oracles-5078cebaf17). In this sense, we’re careful about treating Airnode development with the respect it deserves, and a part of this is preventing it from turning into an object of hype.

Airnode v0.2 is a silent release, meaning that it is public, but not necessarily publicized (this report doesn’t count because we have to tell you about it for governance purposes). What is more significant than the release itself is that we have a release management process in place, which we have tested now with great success by making this release. This will allow us to do rolling releases from here, meaning Airnode being improved iteratively (not that the pre-alpha version wasn’t good, but it had to be frozen and consequently couldn’t be improved further) and being able to address business problems by implementing new features.

I have recently posted an [article](https://medium.com/api3/beyond-pre-alpha-rrp-88717e9ed22d) on what has changed in the Airnode request–response protocol since pre-alpha. Note that a protocol update is only a subset of a node update, and this node update is especially extensive. I’ll try to list some high level items here:

- We switched from using Serverless Framework and Terraform to pure Terraform for managing our deployments. This will be transparent to the user, yet it improved the stability, future-proofness and cloud provider-agnosticism of Airnode significantly.
- We implemented an HTTP endpoint that can be used to make test API calls and an outbound heartbeat function for monitoring, primarily for integration platforms such as [ChainAPI](https://medium.com/api3/hello-chainapi-e1b386a74f1d).
- The OIS validator is now tested with all of the integrations that the API integrations team has done and is automatically being run as a step by the deployer. This means that if a user attempts to deploy an Airnode with invalid configuration files, the deployer will detect this and throw an error.
- In addition to implementing the authorizer contracts (see the [protocol update post](https://medium.com/api3/beyond-pre-alpha-rrp-88717e9ed22d) mentioned before), we implemented an interface in the airnode-admin package that Airnode operators can use to personally manage the whitelisting statuses of their clients. Note that this is an alternative to the Airnode management UI.
- Configuration files that specify integrations and node operator secrets are reworked for better separation and flexibility.
- Airnode is implemented as a monorepo, which means it is composed of many packages, some of which are useful for developers and node operators in standalone form. In addition to publishing the airnode-deployer Docker image (this is what you use to deploy an Airnode as a serverless function) and the airnode-client Docker image (this is what you use if you want to run Airnode in a container, locally or otherwise), we now also publish [all packages of the monorepo](https://www.npmjs.com/org/api3) as npm packages. This allows you to run the following command on your terminal
  ```
  npx @api3/airnode-admin derive-airnode-xpub --airnode-mnemonic “nature about salad…”
  ```
  (to derive the extended public key of your Airnode by providing your mnemonic) or import @api3/airnode-protocol in your contract to inherit RrpRequester to make Airnode requests.
- [This](https://x.com/api3dao/status/1331905770343067648) is no longer as impressive. The Airnode implementation in the airnode-deployer and airnode-client Docker images are now pre-built, which means they are quarter the size of the pre-alpha counterparts and they download and run much faster, providing a better user experience.
- The pre-alpha documentation was frozen along with the implementation. Since then, we have been working on documentation versioning and v0.2 contents.
- The example project of the pre-alpha version lives in a separate repo, which makes it very difficult to keep up to date. We migrated our examples to the Airnode monorepo at https://github.com/api3dao/airnode/tree/master/packages/airnode-examples and integrated them to our CI tests to make sure that they don’t fall out of date (nothing sours a developer away faster than the example projects being broken). We also extended the examples to not require a public chain or a cloud provider account to reduce developer on-boarding friction.

The one thing that we didn’t do is a complete refactor of the [node implementation](https://medium.com/api3/getting-to-know-airnode-162e50ea243e), as that was already very solid in the pre-alpha version. So even though this is quite a major release, we expect the node to keep behaving stably. I’m sure there are bits that I forgot to mention, but this is where you come in anyway. You’re more than welcome to poke around and give us feedback by creating [Github issues](https://github.com/api3dao/airnode/issues) or swinging by [our Discord](https://discord.gg/api3dao).

All in all, this was a satisfying end to our August–October grant cycle. This was made possible by a team of great people who take pride in their work. On behalf of myself and the entire API3 community, I thank the members of the core technical team for their great effort. We’re only getting started though, so stay tuned.

{{< figure src="/2023-08-31-api3-core-technical-team-reports-october-2021-2.jpeg" >}}

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-november-2021.jpeg" caption="Francisco de Zurbarán, Autoportrait, 1650." >}}

# API3 Core Technical Team Report, November 2021

We have been working on Airnode v0.3 during November and you can expect it to be released in the following days. We had two main objectives for this release:

- Allow the requester to specify an arbitrary single-level object to be returned (instead of a single point of data)
- Support Google Cloud Platform (GCP) for the serverless configuration

We managed to hit these objectives and a few more, which we’ll discuss in this post.

## Returning objects

Say you want an oracle to call https://www.crypto-api.com/markets?from=ETH&to=USD and return you the price of ETH-USD and the total volume of the market. There are commonly two options:

- Make an oracle request for the price and the volume separately
- Implement a specialized, hard-coded adapter that will give the price and the volume fused together

(1) is bad because it’s unwieldy and expensive. (2) is bad because it requires this adapter to be developed on a case-by-case basis. Our goal is to develop an oracle protocol that supports seamless and flexible API integrations to smart contracts, which includes protocolizing how the API response needs to be processed. Allowing requests to be specified to return encoded objects instead of a single point of data is the first step of these efforts.

Starting from v0.3, the requesters can specify that they want Airnode to make a specific API call and use the returned JSON to build any single-level object, which will be returned to the chain by the Airnode and decoded there. This is much more flexible (in that the requester is not limited to the existing adapters) and scalable (in that you don’t need someone to pre-build and deploy purpose-specific adapters) compared to existing methods, and should be enough by itself to serve the majority of the potential oracle use-cases. However, we will be continuing our efforts in extending the Airnode protocol for better flexibility in this regard in the following versions.

## GCP support

We have mentioned that [we switched to a pure-Terraform configuration in v0.2](#api3-core-technical-team-report-october-2021) that will allow us to port Airnode to various cloud providers more easily, and in a more maintainable and secure way. This was followed through by extending the cloud provider options for the serverless configuration from the existing AWS to GCP.

Note that this is not necessarily a matter of either/or. The Airnode protocol is uniquely designed to be able to be served by multiple independent deployments for optimal uptime. This means an Airnode operator can use serverless configurations deployed on AWS and GCP simultaneously, and in fact, this is the recommended setup. In this way, providing GCP (or rather, a second cloud provider in addition to AWS) support fulfills a critical step in allowing unbreakable Airnodes to be deployed. We are planning to extend support to Azure and potentially other cloud providers in the future.

## Stress tests and adjustments

In a first-party oracle solution, an API is served only by a single oracle, operated by the API provider. This means there is no node-level redundancy, resulting in maximal cost-efficiency. However, this also means that we can’t depend on node-level redundancy for availability and have to build a truly highly available node (even if it’s not actively monitored and maintained by dedicated personnel). Recall that the Airnode protocol allows each requester to specify a different wallet to fulfill their requests, which enables oracles with infinite individual bandwidth. However, the node implementation should also be designed and built in a way to support this, which is one of the reasons why the recommended configuration is serverless.

To fulfill our vision of scaling up to fulfill any and all API connectivity needs, Airnode must be accessible in a permissionless, programmatic way. This is a unique goal in the oracle space, and poses a specific challenge: We can’t depend on access restriction as a security measure, i.e., anyone will be able to spam an Airnode on-chain after programmatically buying access, and Airnode should be built in a way that this is inconsequential. The current serverless configuration gives us the tools to achieve this, yet this is still a lofty goal that needs to be attended to specifically.

While developing this version, we conducted stress tests in various environments to assess the limits of the current implementation. Based on our findings, we made adjustments to our serverless configuration that greatly improved the resiliency of the node to the degree that it’s already better than the available alternatives. However, we have a few further goals around this matter that we want to fulfill in the upcoming versions:

- Improve the node architecture so that it can scale limitlessly (in practice, up to the limit imposed by the cloud provider on an account-basis)
- Allow the user to quantify the capacity they want to allocate to specific chains, and this capacity to be guaranteed by the node
- Come up with an optimal configuration that we can recommend to serve use-cases that will secure an arbitrarily large amount of value

In addition to the above, we implemented an image that wraps the airnode-admin CLI, mainly to allow the API providers to generate a mnemonic for their Airnodes. Features described above are demonstrated with example projects under the airnode-examples package, and our documentations are extended with these features. We recently planned the upcoming v0.4 according to the strategic needs of the DAO, and will start work on it soon.

<div style="text-align: center"> — </div>

If you haven’t noticed, we updated our whitepaper to v1.0.2. This was a long way coming, as the described staking reward mechanism was outdated, and despite v1.0.1 linked to a [post that went through the planned updates](https://medium.com/api3/api3-tokenomics-update-f032d6e49b30), some readers overlooked that and were confused. This update worked the contents of that post into the whitepaper, while removing the outdated content such as the scheduled staking reward graph. What was particularly rewarding was realizing that we had already delivered a lot of the things that we said we would deliver in the whitepaper, and the respective statements needed to be rephrased to reflect that. Changing “we will do”s to “we did”s is the best kind of update a whitepaper can get, and we’re looking forward to doing more of this in the following months.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-december-2021.jpeg" caption="Pieter Brueghel the Elder, The Hunters in the Snow (winter), 1565." >}}

# API3 Core Technical Team Report, December 2021

As promised in the [November report](#api3-core-technical-team-report-november-2021), we released Airnode v0.3 on December 7th. We started working on v0.4, which is largely focused on revising how the requests are handled to:

- Enable unlimited scaling (to the point that the cloud provider allows) and chain-specific provisioning of concurrency, which will allow a single node deployment to serve the needs of all API providers, regardless of the number of chains being served or the expected volume. This means Airnode will be deployed the same way — without requiring additional [orchestration](https://en.wikipedia.org/wiki/Orchestration_(computing)) — if it’s only for testing, serving a single production use-case or serving many production use-cases across many blockchains.
- Allow requesters to specify the API provider to sign the response, yet a separate reporter to submit the fulfillment transaction (see the second figure here, or Section 4.1.1 from [our whitepaper](https://github.com/api3dao/api3-whitepaper/blob/master/api3-whitepaper.pdf)). This potentially solves some significant business problems and makes new use-cases possible. We will elaborate on this feature as it comes closer to fruition.

In the meantime, we are also working on the v1.x protocol contracts, which include PSP (publish–subscribe protocol), RRP+PSP Beacons, dAPIs, token lock-up and payment functionality for automating access to API3 services.

After Certik, Sigma Prime has completed a second audit of the v0.x protocol contracts. The audit report can be accessed through [our monorepo](https://github.com/api3dao/airnode/tree/master/packages/airnode-protocol/audit-reports). No vulnerabilities have been uncovered in the protocol, and releases v0.2 and v0.3 are once again confirmed to be safe to use. Nevertheless, it is planned for the v0.4 release to use a new iteration of the contracts where the suggestions from the audit report are implemented.

<div style="text-align: center"> — </div>

This month, we published [an article introducing Beacons](https://medium.com/api3/beacons-building-blocks-for-web3-data-connectivity-df6ad3eb5763). A Beacon is a data feed that is powered by a single first-party oracle. It can either be used by itself, or multiple of them can be combined to form dAPIs. This relates to the core technical team in that the Beacons and the Beacon-based dAPI architecture is our design. In other words, similar to [what has happened with the authoritative DAO](https://bbenligiray.medium.com/story-of-the-authoritative-dao-1153990a3eff), the core technical team has claimed dAPI (and Beacon) development and operations, despite them not being a part of our responsibilities according to our most recent proposal.

The core technical team is responsible for building a scalable infrastructure, which increases the leverage of the ecosystem participants. Developing ecosystems commonly don’t have participants that can utilize the available tools to their full potential. A common pitfall here is for the core technical team to go in and show ’em how it’s done. This is done by choosing a few, large enough clients and bending over backwards for them. This will result in some short-term success and mutual backslapping, but it ends up poisoning the project because:


- The core technical team stops thinking about the untapped potential and only about the needs of the few clients. This is fine if the goal is to become a service provider, but not if it is to build a protocol and an ecosystem on it — imagine Ethereum developed with specific dApps in mind. This stunts the development of the protocol, and the general ecosystem participants will leave for greener pastures because they are not being cared for.
- Once the vision for an ecosystem is lost, the future of the project is now hinged on keeping the existing clients, which means continually building what is asked for rather than the grand vision, so it’s a downward spiral from here.

These observations delayed us from participating in dAPI development, noting that building Beacons or dAPIs wouldn’t have been enough, they would also need to be actively operated, which would take up a considerable amount of time that we could spend developing the node and the protocol (which can be used for much more than Beacons and dAPIs). That being said, we are indeed the best people available to operate these services reliably. We have a two-fold solution to this:

- Build towards a level of readiness where we would be comfortable with allocating some of our resources towards operations. This has been partly achieved by the recent Airnode releases, which is why we have stepped in now and not earlier.
- Continue the core development in a way to feasibly [offload the operations](https://medium.com/api3/fractal-scaling-of-api3-b3ba78c9dcb7) in the future, which would be made possible by data feed operation to be more of a set-and-forget matter, most importantly through the implementation of PSP.

In summary, the core technical team has taken over development and technical operation of Beacons, and dAPIs by implication. This work will be carefully balanced with infrastructure development to uphold the long-term interests of API3. From a general point of view, the core technical team is on track with building the deliverables from the [whitepaper](https://github.com/api3dao/api3-whitepaper/blob/master/api3-whitepaper.pdf) in the [stated three years](https://medium.com/api3/the-api3-public-token-distribution-event-has-ended-644e984f50fc) (of which one has passed) without requiring outside help ([assuming that our proposals pass](https://bbenligiray.medium.com/decentrally-governed-projects-cant-be-roadmapped-9400d56d969f)). We are still carefully optimistic about external dAPI operation teams (meaning “external to the core technical team”), and will be designing and documenting the Beacon and dAPI operation process in a way to make that feasible.

Thanks for reading our report, Happy Holidays and best wishes for the New Year for the API3 community!

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-january-2022.jpeg" caption="A Composite Elephant And Rider (Mughal), 1600–1640." >}}

# API3 Core Technical Team Report, January 2022

As explained in the [December report](#api3-core-technical-team-report-december-2021), the core technical team carefully started expanding its efforts towards building products that utilize Airnode, in addition to building Airnode itself. [Beacons](https://medium.com/api3/beacons-building-blocks-for-web3-data-connectivity-df6ad3eb5763) are the first of such oracle primitives, yet “building Beacons” doesn’t say much because a Beacon is an abstract product, and is brought into reality by building and combining many pieces of technology. What unites these is that they all depend on or interact with Airnode or its protocol, and this recent work has shown us that Airnode is a really solid foundation to build things on thanks to its design and implementation.

We continued our work on Airnode v0.4 this month, and are expecting to release it in a week. We didn’t rush the work on v0.4 — as the current v0.3.1 is provably capable of powering Beacons — and aimed to achieve all of our wants instead. The scope for v0.5 is agreed on; the features to be implemented will mostly be focused on improving Beacon performance further in terms of cost-efficiency.

Here’s something that you may not have heard about before: Airkeeper. We have been [criticizing oracle nodes](https://medium.com/api3/where-are-the-first-party-oracles-5078cebaf17) for not being designed to optimize the user requirements. The truth is, the same requirements apply for keeper nodes and bridges, people want them to be performant and set-and-forget. Furthermore, adding the ability to make API calls to such nodes would supercharge them, and in our case, these would be first-party API calls that can be depended on for executing transactions of financial nature. This all is obviously exciting, but our reason for building Airkeeper now is more practical: We want Beacons to be operable solely through the request–response protocol (RRP).

At the moment, Airkeeper is specifically designed to “keep” a Beacon alive based on an arbitrary deviation threshold. It is similar to Airnode in terms of operational requirements, meaning that it can easily be operated by an API provider. Furthermore, one can operate as many of them as they want in a third-party way to create redundancy, and add an incentive mechanism to increase their robustness. Note that the Airnode protocol also doesn’t include an incentive mechanism. From the whitepaper:

> …Finally, let us briefly mention how the Airnode protocol approaches monetization. It is common for a project-specific token to be worked into the core of the protocol in an attempt to ensure that the said token is needed. However, this induces a significant gas price overhead, severely restricts alternative monetization options and creates overall friction. For these reasons, the Airnode protocol purposefully avoids using such a token. Instead…

Here, the motivation is the same. The keeper protocol that isn’t built around a token will eat the others.

I like describing the publish–subscribe protocol (PSP) as an oracle and a keeper rolled into one. Therefore, Airkeeper could be seen as a less-protocolized, proto-PSP node. In other words, Airnode that supports PSP will be able to do everything that the Airkeeper is currently doing, including triggering first-party RRP requests when necessary. We are getting into the weeds a bit here, but the point is, the long-term plan for Airnode is for it to be a first-party, cross-chain oracle and keeper node. This new functionality is developed in components independent from Airnode (such as Airkeeper) to avoid introducing issues to Airnode, which is desired to be very stable. Once this functionality reaches maturity, e.g., is able to support full-PSP, it will be merged to Airnode.

Another key component of Beacons are their operational side. In a decentralized solution, this means keeping a transparent source of truth, which can then be used to top up the sponsor wallets periodically, visualize the metrics and monitor them to detect anomalies. The key thing we have considered here was to not reuse any Airnode/Airkeeper implementation. Although we have a strong toolbox we can draw from, we are verifying the integrity of this very toolbox, which makes it off-limits for this kind of work.

Finally, one builds a product for it to be used. Any developer knows the importance of a good SDK. However, what that means completely depends on what it’s for. The Airnode protocol is very powerful, which is a requirement for some builders such as [OBP](https://medium.com/api3/api3-and-open-bank-project-initiate-a-10-year-development-partnership-to-bridge-open-banking-with-299b9f1384a3). There are also some builders that just need the price of X, and they can’t be bothered with reading through our Airnode documentation, however much pedagogical it is. What we are aiming with the Beacons is to abstract away the entire Airnode implementation, so that the user simply needs to interact with a contract that they read a value from. But even while doing so, we are benefiting from the Airnode protocol design, in that a first-party Airnode has the same address on all chains, and a specific request to these Airnodes are all identified by the same ID on all chains, which means we don’t need to duplicate documentation across chains — one thing that works on one chain also works on another in a verifiably identical way.

And this is the end product:

{{< figure src="/2023-08-31-api3-core-technical-team-reports-january-2022-2.png" >}}

A first-party Airnode–Airkeeper pair, operating a Beacon (yellow) that tracks the API response (green) at the deviation threshold they were configured for. We will be making a variety of these Beacons available at [ETHDenver, of which API3 is the official DeFi track sponsor](https://medium.com/api3/announcing-amberdata-beacons-powering-defi-at-ethdenver-330a4084c1b5). We are big proponents of user-centered design, so we will use the feedback gathered from Web3 developers and projects to hone our design.

As a final note, I find it ridiculous how swift and skillfully everything around Beacons is tied together, all the while not disrupting the work on Airnode. For this, I feel the need to congratulate the core technical team.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-february-2022.jpeg" caption="William Holman Hunt, The Miracle of the Holy Fire, 1892–1899." >}}

# API3 Core Technical Team Report, February 2022

We were at ETHDenver and it was glorious! We used this opportunity to showcase Amberdata [Beacons](https://medium.com/api3/beacons-building-blocks-for-web3-data-connectivity-df6ad3eb5763), which were received with a lot of enthusiasm and approval. It was encouraging to see that potential users found first-party oracles to make a lot of sense, and gaining widespread adoption is only a matter of time and effort put into scaling. All this was made possible by the core technical team deciding to expand its efforts into building live data feeds in [mid-December](#api3-core-technical-team-report-december-2021), and this quickly coming into fruition with 20 RRP-based Beacons each on 4 chains in early-February. This demonstrates how agile one can be when they use Airnode to put together higher level oracle services, and you can expect us to do more of this.

As discussed in the [December report](#api3-core-technical-team-report-december-2021), it’s important to balance product development and protocol development. Products are what the market wants and needs, yet a powerful Airnode is what makes it easy to build impactful products. Add good documentation and guides on top of this, and [our users will be building the products for us](https://x.com/dao_kassandra/status/1493261830046859270). Based on this reasoning, we did not let Beacon development stop Airnode development, and [released Airnode v0.4](https://github.com/api3dao/airnode/releases/tag/v0.4.0) early in the month. This release was mostly about improving RRP performance and implementing all of the breaking changes anticipated in v0 early on. Work on v0.5 has started, and it’s expected to be released in March.

Feel free to refer to the links above for more details about what we have built this month, and let me quickly plug [a talk](https://www.youtube.com/watch?v=94tqEQgTwVg) I gave at ETHDenver on our approach to designing technical solutions, which places Beacons in a larger framework. You can also take a look at the [Beacon workshop](https://www.youtube.com/watch?v=0uMpWEa7kiA) or [Ashar’s RRP demo](https://www.youtube.com/watch?v=Hss-8Tzg7TI). Cheers for reading!

{{< figure src="/2023-08-31-api3-core-technical-team-reports-february-2022-2.jpeg" >}}

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-march-2022.jpeg" caption="Illumination from Pontifical of Renaud de Bar, 1303–1316." >}}

# API3 Core Technical Team Report, March 2022

We have released [Airnode v0.5](https://github.com/api3dao/airnode/releases), which implements all remaining requirements for [Beacons](https://medium.com/api3/beacons-building-blocks-for-web3-data-connectivity-df6ad3eb5763). We’re continuing having our contracts audited in a rolling fashion, and a new preliminary report verifies (for the fourth time) that the v0 protocol contracts do not contain any unintended vulnerabilities. Accordingly, you can expect a v0.6 release in the coming April that rolls out the v0 protocol on more EVM chains. Furthermore, work has started on porting Beacons and dAPIs to some non-EVM chains. Details about the scope and budgeting of this work will be shared in the coming months.

After the v0.5 release, we were able to focus more on Beacon-specific development. The contract that implements Beacons and dAPIs is designed to be compatible with all Airnode protocols (RRP, PSP, relayed RRP, relayed PSP, API-signed data). In contrast, the [ETHDenver Beacons](https://medium.com/api3/announcing-amberdata-beacons-powering-defi-at-ethdenver-330a4084c1b5) are being operated only using RRP — which has proven itself to be quite reliable on its own. We will operate our production Beacons using PSP for cost-efficiency and improved responsiveness. On top of this, we will utilize the API-signed data served by the HTTP endpoint implemented in Airnode v0.5. This scheme is superior to even PSP in terms of cost-efficiency and responsiveness, but more importantly, it allows the core technical team to respond to incidents without disturbing the trust-minimized, first-party nature of the service. Using PSP and API-signed data simultaneously allows us to enjoy the advantages of both without any degradation in trustlessness because the data will always be cryptographically signed by the API provider.

Finally, for those who have missed it, we have pushed an updated DAO dashboard version to production. With that, let me link you to [an article where we do a deep dive into dAPIs](../2022-31-05-dapis-apis-for-dapps).

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-april-2022.jpeg" caption="Katsushika Hokusai, Remarkable Views of Bridges in Various Provinces: Old View of the Boat-bridge at Sano in Kōzuke Province, 1833." >}}

# API3 Core Technical Team Report, April 2022

We have finalized our [audit](https://github.com/trailofbits/publications/blob/master/reviews/API3.pdf) with Trail of Bits that covers the [Airnode protocol v1](https://github.com/api3dao/airnode-protocol-v1) — RRP, PSP, relayed-RRP, relayed-PSP and signed data-based usage. All of these protocols are used in our [dAPI](../2022-31-05-dapis-apis-for-dapps) server contract, and will go into production soon to power [Beacons](https://medium.com/api3/beacons-building-blocks-for-web3-data-connectivity-df6ad3eb5763). In addition to the protocol contracts, the Airnode monetization contracts are audited as well, which means they can be used as is (for example, if you want to set up an Airnode that only responds if the requester has paid a subscription fee in stablecoins) or as a solid foundation to build your custom logic on. Our work at the protocol side is done for the foreseeable future. Now, the node needs to catch up to implement these protocols fully.

A lot of the v0 and v1 contracts overlap, which means the audit above also applies to protocol v0. With this added assurance, we have released [Airnode v0.6](https://github.com/api3dao/airnode/releases/tag/v0.6.0), where we have rolled out official Airnode integrations to the following smart contract platforms and their testnets: Ethereum, Arbitrum, Avalanche, BNB Chain, Fantom, Gnosis Chain, Metis, Milkomeda C1 (Cardano), Moonbeam, Moonriver, Optimism, Polygon and RSK. Projects building on these chains can expect to be able to enjoy API3 services earlier, yet we’re planning to address the rest of our backlog rapidly.

One of the biggest technical news of this month was the announcement of the [ChainAPI beta access](https://medium.com/chainapi/get-first-access-to-chainapi-and-help-us-make-it-even-better-752e4e1e05d3). After a lot of development and closed testing, ChainAPI is finally ready to meet its first users. At this stage, ChainAPI helps the user create and manage API–Airnode integrations, and deploy Airnodes that will serve these integrations. If you’re planning to run an Airnode, I heavily recommended you to apply to beta access.

I don’t want to dilute these three big news with filler, so I’ll keep this one short. Let me end by plugging an article I’ve published recently: [Commercial building blocks](../2022-04-17-commercial-building-blocks), which is essentially a personal time-investment thesis, as in why I find API3 worth working on above everything else.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-may-2022.jpeg" caption="Sophie Green, The March, 2021." >}}

# API3 Core Technical Team Report, May 2022

We did something uncommon this month, and revealed QRNG without any prior mention. A first-party oracle service being provided on 13 mainnets and 4 testnets, and this being launched on all chains simultaneously is a first, and foreshadows what Airnode will do in the future. There are two main reasons why we were able to do this:

- The single Airnode that ANU Quantum Numbers deployed is serving all of these chains simultaneously, in an isolated way. This allows us to provide the same service on more chains with no additional cost or maintenance requirement.
- The Airnode protocol allows the requester to cover all gas costs, which is one of the things that makes it _set-and-forget_. This is especially beneficial if the chain has limited infrastructure and getting a hold of some native currency that is used for gas costs is relatively difficult.

As you can imagine, these advantages translate to all use-cases when it comes to serving under-served chains, and not only QRNG.

One important benefit of working on QRNG was that we had to do some R&D to make it possible, which provided important insights about API response caching, stateful authentication methods such as OAuth2 and a way to implement them with a stateless Airnode, without having to resort to custom builds or external dependencies. In this regard, we got much more out of QRNG than the time that we put into developing it.

We have continued focusing the majority of our attention on building [Beacons](https://medium.com/api3/beacons-building-blocks-for-web3-data-connectivity-df6ad3eb5763) and [dAPIs](../2022-31-05-dapis-apis-for-dapps). As you may know, we have been operating 25 Beacons each on 4 testnets since [January](#api3-core-technical-team-report-january-2022). We also started operating Beacons on 4 mainnets since the end of April, with over 30,000 Beacon updates! One of these Beacons was UST/USD on Avalanche, which has proven to be the perfect stress test (see below). Overall, we’re happy to say that our Beacons have performed excellently during these trying market and chain conditions, and we can’t wait to allow projects to start using them

{{< figure src="/2023-08-31-api3-core-technical-team-reports-may-2022-2.png" caption="Airnode gazing into the abyss." >}}

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-june-2022.jpeg" caption="Illumination from Ein wahres Probiertes und Pracktisches geschriebenes Feuerbuch, 1607." >}}

# API3 Core Technical Team Report, June 2022

We have released [Airnode v0.7](https://github.com/api3dao/airnode/releases/tag/v0.7.0), which was a big update that both reworked parts of Airnode and implemented new features that we’re using heavily in new integrations. We have started working on v0.8 and an important part of this release is that its development will be tracked publicly. This has two implications: (1) The users will know what to expect from v0.8 before it’s released, (2) External contributions will be more feasible, as one can pick up a task from the backlog and work on it.

Another important development is that the OIS (Oracle Integration Specifications) implementation in the [Airnode monorepo](https://github.com/api3dao/airnode) is migrated to [its own repo](https://github.com/api3dao/ois) (and the package name is updated from @api3/airnode-ois to @api3/ois). We have separated the OIS docs from Airnode docs before and this sets OIS further apart from Airnode as an oracle integration standard, rather than the integration specification format of a specific oracle node implementation. The current version of OIS was specified almost 2 years ago and what is expected from an oracle has changed since then. Specifically, in addition to delivering API responses, oracles are required to read on-chain, archival and logs data from arbitrary chains, and combine the resulting data in arbitrary ways. By supporting this functionality in coming versions of OIS, we will enable first-party keepers and bridges, in addition to more novel services.

[ChainAPI being launched this week](https://medium.com/chainapi/chainapis-web3-api-integration-platform-is-now-live-996521f276b1) is probably important news for people reading our reports. For people who have already used an Airnode following our docs, the most interesting feature that ChainAPI provides is being able to check the status of the Airnode you have deployed. It is generally recommended for the API providers to have redundant deployments. These should at least be on separate availability zones, but the gold standard is a multi-cloud deployment (for example Amberdata has an AWS and GCP deployment at the moment). Furthermore, we practice A/B updates, which means an old deployment isn’t taken down before the new one is confirmed. Therefore, to provide a very reliable service, an API provider will sometimes have four deployments at a time on multiple platforms, which is obviously difficult to juggle. Airnodes deployed using ChainAPI are configured to send heartbeats to ChainAPI (a fully-outbound, trustless process), which allows ChainAPI to display what deployments you have online at a time, on which cloud providers and regions, etc. This functionality and everything else that ChainAPI provides is completely trustless (so that it doesn’t degrade the security guarantees that first-partyness provides) and for free.

As a final note, we’re finally there with our [dAPIs](../2022-31-05-dapis-apis-for-dapps). We have been running them on various mainnets for a long time now with great success. We have revamped our data feed docs to be more dAPI-focused, including the dAPI Browser embedded in our docs that displays on-chain data in real-time. While continuing the development of Beacon set-based dAPIs and the coverage product (and by the way, we released a [whitepaper patch](https://github.com/api3dao/api3-whitepaper/releases/tag/v1.0.3) related to that), our next step is to start getting our first dAPIs in use.

{{< figure src="/2023-08-31-api3-core-technical-team-reports-june-2022-2.jpeg" caption="Illumination from Feuer Buech, 1584." >}}

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-july-2022.png" >}}

# API3 Core Technical Team Report, July 2022

We’ve been running testnet [Beacons](https://medium.com/api3/beacons-building-blocks-for-web3-data-connectivity-df6ad3eb5763) since [January](#api3-core-technical-team-report-january-2022) and mainnet Beacons since the end of April. We encountered some exciting chain and market conditions during this period, yet Airnode performed as intended without any surprises. As a result, we finally decided to [ship our data feeds](https://medium.com/api3/api3-dapis-available-on-polygon-bnb-chain-avalanche-and-rsk-a6c088df606f). Note that we not only provide our data feeds as Beacons, but also [dAPIs](../2022-31-05-dapis-apis-for-dapps). Currently, the dAPIs are pointed to individual Beacons by a 3 of 6 multisig controlled by members of the core technical team (more documentation about this is coming). In the near future, we will set up Beacon sets and point the dAPIs to them where appropriate.

The [API3 whitepaper](https://github.com/api3dao/api3-whitepaper/blob/master/api3-whitepaper.pdf) proposes that service level guarantees in the form of an insurance-like product is the ideal security mechanism for oracles (and that this wouldn’t be optimally cost-efficient with non-first-party oracles). Even though we haven’t released this product yet (and the data feeds will be free to use until then), the fact that we’re planning to do so in the near future caused us to consider it at every step of designing the data feeds and deciding if they are ready to be used yet. “Would we want to insure this at scale?” was a question that we frequently asked ourselves and made decisions accordingly, which validates the idea that oracle services should not only come with coverage, but that should ideally be by the provider of that service — in this case, API3.

The second major product we launched this month is [API3 Market](https://market.api3.org/). We had been working on this with Protofire for the last three months, with significant contribution from our team due to the importance of the project. The result is very slick and pretty, so check it out if you haven’t already. The core technical team has fully taken it over from here and have already started improving it based on the user feedback.

The main difference between API3 Market and data feed pages built by other oracle projects is obvious from the name: API3 Market is an interactive platform where you would go to buy access and coverage for oracle services (rather than the typical one that is designed to prove token holders that the project has working data feeds). This is directly related to our vision for [API monetization on Web3](https://medium.com/api3/api-monetization-on-web3-7d5fe855a8e3), and you can consider API3 Market to be one of the foundations that we will build this on.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-august-2022.png" caption="Simone Martini, Miracle of the Child Falling From the Balcony, 1324." >}}

# API3 Core Technical Team Report, August 2022

In preparation for our insurance-like service coverage product, we scheduled a fourth audit of the DAO and the staking pool to be done this month. Unlike others, the scope of this audit included the front-end, and there were two critical findings in the module we specifically requested extra attention to. These findings are now patched in production, and we confirmed that they haven’t been exploited in the past. There were no findings relating to contract code that warranted a response. We will [publish the audit report](https://github.com/api3dao/api3-dao/tree/main/reports) once it’s finalized, which you can get detailed information from.

At the data feed operation side, we were set back by Airnode issues around GCP deployments. We’ll rework the related components to fix these problems and potentially implement features that weren’t possible before.

With this 3 month-cycle, the core technical team kicked off the monetization effort. This primarily relates to premiums paid for service coverage policies being translated into [API3 tokens being bought back from the market and burned](https://medium.com/api3/api3-tokenomics-update-f032d6e49b30), and [API providers being compensated at scale](https://medium.com/api3/api-monetization-on-web3-7d5fe855a8e3). We’re planning the end result to be an end-to-end flow that starts at the [API3 Market](https://market.api3.org/) and ends with API3 token scarcity and happy API providers.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-september-2022.png" caption="Katsushika Hokusai, The Wave (outpainted), 1831." >}}

# API3 Core Technical Team Report, September 2022

We released [Airnode v0.8](https://github.com/api3dao/airnode/releases/tag/v0.8.0) this month, which introduces a few useful features that we’ve been using in customized versions for a while. We’re currently working on v0.9, and have already planned out v0.10 and v0.11. As a reminder, we track our work on a public board (even though we can’t make all issues publicly visible), and have started representing more of our work there by fully migrating from our Jira boards.

The more curious people may have already noticed that we track our data feed operations (new API integrations, new Beacons being set up, dAPIs being reconfigured, etc.) using [a public repo](https://github.com/api3dao/operations-deprecated). We used this both to easily coordinate among ourselves through git, which we’re all conveniently familiar with, and also to provide the public and dependent services with an easily accessible, human-browsable, single source of truth. This approach made a lot of things possible — for example, tracking subscriptions and coverage services and the related payments, and processing these automatically with minimal development overhead — yet we found that it’s not dynamic and scalable enough for what is to come. In line with our future direction, we started rebuilding this piece of backend this month. Additionally, we did a lot of work this month on refactoring and improving the infrastructure that we have developed to operate data feeds at scale.

With recent additions to the core technical team, we finally gained the capacity to be able to do in-house API integrations (as the core technical team), and more importantly, analyze APIs for fitness to be used in dAPIs. Being able to use ChainAPI in integrations was reportedly a huge help in data feed integrations, which is good news considering that [ChainAPI has launched workspaces](https://x.com/ChainAPIcom/status/1551613079846273025) and we decided to do all future data feed integrations through this functionality. While speaking of ChainAPI, it now [supports all chains](https://x.com/ChainAPIcom/status/1570804159074672643) that Airnode protocol v0 (which will be used by Airnode v0.x) is officially integrated to.

We continued working on the data feed-coverage smart contracts and their frontend. This frontend will be implemented as a part of the [DAO dashboard](https://api3.eth.limo/), as it’s essentially a dApp that the data feed users will use to interact with the DAO. Similar to how you would use the DAO dashboard to stake and vote, and Enormous’s DAO Tracker to see what the other DAO members are doing, there will be a separate frontend where you can inspect what coverage policies have been created for others, what claims people are making and what their statuses are. One thing that I forgot to mention in the August report is that Enormous’s team —which was an independent DAO grantee previously — has joined the core technical team for better coordination.

The most important news of this month is that [the Market](https://market.api3.org/) is updated to allow users to make a transaction on the respective chain to allow their contract to read any dAPI for the next 30 days. The previous version of the Market required the users to contact us for this in preparation of the on-boarding flow we had designed. As we diverged from these plans, the requirement to contact someone became a needless friction point, which we temporarily alleviated by this change. We’re planning to improve this data feed integration process further.

To avoid announcing announcements in these monthly reports, I either note what we have already delivered, or continuous infrastructure work whose results you will never see directly. This requires me to omit a lot of ongoing work. However, things have finally reached a level of maturity that warrant them being shared, so be on the lookout for new articles over the next month, which will unveil plans that will greatly affect API3 and this team.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-october-2022.png" >}}

# API3 Core Technical Team Report, October 2022

We released [Airnode v0.9](https://github.com/api3dao/airnode/releases/tag/v0.9.0) this month, which reworks how cloud resources are managed to address an issue with GCP redeployments and prevent similar issues in the future. We still have a few additional v0 releases planned before we start working on Airnode v1.

The work on the new data feed operation infrastructure mentioned in the [previous report](#api3-core-technical-team-report-september-2022) is being continued. Notably, support for Beacon sets (aggregated data feeds) is largely completed, including operation and their display on the [Market](https://market.api3.org/). Such features will not be released as soon as they become available, and their launch will be grouped and sequenced in a planned way.

The most interesting news of this month was the announcement of byog — bring-your-own-gas. This is a spin-off from the core technical team to aggressively expand the reach of oracle services based on API3 technologies. The first of these services are byog Beacons, which are data feeds that are readily available on a large number of chains that start operating immediately as soon as the respective sponsor wallet gets funded. Read the [blog post](https://bbenligiray.medium.com/introducing-byog-b8d5c01d9e82) for details.

And that’s it, this is the last of the monthly core technical team reports. As you will find out in the following weeks, we are nearing the completion of the [original whitepaper](https://raw.githubusercontent.com/api3dao/api3-whitepaper/master/api3-whitepaper.pdf), and are dovetailing into a new phase, which will require the technical teams to be restructured. This will result in the new core technical team focusing on foundational (yet boring) work such as Airnode development, while the other teams will be shipping the products that the public will be interested in. It’s not producive to write monthly reports that amount to “we released an Airnode version this month”, so it makes sense to leave the communication around these newly shipped products to the respective teams.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-november-2022-february-2023.jpeg" caption="Henry Stinson, Untitled Wall Mural, 2019. (Columbia Heritage Photographs)" >}}

# API3 Core Technical Team Report, November 2022–February 2023

By providing their services in the form of APIs, businesses extend their customer base to include computer programs, in addition to humans. API3 enhances these APIs for them to be able to cater to smart contracts as well. This effort has both technical and business development aspects, and considering the size of the API market, the successful scaling of it is critical for API3’s goals. We approach this problem from two directions:

1. Protocolize the integration and the [business model](https://medium.com/api3/api-monetization-on-web3-7d5fe855a8e3), and build tools that utilize these protocols to enable all parties to self-serve to minimize bottlenecks
2. Use efficient methods to scale up the operations that cannot be protocolized

An example to (1) is [Airnode](https://medium.com/api3/airnode-the-api-gateway-for-blockchains-8b07ff136840), which API providers can use to provide first-party oracle services on their own (instead of having to partner with a third-party oracle solution, which is a much more complex arrangement). The API–Airnode integration is defined by OIS, which API providers can create using [ChainAPI](https://chainapi.com/) in a way that requires very little blockchain know-how. The next ChainAPI proposal to be delivered addresses the protocolization of the business model. At the end-user integration side, byog has showcased a model that utilizes Airnode to set up data feeds at scale, without stipulating existing demand. This approach leapfrogs over the traditional flow of “dApp asks for a data feed, oracle project researches feasibility, agreement gets signed, data feed is set up” and reduces the integration process down to minutes. The dAPI team will use this model as a foundation to build a similarly frictionless user flow for data feeds aggregating from multiple sources at [API3 Market](https://market.api3.org/).

Development of the protocol and the tooling mentioned in (1) typically needs to be regarded as operations that API3 will have to undertake internally, and thus has to be considered under (2). As you may have already noticed from the above, we adopt a team of teams approach to scale these operations up efficiently, where the teams give separate proposals, manage separate budgets, and thus are largely autonomous. Since November 2022, the three teams below have spun off from the core technical team and made their first proposals:

- The dAPI team: Responsible for data feed technical operations (except integrations) and the development of the API3 Market
- byog: Develops tooling for self-funded feeds and operates their own self-funded feeds using their own API, manages the data feed integrations for the dAPI team
- Vacuumlabs: Supports all technical teams (excluding byog) in various ways

In addition to these, the ChainAPI team still develops their platform independently, and the core technical team is still responsible for core technology such as Airnode and its protocol. This all being said, it shouldn’t be surprising that these five technical teams cooperate extensively, and the lines between the teams often become a matter of technicality during our work.

## OEV

We have announced our work on [oracle extractable value (OEV)](../2022-11-01-oracle-extractable-value-oev) in November, which was accompanied by a [litepaper](https://raw.githubusercontent.com/api3dao/oev-litepaper/main/oev-litepaper.pdf) that the core technical team has contributed to. By doing so, we’ve answered some of the open questions from the original whitepaper, such as “how do you price a data feed service in a programmatic way” (the winning bid in the OEV auction is an exact measure of the value being created by an update) and “how do you convince projects to pay for a service that they’re used to receive for free” (the projects will practically be paid to use our data feeds, which beats free).

An important objective of the litepaper was to disperse any doubts about if this can be delivered in a timely manner, both to API3 stakeholders and potential users. Coinciding with the litepaper release, the dAPI team placed the OEV launch in the Phase 3 of their roadmap, after aggregated feeds and before security coverage support. Accordingly, the core technical team immediately started working on the OEV implementation, and once the development is complete, it will be handed off to the dAPI team to be operated. The overarching Vacuumlabs team will make sure that this hand-off happens smoothly.

## Airnode

We have released [Airnode v0.10](https://github.com/api3dao/airnode/releases/tag/v0.10.0) this cycle, which was a big one. The most fundamental change was to do with how the deployments are stored by the cloud provider, and the deployer CLI being revamped to make use of this. As a result, the user can now manage their deployments as easily as Docker containers running locally.

We have implemented [authorizers](#api3-dao-development-report-march-2021) for protocolized monetization schemes to be built on top of them. An authorizer has to be on the same chain as the requester contract, which means a lot of integration overhead in a future with many side-chains and roll-ups. v0.10 adds cross-chain authorizers, which essentially allows the Airnode to serve many chains, but require payments for these services to be made on a single chain, such as the Ethereum mainnet. This new feature will be used by the upcoming ChainAPI implementation.

We have been providing QRNG services as a free, public utility on a lot of chains. QRNG is not a service that is purpose-built to deliver random numbers, but instead uses our request–response protocol (RRP). This means that doing so allowed us to battle-test RRP across a lot of chains in all kinds of use-cases, which validated some of our design decisions and uncovered some user needs that we hadn’t prioritized. We have addressed some of these in v0.10, and will continue addressing them in the upcoming releases. This sets up the stage nicely for the upcoming RRP-based services that we’re planning.

## Self-funded feeds

Publish–subscribe protocol (PSP) was originally designed to allow API3 to signal API provider Airnodes to start updating a particular data feed. byog’s work proved that one doesn’t need the full RRP/PSP, but only the sponsorship scheme of the Airnode protocol. By using the sponsorship scheme and data signed by the Airnode, one can efficiently roll out a very large number of data feeds, and allow users to turn them on and off remotely through controlling the funding of the sponsor wallet that updates the respective data feed. This scheme is exactly trust-miniminized, as it makes it impossible to censor data feed updates without collusion from the API provider.

Accordingly, we decided to postpone the PSP implementation (which is still valuable because it’s a generic protocol that can be used to build a wide variety of services) in favor of building what byog uses to do the above into Airnode. Following this, byog will have API providers set up their own self-funded feeds to act as trust-minimized fallback mechanisms. Note that this has implications beyond the security add; it allows arbitrary aggregated data feeds to be curated permissionlessly, which enables users to self-govern the data feeds they use.

## Service coverage, Omnimarket

There are two services that the core technical team has been working on that had to take a backseat in favor of OEV. The first of these is service coverage, which was introduced in the whitepaper as a comprehensive security mechanism for data feeds. Considering that this will be a service offered to data feed users, we decided that it makes more sense to deliver it after the traction that OEV will provide. Accordingly, the dAPI team moved it to Phase 4 (after OEV), and the core technical team stopped the work on it. That being said, we currently have no unknowns about the implementation, and delivery won’t be an issue once we find the opportunity.

Omnimarket is an unannounced project that addresses some of the issues I’ve raised in [this article](../2022-04-17-commercial-building-blocks). It also complements the upcoming ChainAPI implementation. However, considering the big overlap between the people working on Omnimarket and the people who could have been working on OEV, we froze the development of Omnimarket. This is convenient because Omnimarket depends on the delivery of a ChainAPI proposal that is yet to be made to reach its full potential. While we’re working on OEV, we’ll guide ChainAPI into designing their deliverables for the next proposal to address the needs of Omnimarket.

## Conclusion

The core technical team is now very sparse, and depends on the other technical teams for execution. Accordingly, our job is now mostly coordination and facilitation, and these reports will increasingly touch on what the other teams are doing, and try to [frame them into a meaning](https://bbenligiray.medium.com/what-is-api3-d97fdfe94e19). This shouldn’t be seen as a claim on what the other teams are working on; each team should be given credit for their contributions and supported accordingly through the governance functions.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-march-may-2023.jpeg" caption="Salvador Dali, Exploding Raphaelesque Head, 1951." >}}

# API3 Core Technical Team Report, March–May 2023

[Nodary](https://bbenligiray.medium.com/byog-is-now-nodary-9a571f23caa4) has [introduced self-funded data feeds back in October 2022](https://bbenligiray.medium.com/introducing-byog-b8d5c01d9e82), and these are thoroughly tested and optimized on a large number of chains since then. In March 2023, [the dAPIs team have delivered the Phase 1 of their roadmap](https://medium.com/@ugurmersin/introducing-phase-1-self-funded-dapis-79de730b7521), self-funded dAPIs, which essentially consists of [a market interface](https://market.api3.org/) that greatly streamlines the usage of dAPIs, which are currently pointed to Nodary’s self-funded data feeds. The upcoming Phase 2 enables users to frictionlessly upgrade these entry-level dAPIs to use multiple data sources and not require self-funding.

[Nodary](https://nodary.io/) is an API provider that builds an oracle-centric API, just as API3 builds API provider-centric oracles. In addition to the obvious synergy between these two approaches, this also implies a separation. A good example is Nodary providing self-funded data feeds on both zkSync Era mainnet and testnet (follow the example [here](https://github.com/api3dao/nodary-examples)), yet the API3 Market only providing dAPIs on zkSync Era testnet. This is because the zkSync team hasn’t released their node yet, which means any oracle service on that chain will have to depend on only the public RPC endpoint. If this is satisfactory is subjective — it is for Nodary but not for the dAPIs team of API3.

<div style="text-align: center"> — </div>

The core technical team is done with the development of QRNG, and it is now handed over to the ecosystem team for the [onboarding of new providers](https://x.com/API3DAO/status/1641137174698688512) and [ecosystem building efforts](https://x.com/API3DAO/status/1641093336571445249). The core technical team still collects requirements (e.g., dynamically estimating the gas requirements of fulfillments, higher bandwidth for consecutive requests) and will continue addressing them in upcoming Airnode releases, which will not only benefit QRNG but all RRP services built using Airnode.

We released [Airnode v0.11](https://github.com/api3dao/airnode/releases/tag/v0.11.0) this cycle. Most importantly, this version supports [OEV](../2022-11-01-oracle-extractable-value-oev) and [ChainAPI](https://chainapi.com/)’s current proposal. As the [OEV litepaper](https://github.com/api3dao/oev-litepaper/blob/main/oev-litepaper.pdf) describes, our implementation of OEV includes an OEV Relay, which communicates with Airnodes operated by API providers to create tamper-proof data feed updates to be auctioned off. Therefore, this release pertains to Airnode doing the relevant validations and signing the data in the format that the OEV Relay expects, and is not the complete OEV implementation. That being said, the development of other OEV components is on track and we’ll share updates as necessary.

<div style="text-align: center"> — </div>

API3 has multiple technical teams working on different products, and one thing they have in common is that they require purpose-specific smart contracts to be developed. Core technical team is responsible for the development and/or auditing of all of these contracts, and this cycle was an especially busy one. A total of four audits were completed (one about ChainAPI/Airnode, two about OEV, one about API3 token burns), and the audit reports will be released as the respective products are launched. In addition, we have finalized the payment contract that API3 Market will use to receive payment for the data feed upgrades that will be implemented in Phase 2, as mentioned above.

Finally, there are a few points from the [last cycle’s report](#api3-core-technical-team-report-november-2022february-2023) that I want to amend. It mentioned that ["byog"](https://bbenligiray.medium.com/byog-is-now-nodary-9a571f23caa4) will have API providers run self-funded feeds. While we still find self-funded feeds to be useful to reduce friction in onboarding new users, we decided against utilizing it for multi-source data feeds, at least for the time being. This is also related to [this post](https://bbenligiray.medium.com/byog-is-now-nodary-9a571f23caa4) that hints at byog being rebranded as Nodary also implying a change in direction. In simple terms, we’ll introduce an architecture that we believe will provide trust-minimization in a much more practical way. The second point to amend is that ChainAPI’s next proposal will likely not be about Omnimarket, but this new direction instead. As usual, we’ll share more information once these come to fruition.

<div style="text-align: center"> — </div>

{{< figure src="/2023-08-31-api3-core-technical-team-reports-june-august-2023.jpeg" caption="Pieter Brueghel the Elder, The Harvesters, 1565." >}}

# API3 Core Technical Team Report, June–August 2023

With no doubt, [the most important news of the previous cycle](https://x.com/API3DAO/status/1691804516549902425) was the managed dAPIs being made publicly available on the [API3 Market](https://market.api3.org/). To explain briefly, a [managed dAPI](https://medium.com/api3/introducing-phase-2-managed-dapis-b204670d2545) is a decentralized first-party data feed for which API3 provides the operational guarantees that the client requests. This is a milestone in blockchain technology, as it’s a first for such a high-level, managed service being offered on-demand in such a streamlined and transparent way. The API3 Market clients are not required to join Telegram groups, attend endless calls or [chant "API3 rules, the other thing drools"](https://medium.com/api3/on-exclusivity-deals-and-their-implications-for-ethereum-9354a9ff7929). Clients fill their shopping cart, pay with their crypto wallet and enjoy their data feeds, saving their time and dignity in the process. All payments go to the dAPIs team’s operational gas fund, so this is essentially a gratis service, similar to our [self-funded feeds](https://bbenligiray.medium.com/introducing-byog-b8d5c01d9e82). Monetization will be handled with the upcoming [OEV share](../2022-11-01-oracle-extractable-value-oev), which will be opt-in for managed dAPI clients.

While this is amazing news for up and coming chains and dApp developers, it poses new challenges for the established DeFi projects that are used to depending on privileged access to data feeds as a moat. Specifically, it will be increasingly trivial for developers to fork DeFi apps on newly launched chains and have them operate as reliably as the real thing. Frankly, I have no advice to give here, so we’ll see how it all plays out.

So, managed dAPIs are a huge deal and a very solid foundation for large-scale OEV generation, but let’s talk a bit about what happens behind the curtains. The managed dAPIs launch is obviously a very dAPIs team-thing; it was Phase 2 in their roadmap (Phase 1 being self-funded feeds and Phase 3 being OEV share). The story of a managed dAPI starts with business development though, where suitable API providers are signed on as partners by the BD team. You can see them all on API3 Market, and [verify yourself that it’s actually them that are providing the service](https://medium.com/@ugurmersin/chainlink-price-feeds-vs-api3-managed-dapis-and-the-state-of-defi-227ac1f56a18), which is again, a first. [Nodary](https://bbenligiray.medium.com/byog-is-now-nodary-9a571f23caa4) integrates them and starts monitoring their data (which never stops from this point) to determine what dAPIs they would be viable for. Each dAPI is curated continuously to uphold our security standards, which is why we call it managed after all.

<div style="text-align: center"> — </div>

As promised in the [previous report](#api3-core-technical-team-report-marchmay-2023), we have released [Airnode v0.12](https://github.com/api3dao/airnode/releases/tag/v0.12.0) with a few, long-awaited features. Most importantly, Airnode operators can now omit the fulfillment gas limit in their config files, which will cause the Airnode to estimate the required gas limit at run-time with RPC calls. For example, one will be able to request a large number of random numbers from QRNG and mint an NFT with each in the fulfillment transaction, as long as their sponsor wallet is funded to be able to do so.

<div style="text-align: center"> — </div>

If you’re up to date with your API3 governance, you should have noticed that two additional teams have spun-off from the core technical team at the end of this cycle: the UX/UI team and the independent monitoring team. I’ve been continuously encouraging people to spin-off from CTT to create teams to work toward a more specific goal in a more autonomous way, which inevitably left CTT with a group of people for which spinning off doesn’t make sense but also they are not specifically cohesive. To address this issue, CTT will be wound down. I will post a closing financial report on the forum, the multisig will return the remainder of the funds to the DAO, and I won’t give a CTT proposal for the next cycle. This dovetails perfectly into the restructuring of the other DAO teams (which you should be able to read about on the forum soon), and the current CTT members will be swallowed by this new structure (including me).
