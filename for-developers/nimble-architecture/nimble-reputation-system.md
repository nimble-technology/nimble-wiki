# Nimble Reputation System

## Context

Each GPU miner has a reputation score that reflects their historical AI task completions and any fraudulent behaviors. The more legitimate work completed, the higher the reputation score. Conversely, the more fraudulent behaviors detected, the lower the reputation score. More mined and staked tokens also lead to a higher reputation score.

## **New Miners**

Initially, new miners are granted a small reputation score. They are assigned AI tasks based on this score during a slow-start period (currently 14 days). After this period, miners with no AI task completions receive a zero reputation score. Fraudulent miners receive negative reputation scores, and their Nimble mining rewards are slashed, while miners with high AI task completion rates enjoy boosted reputation scores.&#x20;

## Understanding Miners' Reputation Score

To ensure high-quality work from miners, Nimble leverages an evaluation flow that utilizes various techniques, such as using the MD5 hash of trained model snapshots and comparing loss values with Nimble's pretrained models. The result of this evaluation process is a boolean decision that determines whether a miner’s work is legitimate or fraudulent.&#x20;

For bootstrap historical data associated with a given miner’s wallet address, we have the following metrics:

* Total Number of Tasks Received by a Miner <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 11.59.31 AM.png" alt="" data-size="line">
* Total Number of Tasks Recognized as Cheating <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.00.02 PM.png" alt="" data-size="line">
* Total Number of Tasks Recognized as Good <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.00.30 PM.png" alt="" data-size="line">
*   Total Nimble Token Received <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.01.01 PM.png" alt="" data-size="line">

    &#x20; Based on total number of tasks recognized as _Good_

A miner’s reputation score _RS_ depends on:

* Total Staked token <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.06.16 PM.png" alt="" data-size="line">
* Total Nimble Token Received <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.01.01 PM.png" alt="" data-size="line">
* Cheat ratio <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.05.41 PM.png" alt="" data-size="line">
* Base Reputation Score <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.03.47 PM.png" alt="" data-size="line">
  * This score is based purely on the ratio of good tasks to cheating tasks.
* Impact Factor _IF_

**The Impact Factor**

The _Impact Factor_ represents a miner’s historical behavior, and will influence the miner’s chances of getting the task.

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.41.14 PM.png" alt="" width="375"><figcaption></figcaption></figure>

ɑ, β, ɣ are the factors that emphasize the miner’s normalized Slashing Factor.

* **Inactive** <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.42.38 PM.png" alt="" data-size="line">

When a miner turns off their machine, their chances of receiving tasks decrease the next time they restart it.

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.46.14 PM.png" alt="" width="375"><figcaption></figcaption></figure>

Where <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.46.51 PM.png" alt="" data-size="line">is the factor that emphasizes the miner’s normalized <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.42.38 PM (1).png" alt="" data-size="line">

* **Incomplete** <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.50.09 PM.png" alt="" data-size="line">

If miners fail to complete a task on time, their chances of receiving future tasks are reduced.

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.49.58 PM.png" alt="" width="375"><figcaption></figcaption></figure>

Where <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.51.07 PM.png" alt="" data-size="line"> is the factor that emphasizes the miner’s normalized <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.50.09 PM (1).png" alt="" data-size="line">

* **Cheating** <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.52.40 PM.png" alt="" data-size="line">

Based on the miner's track record, if their performance falls short compared to other miners, their chances of being assigned future tasks decrease.

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.54.37 PM.png" alt="" width="375"><figcaption></figcaption></figure>

Where <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.56.43 PM.png" alt="" data-size="line"> is the factor that emphasizes the miner’s normalized <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.52.40 PM (1).png" alt="" data-size="line">

The <img src="../../.gitbook/assets/Screenshot 2024-08-05 at 12.52.40 PM (2).png" alt="" data-size="line"> is based on the ratio of the amount of the miner's cheating to the amount of all miners in the previous mining period, such as the median, 80%, 95% positions.

> p95: red p80: yellow p50: blue

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdJWWWkqLDd6iY9N4fwKHoeKxeXE2M9tWD_d9Cuz1lhzU1hjzjXseselInFcyTmu0CW9vTsLUojkyCqfJKdx9jB6cXoSBpBSPw4lyF7ytp1sdQgg7c1fGiE64N-FQ9LiwVKCCg3_KIir3-Vv3CHhZsobtNe?key=Psa4WekwAwL9B-T9nK18Ow" alt="" width="375"><figcaption></figcaption></figure>

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkU87nET2B-TRnC8R-lbLIm-ACgaeGqtnre_w14Y4OTdVNePjUCxt3ThZu_bc6JvqiMO3w9xUejs94XIEfpRK3dcMJXhQqydMqoVhFGwMeMD_14-UdEaypE-LskBbCSB0LVIXFQg_4XBJMGE2PahtPVf1Z?key=Psa4WekwAwL9B-T9nK18Ow" alt=""><figcaption></figcaption></figure>

0 means he has never cheated, 100 means he is the most cheating among all miners.

### **Slashing**

Mined tokens are automatically staked for miners, but miners can also stake additional tokens to increase their reputation score. Fraudulent mining behavior results in a lower reputation score and slashed tokens.

* Penalty: $$SFpenalty$$

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-05 at 11.47.33 AM.png" alt="" width="563"><figcaption></figcaption></figure>

## Understanding Mining Power

Mining power captures the full mining capacity of miners, reflecting their ability to run AI tasks at full GPU capacity. Each miner’s mining power consists of two components:

* **Physical Mining Power:** Miners can increase their physical mining power by adding more GPUs or using higher-end GPUs.
* **Virtual Mining Power:** Miners can also increase their total mining power by purchasing virtual mining power, which provides equivalent mining rewards as physical mining machines.

## AI Task Distribution and Dynamic Rewards

AI tasks are distributed to miners through the AI orderbook **based on** their **reputation score** and **mining power**. The higher the reputation score, the better the chances of receiving AI tasks and, consequently, higher rewards. Miners with low reputation scores may not receive enough AI tasks to utilize their GPUs at full capacity, even if their mining power is high.

Miners can further enhance their reputation scores by completing more AI tasks and/or staking more Nimble tokens.

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-05 at 1.03.48 PM.png" alt="" width="563"><figcaption></figcaption></figure>

Maintaining high reputation scores is in miners' interests to secure higher mining rewards and avoid penalties for fraudulent behavior. Rewards are dynamic and depend on the network state, including AI task demand and GPU supply. Each task is tied to a specific mining reward, and the total rewards depend on the number of AI tasks completed and their associated rewards.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXesDpV-jYgyQ06TEQmK8-nArC1s5Wpd_7nXPjE9Hw9SaBH4ezkcO7cmWjK4ze2FEy0oI_3UCg7BeMpobsMa7MJOBrLWX7G3cT4Qi4bw5x0KCxQp5sc5rtk69TCLb7Im7wf4nKg9m-urIHZf81tWfWIkl7CI?key=Psa4WekwAwL9B-T9nK18Ow" alt="" width="563"><figcaption></figcaption></figure>
