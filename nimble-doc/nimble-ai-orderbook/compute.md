---
cover: >-
  https://images.unsplash.com/photo-1580777361964-27e9cdd2f838?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw5fHxjb21wdXRlfGVufDB8fHx8MTcxNDExNTE0OHww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Compute

## Context

The evolution of deep learning has propelled machine learning from smaller, manually-crafted models to expansive neural networks. Large Language Models (LLMs), for instance, can have billions to hundreds of billions of parameters, necessitating substantial GPU resources in terms of memory and processing power. For example, running a model like Llama 70B typically requires high-end GPUs such as the A100 or H100.

Despite this trend, the mantra "bigger is better" does not universally apply. In many business applications, such as spam detection, churn prediction, and credit scoring, smaller models suffice, and can effectively run on more accessible GPUs like the 1080 gaming card. This diversity in model size and business needs creates a varied landscape in AI compute requirements.

## Nimble's Value

### Efficient Resource Matching

Nimble strategically addresses this varied landscape by efficiently matching specific computational needs with appropriate GPU resources. Our platform manages a robust network of GPU providers, which has accumulated over 4 million training hours during a month-long proof of concept. This extensive experience allows Nimble to pinpoint the most cost-effective GPU for any given task, ensuring that resources are not only adequate but also economically optimized.

### Model Scalability by Segmentation

For exceptionally large models that cannot be supported by a single GPU—such as a hypothetical 100-billion-parameter model—Nimble offers a unique solution. Our system can decompose such models into 100 smaller segments, each with 1 billion parameters, making them manageable for commodity hardware to process.

### Miner Rewards

Ultimately, Nimble orchestrates GPU resources, distributing tasks across a network of miners who train the models, compile results, and commit transactions to the blockchain. This process rewards the miners for their contributions, creating a symbiotic ecosystem that drives the advancement of AI technologies.
