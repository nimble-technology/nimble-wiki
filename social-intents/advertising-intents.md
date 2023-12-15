---
description: An overview of Intent-based advertising
---

# Advertising Intents

We've all become familiar with Intents from their DeFi applications. In that domain, protocols position Intents as a solution to the MEV and usability crises in Web3.

Nimble believes intents should and must transcend DeFi if we are to drive adoption from mainstream internet users. Improved experiences cannot be restricted to the world of trading.

This article focuses on how intent-based architecture can be applied to advertising.

### The Attention Marketplace

Nimble is building a generic marketplace infrastructure to democratize the exchange of value. But what does that **really** mean? Let's back up.

Today's largest tech platforms are marketplaces for attention. Users are attracted by features (search, entertainment, etc), and their attention is sold to advertisers. In this system, the infrastructure connecting users to their desired outcome is centralized and monopolistic.

The attention marketplace inverts this equation.

<figure><img src="../.gitbook/assets/Slide 16_10 - 90 (1).png" alt=""><figcaption><p>Advertising intent architecture on Nimble's Marketplace of Intents</p></figcaption></figure>

Advertisers access the marketplace by submitting advertising intents. In this system, advertisers represent the **intent supply**.

Their intent specifies:

* Budget
* Desired topics
* Desired reach
* Variable to optimize for (clicks, views, conversions, etc)

Nimble operates a multi-stage batch auction to solve the advertiser's intent.

### Targeting Auction

To ensure the ad reaches the desired destination, solvers compete in a targeting auction to identify appropriate ad recipients based on on-chain historical data. Participants at this level can be AI models or heuristics.

Ad targeting is analogous to the systems used by centralized platforms to decide which ads you see. One critical difference is the degree of transparency and control provided to users to decide which of their data is leveraged in such auctions.

Targeting solvers leverage on-chain data related to potential ad targets and propose a set of recipients. Reputations are maintained for each solver to indicate their historical performance (CTR, views, etc), and more precise targeting solvers can charge higher fees.

### Advertising Auction

The advertising auction begins with a set of potential recipients from the targeting auction. Each recipient is a solver in the advertising auction. They bid to receive the ad.

The quality of their bid is a combination of the fee they are willing to receive and the quality of their match, as determined by the advertising auction.

At the close of the advertising auction, recipients are selected to receive the advertisement and the fee allocated to them.

### Wrapping up

Advertising intents will be one of the first social intents supported on Nimble. This architecture enables a fairer distribution of resources between advertiser and recipient and brings us one step closer to achieving our vision of democratizing the exchange of value.
