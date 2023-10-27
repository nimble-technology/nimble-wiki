---
description: The 6 innovations enabling Nimble to decentralize the Silicon Valley
---

# Key Innovations

Nimble was conceived in 2023 when its founding team sought a way for a decentralized network of nodes to orchestrate a trustless marketplace infrastructure for everything. None of the major decentralized networks, including blockchains, achieve this property. Accomplishing this is Nimble’s North Star.

Blockchains like Ethereum, Solana, Aptos, BNB, Avalanche, Cosmos, Sei, and Injective scale the network transactions with Byzantine Fault Tolerance-based Proof of Stake (PoS) systems. The most important internet applications are still not supported by today’s blockchains to achieve the Web3 vision: Web3 is the internet owned by the builders and users, orchestrated with tokens. Nimble, an intent-centric decentralized network, supports general-purpose intents and everything marketplace applications, making it the most general-purpose decentralized infrastructure for Internet applications.

The Nimble team has successfully built sophisticated tech solutions, products, and platforms that have been used by billions of people worldwide. Since its inception, the team — consisting of serial entrepreneurs and established researchers from Meta, Uber, Palo Alto Networks, and Yale — has focused on building the tech to realize the ultimate Web3 internet being owned by the builders and users.

To create a decentralized, permissionless network that enables any Internet application, the Nimble team developed 6 key technologies:

* Proof of Intent - the Intent Version of PoS;
* Sandhill - Intent Action Recognition Protocol;
* Rainstorm - Horizontally-Scaled Dispatching Network;
* Orchestrator - Modular Incentives for the Everything Marketplace;
* Bandwagon - General Purpose Intent Database;
* HashTrail - Distributed Intent Ledger

In this essay, we’ll briefly explain each of the above. If you’d like to learn more about each, we’ve also written detailed explainers that you can access by clicking the links above.

## Proof of Intent - the Intent Version of PoS

Today’s internet is an everything marketplace of user intents, matching them with content, products, advertisers, drivers, house owners, and restaurants. Users express themselves explicitly with natural language queries in search, likes in recommendation, rides in ride-hailing apps, purchases in e-commerce websites, and clicks in ads ranking systems. The internet applications are built and designed around intents.

If a decentralized network as a whole will support any Internet applications, that implies that transaction cannot be the core of the design but rather intent. To achieve this, we need to first define what intents are and how intents reach consensus.

Today’s blockchains are built with a transaction-centric approach for digital assets. The key logic of accounts, transactions, and contracts is linked to tokens. There are no ways to express users in a complex and general-purpose manner like Web2.

The core innovation is Proof of Intent (PoI), in which the key operating elements of the protocol are intents. Intents are represented by unique identifiers, metadata, and an arbitrary associated payload. Network validators reach consensus about intent processing and dispatching with PoS-like consensus algorithms. The associated payload can be natural language with general purpose intents or structured data fields in DSL intents. Nimble is designed to be blocks of intents structured as Merkle trees.

This core innovation opens the design space for decentralized applications (dApps). It enables decentralized marketplace applications on blockchains and allows developers to build decentralized data marketplaces (e.g., Google), ride-hailing marketplaces (e.g., Uber), e-commerce product marketplaces (e.g., Amazon), and so on.

## Sandhill - Intent Action Recognition Protocol

Sandhill translates intents into actions — accurate, executable, and DSL formatted intent operations — with the innovative Intent Action Recognition (IAR) technology. IAR is tasked to translate user intents in arbitrary formats into specific intent actions.

IAR is a set of LLMs specialized in entity sequence modeling, conversational interactions, and task agents. First, intents are mapped into word entities with the Nimble tagging system after spelling correction and tokenization. Entity sequence modeling tags each word in the user intents with real meanings (e.g., tag ETH as Ethereum native tokens and swap as a trading action). With model predictions of entity tags, DSLs are leveraged for accurate and specific intent operation understanding. Often, user inputs are incomplete (e.g., swap ETH for USDC) in which quantities or other info are missing. LAR conversational module interacts with users to collect the missing inputs for precise action mapping. The agent module consolidates learned tags and intent inputs into a DSL format intent.

It is also a general-purpose AI layer with today’s purpose-built LLMs, which can be run entirely at the edge, including an end user’s mobile device. These purpose-built LLMs coordinate and work together as a team to fulfill network tasks like IAR, as described above. They communicate with each other with a horizontally-scaled dispatching protocol.

## Rainstorm - Horizontally-Scaled Dispatching Network

Nimble network is designed for multi-sided marketplaces handling large-scale requests daily across the globe. Think of the network scale when Uber, Airbnb, and TikTok applications run on the Nimble decentralized network. This Web2 network scale support is never tackled in any decentralized network. We thus strive to build real-time experiences for all users.

The nature of real-time marketplaces makes intent dispatching very lively. Over the lifetime of an intent, multiple network participants can view and update the state of an ongoing intent and need real-time responses. This creates the need to build a horizontally scaled dispatching system and keep network participants synced with real-time intent information, whether through intent understanding time, intent DSL processing time and solvers computing the executions, or users receiving intent completion notifications on their dApps.

Intent dispatching is an orchestration among nodes of heterogeneous capacities, joining and leaving the network dynamically in a decentralized manner. These network nodes need to stay updated with each other as the intents are processed.

Consider a scenario where a user has requested an intent operation, and solvers are online to provide a service. Nimble’s dispatching system identifies a match and provides a solution offered to the user. Now, everyone (intent recognizer, auctioneer, and solver) should be synchronized with each other’s progress.

