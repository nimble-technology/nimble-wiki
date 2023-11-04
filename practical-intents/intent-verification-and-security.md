---
description: Practical strategies for securing the intent network
---

# Intent Verification and Security

Since Intents were first discussed, the concept has remained vague.

At a high level, it all makes sense. Users say what they want; the network figures it out. Great.

For projects that aren’t seriously building an intent network, this narrative may fly. We’re taking things a little bit more seriously.

In this post, I’ll explain a few core concepts that enable Nimble to process intents in the wild. That includes which types of intents we can and cannot handle and how we verify that the outcome we describe is achieved.

<figure><img src="https://lh7-us.googleusercontent.com/u0CdEhtNd5T39SHCGA49BkADB24r2H8WIbJe6rKK-NaJocxMWfdNQcIIcvjE6ancyk5F32voDQVlUZrtI7NNMoA6_0oPyHyGBSUa_aOiFiHPt2I8cN5IjCH3fmmeso1K4pEMFxubVeWhS78YPFbKgco" alt=""><figcaption><p>Good intentions, poor execution</p></figcaption></figure>

### Entering the Network

To ensure Nimble can process intents that make their way into our network, we must ensure validity. Garbage in, garbage out, as they say. This is where Nimble is different from every other intent project.

Intents to our network cannot be free-form.

Any good web developer can tell you - user input must be treated as garbage. Imagine the pentest results if someone fuzzed an intent network that accepted free-form input. Absolute chaos.

Web2 has well-established paradigms for users to submit their intents to a network. These are so good that even toddlers can use them.

