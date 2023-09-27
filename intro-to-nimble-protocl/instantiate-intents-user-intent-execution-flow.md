---
description: >-
  The intent standard can be generalized to any chains. EVM is used as an
  example for the standard implementation and user intent flow illustration.
---

# Instantiate Intents - User Intent Execution Flow

<figure><img src="https://lh5.googleusercontent.com/tuSl0z32ZxGJNyl6nQQLMJ6JeCQ8iyJw_vSPT0OJu05ptcnVh4-zVO_-ThUTdjSoxttND4aWPjPPCZWM5B2ZLiMEZzhPxVFc2qPLiKzldS9U5ODotKUp2C_bQe-doRc84jbpMwIi8M97iBe1TeKAtqA" alt=""><figcaption></figcaption></figure>

## User Intent Flow

A user intent is a signed request in any format. It goes through the following modules or components before being executed onchain with the Nimble intent contract:

* Intent Parser: intents first arrive at the intent parser which performs the intent understanding functionalities. It first understands the intent with LLMs and rule engine by mapping it to a specific operation onchain. Then, the mapped operation is formatted to a standard data payload as defined by the intent DSL. This payload is serialized into the intent pool.
* Intent Pool: Intents in the pool are short lived intents with a TTL. They are fetched by auction service periodically. Solvers compete for profitable intents through auctions and thus the profit margins (i.e., MEV) are minimized. If fulfilled by solvers or the TTL expires, they will be removed from the pool.
* Dispatcher: The dispatching module is to fetch intents from the intent pool and dispatch them to different auctions running in the auction protocols. Swap, aggregation, stake and transfer operations form separate auctions and even different groups of solvers can form separate auctions given the particular settings.
* Auction Protocol: 2nd price auction is adopted to reveal truthful bids for the intents. It is widely adopted in Ads systems for its practicality. The intents are listened by solvers with a pull based approach.
* Solvers: Solvers are heterogeneous agents with different expertises and capacities. They filter and decide which intents to send a bid. Bids are calculated with their own algorithms. Standard algorithms are provided in Nimble SDKs as well.

The intents are executed by interacting with the intent contract which is illustrated below.

## Nimble Intent Contracts

<figure><img src="https://lh4.googleusercontent.com/uT_LTl9gvHQhh8pIMHp3ytKaHMAzQ3r8Nw7QlEP22KhISNAU6G96P4dsSkNFfArNKZVWoY16i2VerYiwfjMc7C_roQrDO9uGOX2Io41SwnGPPvTizSLFfPtkPjthLY6ANlRnv0nvLy7AaIuZN3BgP-g" alt=""><figcaption></figcaption></figure>

User intent classes, execution, dispatching, validation and error handling are key components of the intent contract. We focus our discussions on the intent class, execution and dispatching, since validation and error handling come naturally.

The UserIntents class defines intents through the taxonomy. It also consists of important intent utility functions. The IntentDispatcher is the unified interface for solvers to interact with and it routes intents to specialized IntentExecutor. IntentExecutor class handles particular intent operation executions. Intents are validated before being sent to the IntentDispatcher. ErrorHandler is called by different components whenever errors are detected.

The following diagram provides a more detailed illustration of the key contract logic:

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



\
