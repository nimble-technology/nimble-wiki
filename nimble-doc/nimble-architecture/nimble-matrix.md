# Nimble Matrix

## Context

The Nimble Matrix represents the fundamental elements flowing through the Orderbook. It is the standardized data structure to define various data structures such as training, inference, data and gpu requests on the network. It is specified by the Nimble domain specific language (DSL) as illustrated below.

## Case Study

Still taking an AI training example, consider an AI developer named 'Bob' who uses a dataset called 'health-bodyscan-image-set' and connects with a GPU provider from 'US-california-40GRAM' to develop large image classification models. Here’s how the corresponding Nimble Matrix would be structured:

| <p>0x9760 (as Bob's address)<br>{<br>    code_snippet:  "0x9760_train.py",<br>    max_pay: "20 $NIM",</p><p>    max_time_duration: "7200 seconds",</p><p>    matching_strategy: "cost efficient",</p><p>    data_strategy: "standard",<br>    ....</p><p>}</p> | <p>0x7044 (as bodyscan data provider's address)<br>{<br>    header: "['userid', 'img', 'label_class_5']",<br>    min_price: "10 $NIM",</p><p>    samping_strategy: "cluster",</p><p>    min_storage: "100GB"</p><p>    matching_strategy: "max earning",<br>    ....</p><p>} </p> |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>0x3695 (as california GPU provider's address)<br>{<br>    GRAM: "40GB",<br>    max_storage: "200GB", <br>    matching_strategy: "stable revenue",<br>    min_price: "5 $NIM",</p><p>    virtualization: "true"</p><p>    ...</p><p>}</p>                    | <p>0xV354 (as validator)<br>{<br>    type: matching,<br>    storage: 100GB,<br>    estimated_duration: "6600 seconds",<br>    output_dir: "ds:0x9760/".<br>    data_strategy: "encryption",<br>    state: validated<br>....</p><p>}</p>                                           |

The example provided is intended solely for matching purposes within the training flow; however, the same structure applies to subsequent steps and inference flows. Each step functions in a fully decentralized manner and is executed on-chain. Importantly, all operations are conducted on top of the Nimble Matrix.