![](https://lh7-us.googleusercontent.com/NgaNEGhr0yn35aE56MJKYmaxInOrON1-15Ci2d969Jtxefz3ePMDaHnsTZ-SCnzXx2Ca5nXW0VaK8oAsd\_\_APfevx3lqUHwzhblJBrqhqG50aqEACuijInXEHy7aE5rDjPCVMN1XZNl-ZFRNMI6D-Nk)

What do you think “X” does?

Intents are submitted to Nimble via an intermediate interaction layer. There are two currently available layers:

1. Apps developed by Web2 devs
2. Our internal LLM, trained by the Nimble team ([read more](https://docs.nimble.technology/practical-intents/natural-language-intents))

In the case of apps, developers structure intents and present them to users as familiar interactive elements. The developer interface is comparable to common query languages like [JQL](https://support.atlassian.com/jira-service-management-cloud/docs/use-advanced-search-with-jira-query-language-jql/).

The “intent magic” for developers comes from operators that abstract blockchain details away from devs entirely. Sending tokens, for example, is a single operator:

**Send**

* From
* To
* Amount

The developer collects the required fields from the users or the context already available in the application. Then, they create the Intent command and submit it to the network. The Nimble intent network receives the intent operation and identifies the optimal path to resolution through the available solver network.

Solvers join auctions for individual intent operations they are capable of fulfilling.  Solutions will be validated and compared with each other in the auction. Nevertheless, the winning solution would also be checked on the contract to ensure it was fulfilled.

In this way, Nimble intents are both concrete and deterministic without losing any functionality.

#### Extensibility

Intent operations are composable and extensible. At the time of network launch, we will support the operations needed to hide the complexity of the most common use cases. These include any combination of swaps, transfers, and bridges.

The community may propose new intent operations that support more complex use cases. These may include compound operations or entirely new operations.&#x20;

Our goal at launch is to enable one-click compound operations.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/lVb3xkloBU8WH1XXBlSM8QPyb1q6znnkO4jGBahlvzxaMru2v6wt4r7e0wo6uxHyE65pijS_JbRU8CrEDQTUSuxcENPNwXbDnNCVqkjFz9Dx6CsSf3INSCSF_2H7hq1asYEQPLRRXbEaXmskWLOwpAs" alt=""><figcaption><p>No bridge - only intent.</p></figcaption></figure>



Bridges are still used within the network as solvers but leveraged as infrastructure only. Users no longer need to use bridges directly.

### Verification

An adversarial solver could submit low-ball bids to auctions to win intent rewards, then fail to submit the transactions. The network solves this issue internally.

Each intent a user creates has a set of requirements that must be fulfilled. When the network accepts a solution, it will check to see if the requirements are met. If not, the solver’s reputation will be penalized.

There are two types of intents. Solution verification is based on the intent type:

#### On-chain Intents

On-chain intent verification can be easily performed through DeFi operations. When solvers submit a solution proposal to on-chain contracts, they describe the specific steps that will be taken to solve the intent.

The network can verify that the transactions were executed by checking the public ledger.

For example, imagine a solver proposes a solution that swaps Token A for Token B at a 1:1 ratio. The swap intent was only successful if completed within the described parameters.

Network rewards are processed after a successful transaction (or set of transactions). Bundlers only receive network token rewards when they return the profits to users and pay network fees, if any.

#### Off-chain Intents

Consider an AI network built on Nimble. A user submits an LLM intent for an interactive, chatbot-like experience. GPT models from numerous developers compete to fulfill the intent. For chat intents, there will be a standardized evaluation function used to compare intents and evaluate them. Users rate GPT model responses. A reputation system built by user feedback is raw data for model evaluations.

In this way, for off-chain intents, a positive feedback loop between users and solvers is achieved. Such feedback dynamics lay the foundation for network health.

<figure><img src="https://lh7-us.googleusercontent.com/GBBel744hYFiRvn9cOBOhp9K3RAGy0xngsANunTU2Tmfjxqpn-wC0QCAdN5a2lBz_ZigwZxCmncEyV1ODPdbXzwbo7-S92-j0oN7mHcgq8IzbDaIi_qsyvC-qhL5mK91nIdhBHp6Jjs7NML0Go29jo8" alt=""><figcaption></figcaption></figure>

### Attack Management

As a piece of public infrastructure, Nimble will be subject to dishonest and fraudulent behavior. This section details how the system responds to a variety of attacks.

#### Solver Reputation

For non-DeFi intents, a reputation system is required to ensure high-quality solver selection.&#x20;

As an orchestration layer, the network needs signals from the community in order to select truthful solvers. For this purpose, we aim to implement solver reputations. Reputation is built as a weighted sum of staking (optional, yet critical), and a history of user feedback. In this way, low-quality solvers are selected out of the network automatically, and high-quality solvers are chosen more often.

Solutions proposed by solvers who repeatedly provide invalid solutions will be rejected automatically.

#### Sybil Attacks

Sybil attacks are a type of fraud where many identities are created by one or a few individuals. It happens mostly for new identities and nodes. Nimble employs three strategies to prevent Sybil attacks:

* New nodes (e.g., users, solvers, and validators) without existing reputations are likely Sybil nodes. As a result, they are placed under suspicion by other nodes on the network. They can prove their honesty with more network token stakes and a history of interactions with other nodes.
* Each node locally maintains social trust (decentralized, and nodes may have different social trust scores for the same node). To minimize the cost of the social trust-building process, nodes can exchange social trust scores. In this way, a good player can establish its reputation faster, while low reputation nodes find it hard to build reputations.
* The social trust system has another good side effect. It rewards early contributors to the network (e.g., solvers, users, and validators). This is helpful for the network jumpstart and the philosophy that the network rewards early contributions.

#### DDoS Attacks

DDoS attacks happen when users and solvers send bulk requests for the purpose of overwhelming the system. Attackers may create large amounts of spam intents (or solutions) that are invalid and make it difficult to select legitimate intents or solutions.

To prevent this, there are two things to be implemented:&#x20;

* Introducing fee markets by charging a fee for intents
* The solver with a high reputation can rate the intents and, thus, users. Low-rated intents should be dropped by the network

The above is just a list of critical security and verification considerations of intent. There are more considerations in the code.\
