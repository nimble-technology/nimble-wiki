---
description: Let's get intentional
---

# Testnet Overview

Today, we’re excited to announce the launch of the Nimble intent protocol on [Goerli testnet](https://goerli.etherscan.io/address/0x0C414bA7B5805c2e21Df1fc8507815eebfD5d6fB).

At launch, this SDK includes support for swap and transfer intents. This small launch marks the first step towards creating the marketplace of intents in pursuit of our mission of decentralizing Silicon Valley.

To jump straight in and start coding, check out the [quick start guide](https://docs.nimble.technology/sdk/quickstart).

Today’s tech monopolies extract revenue from our online lives. They profit from mediating our exchanges with one another. By enabling seamless, direct transfer of value between community participants, swap and transfer intents will serve as the foundation for the marketplace of intents.

But this is only the beginning. In the coming weeks, incremental launches will bring this vision into clear view.

Our approach has four phases:

0\. Base protocol launch **<- we are here**

1\. Seed our infrastructure by building the first generation of intent-based dApps

2\. Expand our infrastructure with community-driven marketplace intents

3\. Public release and open-sourcing

<figure><img src="https://lh7-us.googleusercontent.com/ZcilTN1b1_qelCQhvN7bGtdh3Z19vITr8ZQ6OKQgCRPiccgAbuFk_W7a1_CwiVOA1EvTZVg0Hl6zfTTLMUuuBQxw-OEWckmAkEU3hKYgnFGIvjPjhFIKulY2GlfTba-qIAU_l77PUZSAnK6m0R9mZX0" alt=""><figcaption></figcaption></figure>

### Background

Usability challenges are one of the main obstacles to mass adoption of Web3.

To perform basic operations on today’s blockchains, users describe the exact sequence of steps (transactions) needed to achieve their desired outcome. This represents significant overhead for both new and experienced users alike.

In this document, we describe the implementation of Nimble’s intent protocol. Developers can craft intents through this SDK, describing acceptable outcomes for token transfers and swaps. The protocol will determine the correct series of transactions needed to achieve the outcome and execute them on-chain.

It stands out by its ability to not only interpret user intents—such as transferring assets between Bitcoin and Ethereum—but also to intelligently bundle these intents with corresponding orders. It goes further by algorithmically determining the most optimized solutions for these bundled intents and efficiently managing their execution. The following is a detailed guide concept and development of this SDK.

### Intent Basics

**Intent**

In this SDK, Intents include two components:

1. The assets they would like to release
2. The results they require to achieve

Both EOA and account abstraction (AA) wallets are supported.

#### GeneralAsset

The SDK is designed to support a GeneralAsset type. This type represents various blockchain assets (like ETH, ERC20, ERC721, ERC1155 tokens).&#x20;

#### Solver & Solution

The solver provides the solution to the user intent. It plays the role of the bundler in EIP-4337. Whenever the solver receives the intent from a user, it may generate additional intents bundled with the user intent as a solution. This bundle is then submitted to the on-chain contract.

### Examples

#### Swap and Transfer

Alex intends to release 100 USDC, and he wants David to get 20 USDC, Julia BTC of 50 USDC, and Anthony 10 DAI.

The solution to Alex’s intent would include 1 transfer intent and 1 swap intent:

1. Transfer intent:&#x20;
   1. Transfer 20 USDC from Alex to David
2. Swap intent
   1. Swap 50 USDC for BTC to Julia
   2. Swap 10 USDC for DAI to Anthony

#### Multi-swap

Bob intends to invest in a portfolio: release 1000 USDC, 60% to BTC, 20% to ETH, and 20% to Solana.

The corresponding solution would include one swap intent:

1. Swap 600 USDC for BTC
2. Swap 200 USDC for ETH
3. Swap 200 USDC for Solana

### The Design

<figure><img src="https://lh7-us.googleusercontent.com/M43vPw-y1KUhu_wSU2m2RldSpVps9o2HlnlaYga-gKSITOPWRk_bw4967DzDSIxVx5687sS_m5TPZPYO6FQaofpg9c8FRX6dxUZjgGZdFAsMWBN3iBscwI-2mXMwohL3x3UTsMUEiLOucUGQmxoSsq0" alt=""><figcaption></figcaption></figure>

### Core Components

#### **Entry Point**

Intents are submitted to the network via the entry point.

This component manages intent handlers by performing the following functions:

1. Register/deregister handlers.
2. Call intent handlers per the handler field, defined in the intent data structure.
3. Validate intents before solution processing.
4. Ensure user requirements are met after solution processing.

#### **Intent Handlers**

Intent handlers define the data format for each intent operation they support. The entry point operates independently from the intent handlers and does not depend on them in any way.

Use the handler ID field to select which intent handler processes an operation.

### Workflow

<figure><img src="https://lh7-us.googleusercontent.com/vKhb38EC44YwpTi6Ezf8qd3cmDXroz4OLiB5IICMBiPVQw4zkEeJ8GKimWRjphT9rEsQ29LJNj4POgLRgSlZEIiHVVJBOYmi9T5pqDdn7b-nX-1G1nEEXlAdX1HUSmatqNqMa2rAuyFEAVro0DPfphY" alt=""><figcaption></figcaption></figure>

#### 1. Create

Structure your intent by completing the required fields in the intent DSL.

Intents can be created directly using a text editor or built into an application and executed via a common interactive element like forms or buttons.&#x20;

#### 2. Submit

Submit your structured intent to our API server.

#### 3. Resolve

The solver will construct a solution that resolves the user’s intent.

#### 4. Validate

The solver will submit its solution to our on-chain Entry Point contract for validation.

#### 5. Route

The Entry Point contract will route the intent data in the solution to different handlers per the solution definition. If this is the final step in the intent, it will be executed on chain.

### Conclusion

This developer SDK is the first step to gather users’ intents for intentional dApp design and development. The team is working hard to bring these SDKs to mainnet and expand the intent network to support additional operations.

Twitter: [https://twitter.com/Nimble\_Network/](https://twitter.com/Nimble\_Network/)

Discord: [https://discord.gg/P8UhBKqAse](https://discord.gg/P8UhBKqAse)
