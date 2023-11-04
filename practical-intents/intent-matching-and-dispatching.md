---
description: Matching structured intent DSLs with solvers
---

# Intent Matching and Dispatching

In the intent-centric world, the efficient handling of information requests across distributed networks has become imperative. With the Nimble intent protocol, we introduce a cutting-edge Peer-to-Peer (P2P) network that seamlessly integrates a DSL query language for efficient and precise request processing and dispatching across nodes.

## Recap

Before diving deep into dispatching details, it is easier to do a quick recap of key elements of the protocol.

#### **Intent Query Language**

The network receives intents articulated in a custom DSL. This language is tailored for defining complex data requests and interactions within the network, allowing users to specify exactly what they are looking for in a succinct and expressive manner. A simple example of making multiple transfers to different accounts.

<figure><img src="https://lh7-us.googleusercontent.com/lUpeFlHy2bQXKIddr3K0kizDpjniexcz5FMdw7ul64OWzAZOKq1IvcmnzoApaz33FzG57xiXFd2CDOM_RKoJ0wnPu-wilc3Tiq2gPvG9tEDmXk4NZ5AWYVa31o_a7EIbbFvWB4jEy-VonhN9-GwM5yM" alt=""><figcaption><p>Intent DSL Query</p></figcaption></figure>

The network also accepts queries made in natural human language, making it accessible to a wider audience, and our AI layer on each node will figure out what the requests are.

**Message Syncing**

When a node receives the intent message, it will recognize it through the AI-powered intent action recognizer on the node, and broadcast the processed message to all the peers in the network. Nimble network uses PubSub model to transmit messages across the network, in that way, it is more efficient as messages are only sent to interested subscribers, thereby reducing redundancy and network load.

**LLM Intent Recognition**

Upon receiving a natural language request, our advanced LLM interprets and analyzes the query to extract the user's intent and required data points. The LLM then constructs structured data from the natural language input, converting it into a format akin to a DSL query for further processing. It will eventually transform into a solver understandable intent format, and broadcast to all the peer nodes.

**Intent Mempool**

After intent requests get recognized, and a solved understandable intent data will be generated, and broadcasted to each peer node, and temporarily stored in a mem pool on each node. Once an intent gets picked up and handled, it will be removed from the mem pool.

## Efficient Dispatching

Dispatching takes place after the intent action recognition layer recognizes the intent requests, each node will autonomously determine the most appropriate path to fulfill the request, it sends different types of requests to different intent mempools accordingly.&#x20;

**Intent Extensibility**

Nimble intents are extensible by design with flexible intent data structures and operators. Default ones are provided for commonly used intents. Advanced users can always customize their own intent operators and data.

Intent data consists of a) intent id - unique id for efficient search in the distributed hash table, b) intent metadata - intent types, timestamp and sender, and c) intent payload - any intent logic related data and non-logic related data.

Intent operators are any functions provided for intent data. Typical ones include but not limited to a) intent evaluator - evaluate intents with returned numerical metrics, b) intent comparator - compare two intents using the evaluator functions and return boolean to show user preferences among them, and c) verify - perform sanity checks of intents with success and error code returns.

With the above design, intent extensibility is easily achieved.

**Matching Efficiency**

Matching problem is a notoriously difficult problem to solve, by matching preferences of two sets of entities - users and solvers in this case. To be more precise, it is to match intent goals with solver solutions. There are several considerations to optimize efficiency.

First, each solver only evaluates intents of a particular type in the modular auction design. An auction algorithm within the dispatching layer determines the most suitable solver node for each request. Solver nodes bid for the right to process requests based on their capabilities, load, and other dynamic factors. The dispatching layer assigns each request to the winning bidder, ensuring optimal resource allocation and timely processing, and solvers are responsible for constructing the intent solution to be handled. When a solver starts constructing solutions for intents, it will pick up the intents first, and then send a message to notify all the peers, removing those intents from the mempool.

Even if the above design limits the complexity to the number of intents N for the particular intent type, the time complexity is still N \* M where M is the number of solvers. Intents are thus batched and solvers bid for each batch. This is combined with solver reputations, which boost solver’s chances of participating in the auctions. Each modular auction is thus organized in a hierarchical tree where high reputation solvers participate in the auction first. Solvers can boost their reputation with more stakes and better intent solutions. This will reduce the time complexity on the solver side to log\_k(N\*M/x) where k is the fanout of the solver reputation tree and x is the average number of intents in a batch.

Dispatchers reduce network cost with structured design, though flooding is the most intuitive yet also costly approach. Intent map is a buffer map with all neighboring peers’ intent lists. First, each node keeps separate intent maps for each intent type. This reduces the network cost since a node can request intent maps for particular intent types. Second, the intent maps are organized as a tree for efficient search and storage in local nodes. The search time is only log\_O where O is the number of intent types on the network. Such modular intent map design also enables dispatching nodes to select intent types based on the intent rewards and dispatcher node capacities. Dispatchers are network aware of each other’s bandwidth and computation capacities. In this way, they can build a more efficient overlay network with capacity aware neighboring peer selections.

Now, the network is scalable with the growth of intent types, solvers, and dispatchers.

**Double Dispatching**\
Double dispatching happens when two or more solvers execute the same intent. Obviously, dispatchers are not doing a good job if this happens. It is catastrophic like double spending in Bitcoin.

To start, each intent mainly has 5 states - a) SENT, b) VERIFIED, c) ALLOCATED, d) SOLVED, and e) INVALID. Users mark intents as SENT before publishing them to the network. It is marked by network nodes as VERIFIED after calling the verify function which returns success. INVALID is used to mark it as intents not being able to be processed by the network. SOLVED is the state to mark intents as being solved already, after being ALLOCATED to solvers with winner bids.

The most naive way to prevent double dispatching is that each intent carries a lock. The lock only allows one node to modify intent states. Yet, this has a lot of scalability issues without fully utilizing the processing power of the network. Our solution to this is any node can modify intent states other than SOLVED. Nodes do not need to derive states like VERIFIED by themselves. Remember each node is connected with a list of other nodes it trusts. A weighted sum of its neighbors’ intent states is already good enough. For the SOLVED state, only the solver has the permission to change it and it can propagate across the network with log\_P where P is the number of nodes on the network. The solution solver is verified by the signature when they are granted the permission to resolve an intent. The solver has no incentive to cheat since it wants to receive network rewards. Network rewards are distributed when ⅔ nodes reach consensus around the intent SOLVED state.
