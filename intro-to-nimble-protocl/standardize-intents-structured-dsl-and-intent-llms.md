---
description: Introducing the Nimble Intent Protocol
---

# What are Intents?

It was a challenging year for Web3. With a consistent stream of bad news, the adoption of blockchain technology has slowed. To end “crypto winter”, our industry needs growth.

For Web3 companies, this growth can’t come from within. Out of the over 26 million global software developers, just over 26 thousand develop for blockchain. Of 5.3 billion people with internet access, just over 420 million own cryptocurrency. For context, Roblox alone has over 9.5 million developers.

<figure><img src="https://lh6.googleusercontent.com/T5ey3Rg3DoJLV_BBq6xwrYkdcI0myGiExoSHm1qqJ3sQBa-uiRhHi0fjQ8D5Kx6NzPyMLjAo4r5yvdwEPPxfYR1o5Ld0TPxenSZ89WI4AT9Ueu1n7kmIvgRQtWrW31cvJgOKtfOUL3gVP8V7HMqpLoE" alt=""><figcaption></figcaption></figure>

Despite this, most startups in this space focus on winning developers and users from these small sets. As a community, we compete for a slice of a shrinking pie instead of expanding it.

Let’s direct our attention to the nearly 4.9 billion people worldwide with internet access who have chosen not to adopt Web3. The most common reasons cited are:

1. Education. Users must understand many novel technical concepts to use crypto. Terms like wallets, private keys, bridges, and DEX are hard to grasp for new users.
2. Usability. Outside of centralized platforms, operations on blockchains are relatively low-level. Users must sign transactions individually and understand the steps required to accomplish their desired task.

### The Usability Crisis

Let me illustrate the extent of this problem with an example. Let’s say you just heard about Friend.tech, an interesting new social networking dapp that uses BASE for in-app transactions. Funding your wallet with ETH requires you to:

1. Update your wallet. Use Chainlink to add the BASE RPC to your wallet.
2. Bridge. Use the BASE bridge to send your ETH to the BASE network.
3. Update network. Select the BASE network in your wallet.
4. Fund. Send BASE to your dapp wallet.

Would your grandparents have signed up if Facebook required users to understand these technical topics?

Web2 companies appeal to an incredible audience by hiding complexity. Users are allowed to live in a world of their desired outcomes.

* Create an account
* Post a photo
* Play a video

The future growth of Web3 depends on our ability to match this level of simplicity. To help get there, we’re introducing the Nimble intent protocol - an easier way to interact with blockchains.

#### What is an Intent Protocol?

Intent protocols let users achieve their desired outcomes without understanding the computational steps needed. They are declarative, meaning you state what you want, and the protocol determines how to achieve it.

Contrast this with today’s imperative protocols, where users describe the specific steps to achieve an outcome. Imperative systems deal with transactions. Transactions are specific computational steps signed by a wallet and executed on a blockchain. Many transactions may be required to achieve a single outcome for a user.

In both cases, the user gets what they want. But with intent protocols, they don’t need to know how it happened. The user is satisfied as long as the terms of the intent are honored.

Return to the earlier example where we funded a Friend.tech wallet using ETH. With an intent protocol, there is just one step: State your desired outcome:

> “Fund my friend.tech wallet with $15 worth of ETH from my wallet”.

The protocol interprets the user’s intent and then converts it into a set of transactions on the blockchain. Transactions are executed on the user’s behalf, achieving their desired outcome without needing them to understand the technical details.

<figure><img src="https://lh3.googleusercontent.com/PHIh13wNnPLRl3a0k1pe5v5155pgK_QxbgpL_1oOQuYxa0DkkNOm7RwSjF4QXWWQRwaSsjmEyDp-6bBRxPXZJ2rcoJfFo32Q3xpAXXdDorFpQgIJ-ntKyhSHNNSztlN0om7xq0I08O7IotFcs_81OdI" alt=""><figcaption></figcaption></figure>

#### Intents versus Transactions

Here’s a helpful analogy to help solidify the difference between intents and transactions. Let’s say it’s your partner’s birthday, and you must get them a cake for their party. The cake must:

1. Be double chocolate - their favorite flavor
2. Feed at least 12
3. Be dairy-free

#### Using Transactions

Based on these preferences, you may opt to bake the cake yourself. You find a recipe, buy the ingredients, and combine each ingredient in the correct order. You need to understand and handle every step of the baking process, but you can be sure to get the right cake.

#### Using Intents

You may also choose to purchase the correct cake from a bakery. You travel to the bakery, state your preferences, and receive a cake precisely as ordered. In this way, the bakery obscured the process of baking a cake from you.

Your partner gets the right cake in each case, but picking it up from the bakery is much easier.

