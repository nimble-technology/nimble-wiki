---
cover: >-
  https://images.unsplash.com/photo-1580777361964-27e9cdd2f838?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw5fHxjb21wdXRlfGVufDB8fHx8MTcxNDExNTE0OHww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Compute

## Context

The evolution of deep learning has transformed machine learning from small, manually-crafted models to expansive neural networks. Large Language Models (LLMs), for example, now contain billions to hundreds of billions of parameters, requiring significant GPU resources in terms of memory and processing power. For instance, running a model like Llama 70B typically requires high-end GPUs such as the A100 or H100.

However, the idea that "bigger is better" doesn't apply universally. Many business applications, such as spam detection, churn prediction, and credit scoring, can effectively run on smaller models using more accessible GPUs like the 1080 gaming card. This diversity in model size and business needs creates a varied landscape in AI compute requirements.

## Nimble's Value

### Efficient Resource Matching

Nimble addresses this diverse landscape by efficiently matching specific computational needs with the appropriate GPU resources. Our platform manages a vast network of GPU providers, which has accumulated over 4 million training hours during a month-long proof of concept. This experience allows Nimble to identify the most cost-effective GPU for any task, ensuring resources are both adequate and economically optimized.

### Model Scalability by Segmentation

For exceptionally large models that cannot be supported by a single GPU—such as a hypothetical 100-billion-parameter model—Nimble offers a unique solution. Our system can decompose such models into 100 smaller segments, each with 1 billion parameters, making them manageable for commodity hardware to process.

### Miner Rewards

Nimble orchestrates GPU resources, by distributing tasks across a network of miners who train the models, compile results, and commit transactions to the blockchain. This process rewards the miners for their contributions, creating a symbiotic ecosystem that drives the advancement of AI technologies.
