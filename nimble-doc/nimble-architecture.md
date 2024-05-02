# 🗼 Nimble Architecture

Despite whatever fancy terms in web3, this page talks about 3 key components of the overall Nimble engineering system: storage, communication and security. &#x20;

## Storage

At Nimble Network, we understand the diverse storage needs essential for powering our AI OrderBook. Our approach to storage is  designed to support two fundamental types: static, immutable data or model files, and dynamic, fast-changing matrix information, node information, and OrderBook.

#### Static, Immutable Storage

For storing static data such as data or model files, which are immutable, we have chosen not to reinvent the wheel. Instead, we've partnered with leading on-chain solutions to ensure scalability and security. A prime example of this integration is with BNB chain Greenfield, specifically for model file storage. This partnership enables us to leverage blockchain technology to secure and scale our storage solutions efficiently.

#### Dynamic, Fast-Changing Storage

For our dynamic and rapidly evolving data needs—matrix information, node information, and OrderBook—we have constructed the backbone using a Distributed Hash Table (DHT). This system serves three critical purposes:

**1. Node Lookup:** Using a consistent hashing scheme, our DHT facilitates precise and swift node lookups. For instance, once a match is completed and an application needs to connect to a specific GPU, the DHT is queried using the provider’s key to locate the responsible validator node.

**2. Load Balancing:** The DHT inherently balances the storage load among nodes as they join or leave the network. Employing algorithms like consistent hashing, it targets evenly distributing tasks such as training requests to GPU providers, optimizing resource use and enhancing system performance.

**3. Dynamic Node Participation:** Our network is in a phase of hyper-growth, with numerous GPUs and validators joining daily. The DHT allows for dynamic participation with minimal disruption. As new validators come onboard, they seamlessly take over a portion of the keys from existing nodes. Similarly, when a node exits, its responsibilities and keys are efficiently reassigned to the remaining nodes.

## Communication

Now it comes to two types of network traffic essential for supporting the AI Orderbook.

### Validador <> Validator&#x20;

Gossip protocols is used for several purposes:

**1.State Synchronization**: Validators can use gossip to keep their state information (like blockchain state, configuration, or operational metrics) synchronized with each other.

**2.Service Discovery**: Validators can propagate information about available services, like GPU availability or data service updates, throughout the network.

**3.Failure Detection**: Validators can quickly share alerts about node failures or connectivity issues, allowing the network to adapt and respond rapidly.

### Validator <> GPU/Data/Developer/Applications

In a landscape as dynamic as the Nimble Network, standard communication protocols often fall short. They can be too rigid or overly broad, failing to address the specific needs and nuances of our decentralized ecosystem. Our DSL is crafted to bridge this gap, providing precise, efficient, and flexible communication tailored to the unique demands of our network.

**1. Integration with Nimble Matrix:** The DSL is fully integrated with our Nimble Matrix, an innovative framework that groups and maps resources across our network. This integration allows for seamless queries and commands related to resource allocation, monitoring, and transactional operations, ensuring a smooth and coherent experience.

**2. Clean and Efficienct:** From querying the status of a GPU to fetching data with specific privacy settings, our DSL makes managing resources straightforward. It supports complex, multi-step operations and can adapt to the network’s changing needs, enhancing our ability to scale and evolve.

**3. Enhanced Security:** Security is paramount in everything we do at Nimble Network. Our DSL includes robust security protocols to authenticate commands and protect against unauthorized access, ensuring that our network remains secure and trustworthy.

## Security and Privacy

At Nimble Network, we recognize the critical importance of privacy and security, especially when it comes to handling sensitive data in on-chain machine learning environments. As we expand our ecosystem, ensuring that all data is protected and used ethically is paramount. To address these concerns, we have implemented robust strategies that include data embedding, encryption, and the introduction of a permissioned access model.

### Data Embedding

Instead of training models or performing inference on raw data, we use a sophisticated embedding technique. This method involves transforming sensitive data into a another dimensional space, which represents the essential information without exposing the raw data. This process not only secures the data but also enhances processing efficiency and protects user privacy.

**1.Privacy Protection**: By converting raw data into embeddings, personal identifiers are removed, ensuring that the data cannot be traced back to any individual.

**2.Reduced Data Abuse Risk**: Embeddings minimize the detailed information that can be exploited, thus significantly lowering the risk of data misuse.

### Encryption

To further safeguard our data, all communications within the Nimble Network will be encrypted. This encryption applies to data as it moves between nodes and while it is at rest, ensuring that only authorized nodes can access or interpret the information.
