---
cover: >-
  https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw2fHxib29rfGVufDB8fHx8MTcxNDA3MTI4Mnww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# 📖 Nimble AI Orderbook

Successful AI training hinges on three critical resources: compute power (GPUs), data, and developers. Each of these pillars faces its own set of challenges—from accessibility and scalability to efficiency. Similarly, AI inferences relies on computer power and application's calls.

We call the whole system "AI Orderbook" as a one-stop shop that connects everything together on chain, covering both training and inference.&#x20;

## Nimble Matrix

The Nimble Matrix represents the fundamental elements flowing through the Orderbook. For example, consider an AI developer named 'Bob' who uses a dataset called 'health-bodyscan-image-set' and collaborates with a GPU provider from 'US-california-40GRAM' to develop large image classification models. Here’s how the corresponding Nimble Matrix would be structured:

| <p>0x9760 (as Bob's address)<br>{<br>    code_snippet:  "0x9760_train.py",<br>    max_pay: "20 $NIM",</p><p>    max_time_duration: "7200 seconds",</p><p>    matching_strategy: "cost efficient",</p><p>    data_strategy: "standard",<br>    ....</p><p>}</p> | <p>0x7044 (as bodyscan data provider's address)<br>{<br>    header: "['userid', 'img', 'label_class_5']",<br>    min_price: "10 $NIM",</p><p>    samping_strategy: "cluster",</p><p>    min_storage: "100GB"</p><p>    matching_strategy: "max earning",<br>    ....</p><p>} </p> |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>0x3695 (as california GPU provider's address)<br>{<br>    GRAM: "40GB",<br>    max_storage: "200GB", <br>    matching_strategy: "stable revenue",<br>    min_price: "5 $NIM",</p><p>    virtualization: "true"</p><p>    ...</p><p>}</p>                    | <p>0xV354 (as validator)<br>{<br>    type: matching,<br>    storage: 100GB,<br>    estimated_duration: "6600 seconds",<br>    output_dir: "ds:0x9760/".<br>    data_strategy: "encryption",<br>    state: validated<br>....</p><p>}</p>                                           |

The example provided is solely for matching purposes, and the complete orderbook flow comprises three distinct steps:

1. **Matching**: Identifies all potential combinations that meet the criteria of every participant.
2. **Pricing**: Participants bid to achieve the most favorable economic outcomes.
3. **Transaction**: This step records the actual execution of training or inference.

Each stage operates fully decentralized and is executed on-chain. Again, they all operate on top of Nimble Matrix.&#x20;

## Nimble OrderBook&#x20;

