---
description: Training our LAM to generate intents from natural language
---

# Natural Language Intents

Nimble is building intent infrastructure to enable transparent use of Web3 components in Web2 applications. To get there, we need to make unique components of Web3 invisible to end users.

Complexity doesn’t go away - it’s just moved elsewhere in the stack. When developers build traditional Web2 apps, complexity exists in the application code. Interactions are exposed to users as contextually obvious components. With our network, the complexity of interacting with blockchain infrastructure is moved into the intent layer.

### Intent Interface

Developers and users, then, need an interface to interact with the intent layer. We are carefully thinking about how to best expose intents to users.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Chat based interface for Web3</p></figcaption></figure>

Any good solution will have the following properties:

#### Nonsense Intent Prevention

The network supports only a fixed set of intent operations at any given time. It can’t, for instance, fold your laundry for you. The ingest layer must prevent unfulfillable intents from entering the network.

While advanced users may override the default behaviors, most input will be processed by an interaction layer.

#### **Data Collection**

To ensure intents can be fulfilled, certain data must be available. To transfer tokens, for instance, an intent must contain the source, destination, quantity, and a signature at minimum.

The intent ingestion layer must gather these data before submitting intents to the network.

### Intents by LAM

In this article, we detail how we trained a publicly available Large Action Model (LAM) to process swap intents as plain language and generate intent DSL. LAM differentiates from LLM by guiding users with followup questions and translating intents into specific on-chain and off-chain operations.

#### The Architecture

The output of this LAM can be processed deterministically by the intent network without exposing blockchain internals to users.



Architecture for fine-tuning of the open-source LAM. The model comes pre-trained, but must be fine-tuned to respond to intent operations and generate meaningful output.

For our swap intent understanding model, we used a large language model’s transformer architecture. The model is based on a self-attention mechanism that focuses on different parts of the input query, enabling it to capture dependencies in the sentence. This enables the model to understand the context and meaning of words better and generate more accurate and coherent responses.

In the LAM transformer model, the transformer model is scaled up and trained on large amounts of textual data. It has a vast number of parameters, allowing it to capture a broader range of language patterns. However, this model must still be fine-tuned for tasks such as token swap understanding.

#### Tailored LAM

Fine-tuning is a technique to train LAM models to improve their language processing abilities. Fine-tuning involves taking a pre-trained language model and further training it on a specifically crafted dataset.

During the fine-tuning process, only some layers of the model's parameters are adjusted based on the specific dataset and task. The pre-trained model serves as a foundation of natural language understanding by fixing the bottom layers of parameters. By training on a specific dataset, the model gains a deeper understanding of the domain and becomes more accurate and effective in performing the desired language-related task. We fine-tune the model for the chatbot interface for query understanding.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Sample formatted intent</p></figcaption></figure>

The model is capable of processing intents in the following manner:

1. Understanding the swap query to parse and extract all parameters for the swap intent. Some parameters are required, and some are optional.
2. If some required parameters are missing, the model will ask follow-up questions until it gets all the info.
3. The model will convert the query to JSON format for auto-processing.
4. Intents that fail to match the pattern are not understood and, thus, not used by the model

#### Intent Interactions

Example user interactions to illustrate the power of the LAM intent action recognition model and how the model guides users for optimal Web3 UX:

<figure><img src="https://lh7-us.googleusercontent.com/Qkm3Hv45uQag08t_OmEKDRAVnBFDSpTX_WXs4lIoxpMECIHLY-E__-BVKG9vRRneNtpvuFcV-44uxunvYqhuoiCKFMAa1BokR_Ag2hDESB_Dd7g55ZhhZ9i3UrOxu7T0Bs0kjDuvKgq01L4nX-qDqlc" alt=""><figcaption><p>Additional supported plain-language interactions with the LAM</p></figcaption></figure>

### Extended Functionality

Currently, the chat interface for our intent network is a prototype and only supports the swap operations. Additional operations can be easily added by further training the model.

This proof of concept demonstrates how functionality is added to the model, and the interaction developers can expose to users within their applications with Nimble.

#### Beta Launch

Before the network beta launch, we aim to support the following additional operations in the language model:

1. Send (transfer)
2. Stake
3. Single withdraw
4. Bulk withdraw
5. Recurring send (ie., payroll)

#### Generic Intents

After beta launch, the network will support generic intents like AI, E-Commerce, NFTs etc. with an ecosystem first approach.

To request additional operations at launch, join our Discord. [https://discord.gg/bG6vjyBX8J](https://discord.gg/bG6vjyBX8J)
