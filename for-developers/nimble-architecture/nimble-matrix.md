# Nimble Matrix

## Context

The Nimble Matrix represents the fundamental elements flowing through the Orderbook. It is the standardized data structure to define various data structures such as training, inference, data and gpu requests on the network. It is specified by the Nimble domain specific language (DSL) as illustrated below.

## Case Study

Still taking an AI training example, consider an AI developer named 'Bob' who uses a dataset called 'health-bodyscan-image-set' and connects with a GPU provider from 'US-california-40GRAM' to develop large image classification models. Here’s how the corresponding Nimble Matrix would be structured:

| <p>0x9760 (as Bob's address)<br>{<br>    code_snippet:  "0x9760_train.py",<br>    max_pay: "20 $NIM",</p><p>    max_time_duration: "7200 seconds",</p><p>    matching_strategy: "cost efficient",</p><p>    data_strategy: "standard",<br>    ....</p><p>}</p> | <p>0x7044 (as bodyscan data provider's address)<br>{<br>    header: "['userid', 'img', 'label_class_5']",<br>    min_price: "10 $NIM",</p><p>    samping_strategy: "cluster",</p><p>    min_storage: "100GB"</p><p>    matching_strategy: "max earning",<br>    ....</p><p>} </p> |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>0x3695 (as california GPU provider's address)<br>{<br>    GRAM: "40GB",<br>    max_storage: "200GB", <br>    matching_strategy: "stable revenue",<br>    min_price: "5 $NIM",</p><p>    virtualization: "true"</p><p>    ...</p><p>}</p>                    | <p>0xV354 (as validator)<br>{<br>    type: matching,<br>    storage: 100GB,<br>    estimated_duration: "6600 seconds",<br>    output_dir: "ds:0x9760/".<br>    data_strategy: "encryption",<br>    state: validated<br>....</p><p>}</p>                                           |

The example provided is intended solely for matching purposes within the training flow; however, the same structure applies to subsequent steps and inference flows. Each step functions in a fully decentralized manner and is executed on-chain. Importantly, all operations are conducted on top of the Nimble Matrix.

## Matrix Storage

At Nimble Network, we understand the diverse storage needs of Nimble Matrix essential for powering our AI OrderBook. Our approach to storage is  designed to support two fundamental types: static, immutable data or model files, and dynamic, fast-changing matrix information, node information, and OrderBook.

#### Dynamic, Fast-Changing Storage

For our dynamic and rapidly evolving data needs—matrix information, node information, and OrderBook—we have constructed the backbone using a Distributed Hash Table (DHT). This system serves three critical purposes:

**1. Node Lookup:** Using a consistent hashing scheme, our DHT facilitates precise and swift node lookups. For instance, once a match is completed and an application needs to connect to a specific GPU, the DHT is queried using the provider’s key to locate the responsible validator node.

**2. Load Balancing:** The DHT inherently balances the storage load among nodes as they join or leave the network. Employing algorithms like consistent hashing, it targets evenly distributing tasks such as training requests to GPU providers, optimizing resource use and enhancing system performance.

**3. Dynamic Node Participation:** Our network is in a phase of hyper-growth, with numerous GPUs and validators joining daily. The DHT allows for dynamic participation with minimal disruption. As new validators come onboard, they seamlessly take over a portion of the keys from existing nodes. Similarly, when a node exits, its responsibilities and keys are efficiently reassigned to the remaining nodes.

<figure><img src="../../.gitbook/assets/gitbook - matrix (2).png" alt=""><figcaption></figcaption></figure>

#### Static, Immutable Storage

For storing static data such as data or model files, which are immutable, we have chosen not to reinvent the wheel. Instead, we've partnered with leading on-chain solutions to ensure scalability and security. A prime example of this integration is with BNB chain Greenfield, specifically for model file storage. This partnership enables us to leverage blockchain technology to secure and scale our storage solutions efficiently.

<figure><img src="../../.gitbook/assets/Nimble x BNB Greenfield.png" alt=""><figcaption></figcaption></figure>

## Matrix Operations

Nimble Matrix can represent onchain and offchain operations as well.

### On-chain AI Operations

On-chain operation verification can be easily performed through DeFi operations. When miners submit a solution proposal to on-chain contracts, they describe the specific steps that will be taken to solve the intent.

The network can verify that the transactions were executed by checking the public ledger.

For example, imagine a miner proposes a solution that swaps Token A for Token B at a 1:1 ratio. The swap operation was only successful if completed within the described parameters.

Network rewards are processed after a successful transaction (or set of transactions). Bundlers only receive network token rewards when they return the profits to users and pay network fees, if any.

### Off-chain AI Operations

Consider a user submits an LLM request for an interactive, chatbot-like experience. GPT models from numerous developers compete to fulfill the operation. For chat requests, there will be a standardized evaluation function used to compare intents and evaluate them. Users rate GPT model responses. A reputation system built by user feedback is raw data for model evaluations.

In this way, for off-chain operations, a positive feedback loop between users and miners is achieved. Such feedback dynamics lay the foundation for network health.&#x20;
