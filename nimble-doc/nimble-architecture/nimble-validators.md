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

## Miner Reputations

Miners like GPUs build reputations by performing tasks.