The fundamental building blocks of Nimble are autonomous agents: network nodes, solvers, and modular auction agents. These are capable of accomplishing tasks entirely on their own. A membership protocol that allows independent agents to discover each other and detect failures. Consistent hashing is adopted to assign work across the agents.

Sprouted from the same never-go-down, always-keep-growing demands for large-scale Web2 applications, what Nimble brings to the table is a decentralized way to get that same partitioning and cooperation at the application level. Nimble nodes detect new capacity when it is added to the network, remove capacity from the network in the event of failure, and distribute the load evenly over whatever capacity there is at any given time. It acts as routing middleware, directing requests to its owner before reaching its handler.

The dispatching nodes are self-organizing and autonomous as a decentralized network. They are rational and aware of other nodes’ capacities based on interaction histories. The network is resilient with a graph topology, and a fanout of 20 implies log\_20(N) time complexity for any request dispatching. N is the total number of nodes in the network.

## Orchestrator - Modular Incentives for the Everything Marketplace

Nimble’s ultimate purpose is to coordinate a network of independent solver agents for the Everything Marketplace. One of the most critical design components is incentive provision for network participants — users with an intent to be fulfilled, solvers with the expertise to contribute, and validators with computation resources to secure the network.

At Web2 scale, a centralized mechanism optimization would not work due to the notorious dimensionality problem. With the growing number of intents, it becomes a matching problem in which each network participant has different optimization goals and definitions of preferences. A direct consequence is the optimization problem will become extremely complex, while the notorious dimensionality problem introduces exponential computational complexity.

Our modular auctions scale the design by coordinating specialized and generic solvers working together to formulate an everything marketplace. The mechanism enjoys truthfulness revealing, incentive compatibility, and regret minimization. Specialized solvers participate in auctions for the specific intent types they are optimized for. Generic and more powerful solvers optimize for different and general intent types by participating in multiple auctions simultaneously or in a multi-stage manner. The modular mechanism design scales the auction layer horizontally despite exponential user request growth.

The modular auctions are inspired by micro-services in big organizations such as Google, Amazon and Meta. It is the ultimate way out for scalability without optimization sacrifices by introducing competition among solvers.

## Bandwagon - General Purpose Intent Database

Everything marketplace infrastructure is only possible with data flexibility instead of being limited to rigid transaction data. The data is thus abstracted as a blob with unique identifiers, metadata, and data row. Metadata contains data types such as intent types, bids, or solutions, while the data row is flexible enough to store all the detailed information related to the data blob. The unique identifier serves as the key in data blob search and modifications.

Reliability at a massive scale with flexible user intents is a unique problem to be solved in a decentralized network. In critical financial marketplaces, even the slightest outage has significant consequences. Nimble network runs on tens of thousands of servers and network components located in any location around the world.

Nimble must scale incrementally. Nimble’s partitioning scheme relies on consistent hashing to distribute the load across multiple storage hosts. In consistent hashing, the output range of a hash function is treated as a fixed circular space or “ring” (i.e. the largest hash value wraps around to the smallest hash value). Each node in the system is assigned a random value within this space representing its “position” on the ring. Each data item identified by a key is assigned to a node by hashing the data item’s key to yield its position on the ring and then walking the ring clockwise to find the first node with a position larger than the item’s position.

Nimble treats the result of each modification as a new and immutable version of the data. It allows for multiple versions of an object to be present in the system simultaneously. Often, new versions subsume the previous version(s), and the system can determine the authoritative version (syntactic reconciliation).

## HashTrail - Distributed intent ledger

The ledger is organized as Merkle trees for anti-entropy: Each node maintains a separate Merkle tree for each key range (the set of keys covered by a virtual node) it hosts. This allows nodes to compare whether the keys within a key range are up-to-date. In this scheme, two nodes exchange the root of the Merkle tree corresponding to the key ranges they host in common.

At Web2 scale, small and large components fail continually. How the persistent state is managed in the face of these failures drives the reliability and scalability of the software systems. It makes extensive use of object versioning and application-assisted conflict resolution in a manner that provides a novel interface for developers to use.

Failure detection is used to avoid attempts to communicate with unreachable peers during get() and put() operations and when transferring partitions and hinted replicas. To avoid failed attempts at communication, a purely local notion of failure detection is entirely sufficient: node A may consider node B failed if node B does not respond to node A’s messages (even if B is responsive to node C's messages).

To achieve high availability and durability, Nimble replicates its data on multiple hosts. Each data item is replicated at N hosts, where N is a parameter configured “per-instance”. Each key, k, is assigned to a coordinator node (described in the previous section). The coordinator is responsible for replicating the data items within its range.

## Summary

As a result of these 6 major innovations, the Nimble network is always online for real-time handling of intent requests. It is general purpose with a focus on the marketplace protocol design. Moreover, for such generality, it supports any marketplace applications on today’s Internet.

Nimble is designed to remove today’s blockchain limitations and enable developers to decentralize Silicon Valley by building decentralized data applications (e.g., search & recommendation), decentralized AI networks (e.g., self-organizing agents), decentralized E-Commerce, and social websites. There will be no operation limitations with the modular auction incentive mechanism design, together with the following 6 innovations:

* Proof of Intent - the Intent Version of PoS;
* Sandhill - Intent Action Recognition Protocol;
* Rainstorm - Horizontally-Scaled Dispatching Network;
* Orchestrator - Modular Incentives for the Everything Marketplace;
* Bandwagon - General Purpose Intent Database;
* HashTrail - Distributed Intent Ledger

## State of the Network

The Nimble network is under active development and is targeted for mainnet beta launch by the end of 2023.