#### How it works

<figure><img src="https://lh5.googleusercontent.com/H4-p1CIE-5dCNcBhc_xIuO5Kdwwzo4yrKllwNrriBEEZ97fvND3jG7Av9VcY-9303Lu-RTp5lSIOJTpmNO-xoqyf3BSSXoPh98dqij_RzrPsMoqI9eHjjZfx07wVBomF_zSZ7O03bMUMdeChUOwADY4" alt=""><figcaption></figcaption></figure>

Our intent protocol accepts intents and translates them into valid computational steps. If the Intent involves a trade, the protocol must also find a counterparty willing to take the trade.

Let’s walk through the process of fulfilling an Intent in more detail.

#### Entering the Network

Intent fulfillment begins with the user submitting an intent to our Intent Recognizer.&#x20;

Since intents may require more than one transaction, they must be signed using an Account Abstraction (EIP-4337) wallet. The user’s goals, enshrined by the Intent, are described in the smart contract authorization.

Once authorized, Nimble submits the Intent to the Intent Pool.

#### Finding Solutions

The dispatcher forwards signed Intents to a Request for Quote (RFQ) model, which attempts to match the user’s desired outcome with an available service or contract. At this stage in the pipeline, the protocol translates the intent into machine-readable transactions.

The critical component of this step is the Solvers. Solvers provide the Nimble network with solutions that satisfy a user’s desired outcome, in whole or in part. Solvers make the functionality of third-party systems available on Nimble and make Nimble’s user base accessible to dapps. We will provide an open SDK for developers to create their own Solver and benefit from Nimble’s user base.

Native solvers are also used to match users directly within the network. When two or more users within Nimble execute both sides of the same transaction, the transaction completes directly. Such on-network transactions eliminate costs associated with transiting third-party networks.

#### Request for Quote (RFQ) Model

In the RFQ model, solvers compete to provide the lowest-cost solution that satisfies their assigned portion of the Intent. In this way, an incentive is placed on solvers to deliver solutions at the lowest possible price.

The costs associated with operations like bridging and swapping can significantly benefit from a diversified pool of solvers.

#### Domain-specific language

To standardize communication between participants in the RFQ model and solvers, we are building a domain-specific language (DSL) for the expression of intents. Solvers must leverage the DSL to identify solutions within their system.

We know other intent-based projects are also working on domain-specific languages and will choose to leverage a standard if one becomes available.

#### Intent Translation

For Solvers to interpret intents, the protocol must translate them into parsable DSL. Nimble leverages a rules engine coupled to a Large Language Model (LLM) to perform this translation. Simple intents may match directly to rules in the rules engine, while our AI language model processes more complex Intents.

#### Solver Network

The power of an intent-centric protocol lies in its network of solvers. A rich network of solvers lowers costs for users and enables functionality to support the fulfillment of more complex outcomes.

Nimble is built on a modular architecture to facilitate the expansion of our solver network. Dapps can quickly build a solver to lower the barrier of entry to using their project and gain access to Nimble’s user base.

Creating a Solver for Nimble benefits dapps in all categories:

#### Exchanges

Exchanges can source order flow from Nimble’s user network, receiving fees for the component of Intents satisfied by their service.

Once a sufficient number of exchange Solvers exist on Nimble, no specialized interface will be needed. Users can submit their intents directly to the Network, which can match DeFi steps with available exchanges.&#x20;

The network of Dispatchers and Solvers will automatically select the series of transactions that result in the lowest fees to the user. The exchange operations are rendered completely transparent to the user.

#### Dapps

Dapps can significantly simplify their onboarding experience with a Nimble Solver.

These experiences require the users to have a native token. Nimble can perform bridging, swaps, and trades in a single step, significantly lowering the friction of creating and funding an account.

Your users will spend more time in your application and less time frustrated by learning blockchain fundamentals.

#### SocialFi

Traditional platforms take advantage of content creators by retaining ownership of audiences. If the content creator leaves the platform, they’ll lose access to the audience they may have spent a significant effort to create.

SocialFi apps can leverage Nimble to grow and monetize their audience. By creating a Solver that matches users with relevant content creators, Nimble can act as a discovery layer for users to find content creators based on their interests

On Web2, users are used to ad-supported content and may be opposed to paying to access content online. Advertising can create Solvers to fund views of ad-supported content by paying network fees and directly compensating content creators.

#### Vision

Nimble aims to unlock the utility of Web3 by building the first marketplace for intents. Our protocol will provide an open and inclusive market for participants to compete to optimize outcomes instead of maximizing extracted value.

In the same way that Google made the world’s data accessible to all, Nimble aims to democratize the exchange of value.
