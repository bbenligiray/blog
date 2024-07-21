+++
title = 'dAPIs: APIs for dApps'
date = '2022-03-31'
description = 'March 2022'
summary = "March 2022"
featured_image = '/2022-31-05-dapis-apis-for-dapps-cropped-upscaled.jpg'
images = ['/2022-31-05-dapis-apis-for-dapps-cropped-upscaled.jpg']
featured_image_caption = 'Utagawa Yoshitora, Picture of the Twelve Animals to Protect the Safety of the Home, Edo Period.'
tags = ['API3']
+++

As discussed in the [whitepaper](https://raw.githubusercontent.com/api3dao/api3-whitepaper/master/api3-whitepaper.pdf), the goal of API3 is to "build, manage and monetize dAPIs at scale".
In this regard, all of the development that we’ve been doing is because the existing tools fall short of being able to support dAPIs as we envision them.
What exactly are these dAPIs then?

A dApp is an application that is implemented as a smart contract that runs on a decentralized blockchain.
By the same token, a dAPI is an API-like service that is delivered to smart contracts.
In simpler terms, just as applications use APIs, dApps will use dAPIs.

dAPIs are designed to resemble APIs from the user perspective:

- The relationship with the user is transactional.
The user pays according to a transparent pricing model to receive a well-specified service, no blood pact required.
- It has a standardized, user-friendly interface that intends to abstract the technical implementation away.
- It is a [managed service](https://en.wikipedia.org/wiki/Managed_services), in that the operational complexities are abstracted away.
The only responsibility that the user has is to not miss the payments.

In addition to the above, dAPIs are quantifiably secure by virtue of being covered against losses due to malfunctions (though even this can be compared to API [SLAs](https://en.wikipedia.org/wiki/Service-level_agreement)).
Here, the first-partyness or the API-level decentralization of the dAPI strictly serves as a tool to optimize the insurance risk.
Furthermore, a dAPI is not necessarily a live data feed, but rather represents an even more general kind of an oracle service.

<div style="text-align: center"> — </div>

After this general definition, let us investigate the first generation of dAPIs that we will build, and how they relate to [Beacons](https://medium.com/api3/beacons-building-blocks-for-web3-data-connectivity-df6ad3eb5763).
As presented in the [recent ETHDenver talk](https://www.youtube.com/watch?t=1364&v=94tqEQgTwVg&feature=youtu.be), our solutions are designed as a hierarchy:

- The lowest level is composed of the Airnode protocols (RRP, PSP, relayed RRP, relayed PSP, API-signed data).
A user that is [authorized](https://medium.com/api3/api3dao-development-update-march-2021-7cae9265fdd3) is allowed to make requests to the respective Airnode at the protocol level.
The [Kassandra/Heimdall use-case](https://medium.com/api3/airnode-is-live-on-avalanche-mainnet-powering-kassandras-avalanche-social-index-fdcc963642f) can be given as an example of this kind of usage.
Typically, implementing such use-cases requires a strong understanding of the Airnode protocol.
- The intermediate level is composed of oracle primitives such as Beacons.
The [Amberdata Beacons built for ETHDenver](https://medium.com/api3/announcing-amberdata-beacons-powering-defi-at-ethdenver-330a4084c1b5) is a good example of this.
Although Beacons are built on top of Airnode protocols, this fact is abstracted away from the user, meaning that they don’t need to know anything about the specific Airnode protocol that is powering the Beacon they are using.
- The highest level solutions we will build are dAPIs.
In the live data feed use-case, a dAPI is either a Beacon or a set of Beacons that is wrapped by a higher-level interface.
In other words, by using a dAPI, the user offloads the responsibility of curating the individual Beacons in a data feed.

The goal of this modular architecture is to allow the user to pick the most suitable tool for the job.
If one needs a turnkey, set-and-forget oracle solution, they should use a dAPI.
If they want full control over the data sources, they should use one or a set of Beacons.
If the solution they need is very niche, it can be built directly on top of the Airnode protocol.
Access control and monetization mechanisms are implemented at each of these levels, meaning that an API provider can realistically productize their services to cover this entire spectrum.

<div style="text-align: center"> — </div>

Since the majority of the readers will be familiar with Beacons, let us compare the user flow of dAPIs to these for further clarification.
A Beacon is addressed by an ID, which is derived from the respective Airnode address and request parameters.
This means that the Beacon with ID `0x49e8...021b` will always be the BTC/USD price reported by Amberdata.
Similarly, Beacon sets are addressed by the hash of the list of Beacon IDs that comprise them, which means a Beacon set ID will always refer to a specific combination of Beacons.
This is great because it allows the user to specify the exact data sources down to the request parameters, which eliminates any possibility of API3-side errors—which may [transmute silver into gold](https://blockonomi.com/chainlink-pricing-anomaly/) for example—and allows API3 to feasibly serve a project that has x100 of its marketcap.
This is not so great because the user will require a robust decentralized governance mechanism that can pick the specific Beacons to be used and update them when necessary, which is typically not applicable to projects that are not well-established.

Here, dAPIs come into play.
A dAPI is essentially a name, mapped to a Beacon ID or a Beacon set ID.
The user addresses the dAPI by its name, and the contract routes this to the respective Beacon or Beacon set.
The API3 core technical team will have multisigs on all chains that API3 serves on, which will make the expert decisions to uphold the security guarantees given by the coverage policies.
Once this process has matured, the dAPI management will be transferred to individual, chain-native DAOs as described in our [fractal scaling](https://medium.com/api3/fractal-scaling-of-api3-b3ba78c9dcb7) plan.
It’s not critically important to the user who does the dAPI management, as they will be insured against governance accidents, no matter who caused them.
Therefore, any risks caused by the dAPI management scheme is considered to be a part of the insurance risk, and is the responsibility of the API3 DAO to manage.

{{< figure src="/2022-31-05-dapis-apis-for-dapps-fig.png" caption="Figure 6 from the whitepaper that depicts dAPI managing entities on individual chains." >}}

We’re fast approaching delivering on API3’s reason for existence, dAPIs, which makes us proud.
However, as the whitepaper quote goes, the goal is also to do this "at scale", which means creating a dAPI economy that is comparable to Web3 as a whole.
Our solutions are designed to work around bottlenecks that may limit ecosystem growth, so the way to achieve this will simply be doing more of what we’ve been doing and allow the Web3 space to catch up.
