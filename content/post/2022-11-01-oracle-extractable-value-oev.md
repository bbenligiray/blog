+++
title = 'Oracle Extractable Value (OEV)'
date = '2022-11-01'
description = 'November 2022'
summary = "November 2022"
featured_image = '/2022-11-01-oracle-extractable-value-oev-upscaled.jpg'
images = ['/2022-11-01-oracle-extractable-value-oev-upscaled.jpg']
tags = ['API3']
+++

Oracle extractable value (OEV) refers to oracles making use of their position to capture value that would otherwise have gone to third parties.
As a simple example, say we have an ETH/USD price data feed with the value of 1000 and the deviation threshold of 1% (meaning that the value after the next update will be 990 or 1010.)
A user has a position that can be liquidated when the data feed value is at least 1005, and ETH/USD price is increasing.
In the traditional case, the oracles will wait until the underlying APIs return 1010 to update the data feed value to 1010.
Then, it’s a race between third parties to liquidate the user and net the reward.
With OEV, the data feed gets updated as soon as the underlying APIs return 1005 and the user gets liquidated in the same transaction to claim the reward.
Oracles can either extract the OEV themselves, or auction off the right to extract the OEV, which results in an equivalent financial outcome for them.

OEV is a concept that is as old as oracles themselves, but important developments have taken place since it was being entertained as a theoretical inevitability.
The traditional way of getting a piece of the [MEV](https://ethereum.org/en/developers/docs/mev/) pie used to be getting into gas wars with other third parties.
Over the last year, Flashbots proved that taking this process off-chain is possible in practice, [extracting more than $650M to date](https://explore.flashbots.net/).
It’s even [argued](https://blog.bitmex.com/flashbots/) that this may be one of the reasons why Ethereum gas fees don’t spike as hard during market volatility.
This demonstrates that as long as there is a trustlessly-available mechanism to fall back on, adding more efficient value extraction mechanisms is feasible, and can benefit all stakeholders.

Before moving on, let us note that intentionally degrading the advertised oracle service specs (by [delaying updates](https://vitalik.eth.limo/general/2022/09/20/daos.html) or [flat-out misreporting](https://x.com/haydenzadams/status/1377431421573234689)) is an oracle attack and not a method of value extraction, which implicitly needs to be sustainable.
At API3, we don’t only advertise specs, but also provide trustless security guarantees through the retrospective, insurance-like service coverage arbitrated by a decentralized third party, which means users of our data feeds are protected from all kinds of oracle attacks.
Furthermore, the added OEV functionality does not make our data feeds any less secure or insurable, as we retain the traditional, decentralized first-party data feed—a trust-minimized architecture—to automatically fall back on.

## Why is there an OEV in the first place?

When people think of oracles, they usually think of data feeds, i.e., live data points on a chain, always ready to be used.
Unfortunately, the only thing certain about a live data feed is that it is outdated (compared to the underlying APIs), if only by milliseconds.
This issue allows arbitrage, frontrunning and various other kinds of value extraction, all paid for by the dApps that use them.
The only immediate solution here is to update the data feeds as frequently as possible, yet the cost of doing so still has to be passed on to someone, and this also makes it difficult to justify providing a large number of data feeds due to the associated gas costs, which impedes innovation.

Now imagine an oracle service that does not store the data that will be used by third parties to change the state, but instead changes the state directly.
If we go back to our liquidation example, the oracles would not need to periodically update any data feeds, and simply liquidate positions as needed.
The dApp wouldn’t need to reward the oracles for this, as this is what one pays for when they’re buying an oracle service.
(As a note, this doesn’t eliminate second-order OEV, e.g., due to cascading liquidations.)

Although our Airnode request–response and publish–subscribe protocols are designed to allow these kinds of novel oracle services to be built, we’re aware that data feeds are not going anywhere soon, and our [dAPIs](https://medium.com/api3/dapis-apis-for-dapps-53b83f8d2493) primarily cater to DeFi projects that require traditional data feeds for this exact reason.
This section is just to clarify that OEV is an unwanted side-effect of legacy-DeFi and fundamental limitations of blockchains in general.

## What to do with OEV?

OEV is DeFi projects bleeding money due to being architected around a suboptimal oracle solution (which, to be fair, is the only one that is readily available.)
Therefore, capturing OEV does not generate more value than picking up the wallet that someone has dropped.
Then, it is obvious what needs to be done with the OEV proceeds. **API3 will extract the OEV, and return it to the dApps.**

OEV is more than oracles having primary rights to MEV.
Let us consider the liquidation example again.
The traditional approach also ends up liquidating the position, but only if ETH/USD price ends up reaching 1010.
But what if the ETH/USD price goes up to 1009, and then goes back down without reaching 1010?
Then, the traditional data feed would not have updated, and the position would not have been liquidated even though it should have.
This is a common occurrence with deviation threshold-based data feeds, and causes significant losses to the dApps that use them.

OEV-based updates benefit the dApp financially even without the dApp receiving the proceeds.
Traditionally, the quality of a data feed is measured by its deviation threshold, where smaller values are better because they result in fewer events such as the example above.
OEV-based updates make this metric obsolete by updating precisely when needed, achieving zero deviation threshold in practice.
Note that OEV-based and deviation threshold-based updates work well together to deliver the best of both worlds because in the context of data feeds, all updates are good updates.

## How does it work?

API3 runs an API that announces data feed updates that can be bid on (imagine 100+ data feeds each on 10+ chains, including Ethereum, Polygon, Arbitrum, Optimism, BNB Chain, Avalanche, Fantom, Gnosis Chain, Moonbeam, Moonriver, Milkomeda, Metis, RSK and more).
Searchers (bots that are programmed to automatically extract MEV) periodically check on these to see if there is an update that can be used to extract any value.
When there is such an update, searchers bid an amount in the native currency of the chain.
The winner of the auction is presented with a meta-transaction that is cryptographically-signed by each API provider that powers the specific dAPI, **which can only be used by the winner of the auction, if they send the bid amount that won the auction along with the meta-transaction**.
Then, the winner of the auction can push the meta-transaction to the chain to update the dAPI, and trigger any additional events in the same transaction, which will guarantee them all the rewards.
(Since the update will be signed to be executed by a specific searcher, it will be compatible with any block production and validation scheme—for example, it doesn’t require a private mempool.)
The auction proceeds accumulate in a dApp-specific contract, withdrawable by the respective account.

More competitive auctions will result in more efficient value extraction, which will be achieved by making them publicly accessible to all searchers.
A staking-based security mechanism will be used for newly onboarded participants to disincentivize denial attacks, which will dynamically shift to a reputation-based system to ensure capital efficiency.
This auction layer is particularly suitable for monetization by first-party oracles (i.e., API providers), as it’s essentially a Web service provided to searchers.

The system will also be publicly accessible to all dApps—in that any dApp that uses any data feed on any chain will be able to open their usage to OEV extraction in a practically permissionless way by following the instructions, and withdraw the proceeds by interacting with a trustless contract.

## Conclusion

Traditional oracle solutions update data feeds blindly, which is wasteful and provides poor granularity.
OEV extraction updates data feeds exactly when needed, which results in cheap and maximally accurate data feeds.
Furthermore, the OEV update transactions can be offloaded to third-parties, making it financially feasible to operate a wide variety of data feeds.

dApps typically offer some MEV to facilitate the automatic triggering of events—for example, liquidating positions should be rewarded for third parties to liquidate positions.
This amount is difficult to minimize without jeopardizing the service, which causes dApps to overpay.
In addition, there are cases where dApps leak MEV without any benefit to themselves.
Extracting OEV maximally through a publicly competitive auction and returning the proceeds to dApps resolves these issues, and provides dApps with a novel and very significant source of revenue.
