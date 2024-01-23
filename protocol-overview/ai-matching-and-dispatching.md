---
description: Matching structured AI operation DSLs with miners
---

# AI Matching and Dispatching

In the AI-centric world, the efficient handling of information requests across distributed networks has become imperative. With the Nimble AI protocol, we introduce a cutting-edge Peer-to-Peer (P2P) network that seamlessly integrates a DSL query language for efficient and precise AI operation processing and dispatching across nodes.

## Recap

Before diving deep into dispatching details, it is easier to do a quick recap of key elements of the protocol.

**Message Syncing**

When a node receives the AI prediction or mining message, it will recognize it through the AI-powered miners (e.g. user action recognizer) on the node, and broadcast the processed message to all the peers in the network. Nimble network uses PubSub model to transmit messages across the network, in that way, it is more efficient as messages are only sent to interested subscribers, thereby reducing redundancy and network load.

**Case Study: LLM Operation Recognition**

Upon receiving a natural language request, the advanced LLM miner interprets and analyzes the query to extract the user's operations and required data points. The LLM then constructs structured data from the natural language input, converting it into a format akin to a DSL query for further processing. It will eventually transform into a miner understandable operation format, and broadcast to all the peer nodes.

#### **AI Operation Query Language**

The network receives AI requests articulated in a custom DSL. This language is tailored for defining complex data requests and interactions within the network, allowing users to specify exactly what they are looking for in a succinct and expressive manner. A simple example of making multiple transfers to different accounts.

The network also accepts queries made in natural human language, making it accessible to a wider audience, and our AI layer on each node will figure out what the requests are.

**Operation Mempool**

After AI requests get recognized, and a solved understandable request data will be generated, and broadcasted to each peer node, and temporarily stored in a mempool on each node. Once an operation gets picked up and handled, it will be removed from the mempool.

## Efficient Dispatching

Dispatching takes place after the operation action recognition layer recognizes the AI requests, each node will autonomously determine the most appropriate path to fulfill the request, it sends different types of requests to different AI operation mempools accordingly.&#x20;

**AI Operation Extensibility**

Nimble operations are extensible by design with flexible operation data structures and operators. Default ones are provided for commonly used operations. Advanced users can always customize their own operation request operators and data.

Operation data consists of a) operation id - unique id for efficient search in the distributed hash table, b) operation metadata - operation types, timestamp and sender, and c) operation payload - any operation logic related data and non-logic related data.

AI operation request operators are any functions provided for operation data. Typical ones include but not limited to a) operation evaluator - evaluate operations with returned numerical metrics, b) operation comparator - compare two operations using the evaluator functions and return boolean to show user preferences among them, and c) verify - perform sanity checks of operations with success and error code returns.

With the above design, operation extensibility is easily achieved.

**Matching Efficiency**

Matching problem is a notoriously difficult problem to solve, by matching preferences of two sets of entities - users and miners in this case. To be more precise, it is to match AI operation goals with miner solutions. There are several considerations to optimize efficiency.

First, each miner only evaluates AI requests of a particular type in the modular auction design. An auction algorithm within the dispatching layer determines the most suitable miner node for each request. Miner nodes bid for the right to process requests based on their capabilities, load, and other dynamic factors. The dispatching layer assigns each request to the winning bidder, ensuring optimal resource allocation and timely processing, and miners are responsible for constructing the operation solution to be handled. When a miner starts constructing solutions for operations, it will pick up the operations first, and then send a message to notify all the peers, removing those operations from the mempool.

Even if the above design limits the complexity to the number of requests N for the particular request type, the time complexity is still N \* M where M is the number of miners. Operations are thus batched and miners bid for each batch. This is combined with miner reputations, which boost miner's chances of participating in the auctions. Each modular auction is thus organized in a hierarchical tree where high reputation miners participate in the auction first. Miners can boost their reputation with more stakes and better operation AI solutions. This will reduce the time complexity on the miner side to log\_k(N\*M/x) where k is the fanout of the miner reputation tree and x is the average number of operations in a batch.

Dispatchers reduce network cost with structured design, though flooding is the most intuitive yet also costly approach. AI operation map is a buffer map with all neighboring peers’ operation lists. First, each node keeps separate operation maps for each operation type. This reduces the network cost since a node can request operation maps for particular operation types. Second, the operation maps are organized as a tree for efficient search and storage in local nodes. The search time is only log\_O where O is the number of operation types on the network. Such modular operation map design also enables dispatching nodes to select operation types based on the operation rewards and dispatcher node capacities. Dispatchers are network aware of each other’s bandwidth and computation capacities. In this way, they can build a more efficient overlay network with capacity aware neighboring peer selections.

Now, the network is scalable with the growth of operation types, miners, and dispatchers.

**Double Dispatching**\
Double dispatching happens when two or more miners execute the same operation. Obviously, dispatchers are not doing a good job if this happens. It is catastrophic like double spending in Bitcoin.

To start, each operation mainly has 5 states - a) SENT, b) VERIFIED, c) ALLOCATED, d) SOLVED, and e) INVALID. Users mark operations as SENT before publishing them to the network. It is marked by network nodes as VERIFIED after calling the verify function which returns success. INVALID is used to mark it as operations not being able to be processed by the network. SOLVED is the state to mark operations as being solved already, after being ALLOCATED to miners with winner bids.

The most naive way to prevent double dispatching is that each operation carries a lock. The lock only allows one node to modify operation states. Yet, this has a lot of scalability issues without fully utilizing the processing power of the network. Our solution to this is any node can modify operation states other than SOLVED. Nodes do not need to derive states like VERIFIED by themselves. Remember each node is connected with a list of other nodes it trusts. A weighted sum of its neighbors’ operation states is already good enough. For the SOLVED state, only the miner has the permission to change it and it can propagate across the network with log\_P where P is the number of nodes on the network. The solution miner is verified by the signature when they are granted the permission to resolve an operation. The miner has no incentive to cheat since it wants to receive network rewards. Network rewards are distributed when ⅔ nodes reach consensus around the operation SOLVED state.
