---
description: Initial Token Proposal to Nimble Community
---

# Tokenomics

## Nimble Tokenomics

This post details how the NIMBLE token is distributed to various participants of the Nimble Network and associated ecosystems. Thoughtful distribution of Nimble tokens is vital for on-chain governance and ensuring a fully decentralized, permissionless, and sustainable ecosystem.

Token-based governance enables token holders to guide the development of Nimble. The goal of this document is to prepare the community to participate in governance events so token holders can shape the future of the protocol productively.

### Terminology

* NIMBLE is the official symbol of the token used in Nimble Network.
* NIM is short for NIMBLE.
* VIM: 1 VIM = 10^-9 NIM.

### Governance and the Nimble DAO

Nimble governance will aid in decision-making as we develop or alter network mechanisms in the future. The governance body is responsible for decisions such as:

* Selection of updates to be applied to programs across the blockchain
* Fee determination
* Reward determination
* Miner permissioning structures
* Updates to interpretation models

Additional topics may be added in the future, with approval by the DAO.

### Distribution of Tokens

| Symbol         | NIMBLE                                                                                                                                                                                                                             |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Supply         | 1,000,000,000                                                                                                                                                                                                                      |
| Initial Supply | 150,000,000 (15%)                                                                                                                                                                                                                  |
| Vesting        | <p>85% of NIMBLE are initially locked.</p><p>40% tokens are unlocked 6, 18, 30, and 42 months after token generation event (TGE).</p><p>45% locked network, ecosystem and miner tokens have halving every 6 months in 4 years.</p> |

### Distribution Table

| Category            | Locked  | Unlocked | Total   |
| ------------------- | ------- | -------- | ------- |
| Network & Ecosystem | 25      | 5        | 30      |
| Miner Rewards       | 18      | 2        | 20      |
| Community           | 0       | 10       | 10      |
| Development         | 20      | 0        | 20      |
| Private Sales       | 20      | 0        | 20      |
| **Total**           | **83%** | **17%**  | **100** |

### Network & Ecosystem

**30%, or 300,000,000 NIMBLE**

This reward allocation is reserved for those who contribute to the Nimble Network. Contributions may come from a variety of sources.

* Protocol developers
* App developers
* Educators
* Early miners
* Early users
* Network miners
* Network validators

With this allocation, we hope to provide incentives and funding for projects to develop functionality with Nimble. Development may include network mining, ecosystem tools, educational events, or other action that increases awareness of Nimble.

5% of the network NIMBLE allocation is unlocked and can be distributed to this community immediately. The remaining 25% (250M) tokens will be distributed following our vesting schedule.

### Miner Rewards

**20%, or 200,000,000 NIMBLE**

This reward allocation is reserved for the network’s Miner pool, or miners.

Miners contribute a variety of functionality to the Nimble protocol. This “Miner Rewards” allocation is a blend of tokens reserved for reward programs, grants, and scholarships that will encourage developers to build miners.

20M NIMBLE are unlocked for immediate use to incentivize miner development. A remaining 180M NIMBLE are locked, subject to our vesting period as described earlier.

Upon unlocking, tokens will be made available for distribution to miners.

### Community

**10%, or 100,000,000 NIMBLE**

The community allocation of NIMBLE is reserved for launch-related purposes.

This includes launch events, marketing, exchange listing, launchpad, and other events that will drive interest in the protocol.

Since this allocation is required for the immediate use of the network, it is unlocked immediately.

### Development

**20%, or 200,000,000 NIMBLE**

The development allocation will be provided to projects or individuals that contribute to core components of the Nimble Network stack. Contributors to the core auction, interpretation stack, or dispatching layer may earn a stake of this allocation.

0% of development NIMBLE allocation is unlocked and can be distributed to developers immediately upon TGE of the network. The remaining 20% will be distributed following our vesting schedule.

### Private Sales

**20%, or 200,000,000 NIMBLE**

This allocation is reserved for early funding of the network development, as required by the core team. As of now, these tokens are unallocated.

0% of private sales NIMBLE allocation is unlocked and can be distributed to private investors immediately upon TGE of the network. Once allocated, tokens from the private sale will be subject to the vesting schedule.

## Validation, Mining & Halving

### Validator & Miner Rewards

New tokens are produced every block at a fixed rate. Newly minted tokens are shared among miners and validators given their contributions to the network. Validators stake to get network validation rewards. The miners are AI miners to provide real model solutions to the network and are rewarded based on the evaluation score of their solutions.

As a result, for the emitted tokens at each block, there are two layers of distribution.

1.  First, a percentage portion of these emitted tokens is allocated to each of models/tasks in the network, in accordance with its improvement/performance. The network determines these percentage portions. All partial allocations should sum up to 100%.

    Consider a model _i_, it has a portion of v% which is determined by the network. And assume the emission at current block _t_ is _x\_t_. Then all validators and miners who participate in model _i_'s update will receive v% \* _x\_t_ in total.
2.  Then, validators will receive divident which is proportional to their staking ratios and miners will receive reward based on its marginal contributions to the model update/task solving. 50% of the tokens emitted to a certain model will be distributed to its validators and another 50% to its miners. For validators, the distribution is calculated by staking ratio.

    So consider 3 validators, staking 100, 100, 200 respectively, they will receive 25%, 25% and 50%. For miners, the distribution is calculated by its marginal contributions (which we use shapley value in a collaborative system for fair distribution of rewards). So consider 3 miners with shapley values of 0.2, 0.3 and 0.5, they will receive 20%, 30% and 50%.

To conclude, for each model/task _i_,

* a validator _m_ will receive `v% * _x_t_ * stake_m / (stake sum within this model/task)`
* a miner _n_ will receive `v% * _x_t_ * shapley_value / (shapley value sum within this model/task)`

Each token is mapped to a real AI operation matching or model solution provision effort by miners and validators. With the growth of the network and halving every 12 months, it becomes more and more competitive to get minted NIMBLE tokens.

### Production Rate Halving

45% of tokens are reserved for mining and validating, being released within 48 months since token generation event (TGE). The network token production rate will be halved every 12 months (i.e., 365 days). Each halving has 2102400 blocks and each blockstep is 15 seconds. Roughly 114.155251142 tokens are created per block at TGE, and the initial daily rate is calculated with the following equation, to be more accurate:

<figure><img src="../.gitbook/assets/image (4).png" alt="" width="169"><figcaption></figcaption></figure>

in which _i_ is an indexing integer to represent the number of years in the vesting schedule.

### Delegation & Staking

Everyone can delegate NIMBLE tokens to validators and earn staking rewards. Validators compete with each other to decide the percentage of staking rewards. The reward market introduces competitions among validators and improves the network robustness.

### Conclusions

We are still actively working to launch the network. Once launched, expect additional announcements regarding NIMBLE governance. Follow along on our Twitter and Discord community pages for up-to-date information and to avoid inaccurate information about the Nimble project.
