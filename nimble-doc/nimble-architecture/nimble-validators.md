# Nimble Validators

## Context

Nimble validators govern the AI orderbook with Proof of Stake. Miners are evaluated by validators to perform real work and build reputations on the network. The core of validator efficiency comes to two types of validator traffic essential for supporting the AI Orderbook.

## Validador <> Validator

Gossip protocols is used for several purposes:

**1.State Synchronization**: Validators can use gossip to keep their state information (like blockchain state, configuration, or operational metrics) synchronized with each other.

**2.Service Discovery**: Validators can propagate information about available services, like GPU availability or data service updates, throughout the network.

**3.Failure Detection**: Validators can quickly share alerts about node failures or connectivity issues, allowing the network to adapt and respond rapidly.

<figure><img src="../../.gitbook/assets/Group 1312318674.png" alt="" width="563"><figcaption></figcaption></figure>

## Validator <> GPU/Data/Developer/Applications

In a landscape as dynamic as the Nimble Network, standard communication protocols often fall short. They can be too rigid or overly broad, failing to address the specific needs and nuances of our decentralized ecosystem. Our DSL is crafted to bridge this gap, providing precise, efficient, and flexible communication tailored to the unique demands of our network.

**1. Integration with Nimble Matrix:** The DSL is fully integrated with our Nimble Matrix, an innovative framework that groups and maps resources across our network. This integration allows for seamless queries and commands related to resource allocation, monitoring, and transactional operations, ensuring a smooth and coherent experience.

**2. Clean and Efficienct:** From querying the status of a GPU to fetching data with specific privacy settings, our DSL makes managing resources straightforward. It supports complex, multi-step operations and can adapt to the network’s changing needs, enhancing our ability to scale and evolve.

**3. Enhanced Security:** Security is paramount in everything we do at Nimble Network. Our DSL includes robust security protocols to authenticate commands and protect against unauthorized access, ensuring that our network remains secure and trustworthy.

<figure><img src="../../.gitbook/assets/Group 1312318675.png" alt="" width="563"><figcaption></figcaption></figure>

## Attack Management

As a piece of public infrastructure, Nimble will be subject to dishonest and fraudulent behavior. This section details how the system responds to a variety of attacks.

### Miner Reputation

A reputation system is required to ensure high-quality and automated miner selection via AI orderbook.

As an orchestration layer, the network needs signals from the community in order to select truthful miners. For this purpose, we aim to implement miner reputations. Reputation is built as a weighted sum of staking (optional, yet critical), and a history of user feedback. In this way, low-quality miners are selected out of the network automatically, and high-quality miners are chosen more often.

Solutions proposed by miners who repeatedly provide invalid solutions will be rejected automatically.

### Sybil Attacks

Sybil attacks are a type of fraud where many identities are created by one or a few individuals. It happens mostly for new identities and nodes. Nimble employs three strategies to prevent Sybil attacks:

* New nodes (e.g., users, miners, and validators) without existing reputations are likely Sybil nodes. As a result, they are placed under suspicion by other nodes on the network. They can prove their honesty with more network token stakes and a history of interactions with other nodes.
* Each node locally maintains social trust (decentralized, and nodes may have different social trust scores for the same node). To minimize the cost of the social trust-building process, nodes can exchange social trust scores. In this way, a good player can establish its reputation faster, while low reputation nodes find it hard to build reputations.
* The social trust system has another good side effect. It rewards early contributors to the network (e.g., miners, users, and validators). This is helpful for the network jumpstart and the philosophy that the network rewards early contributions.

### DDoS Attacks

DDoS attacks happen when users and miners send bulk requests for the purpose of overwhelming the system. Attackers may create large amounts of spam operations (or solutions) that are invalid and make it difficult to select legitimate requests or solutions.

To prevent this, there are two things to be implemented:&#x20;

* Introducing fee markets by charging a fee for operations
* The miner with a high reputation can rate the operations and, thus, users. Low-rated requests should be dropped by the network

The above is just a list of critical security and verification considerations of operation. There are more considerations in the code.



