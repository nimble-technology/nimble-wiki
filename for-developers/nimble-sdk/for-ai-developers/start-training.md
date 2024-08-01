# Start training

The `nimble-cli` and `NimbleSDK` are always available in this training environment. They are designed to work together streamline the training process, ensuring a unified flow and providing essential resources like GPU connection and reporting tools. Carefully read the doc and use `nimble-cli` to manage those critical steps in the training flow. Below, we detail how to use this cli effectively.

## **Pre-Process**

Define a trainer file. Assume we name it `my_trainer.py`&#x20;

Before you start training your model, preparation is crucial.

```python
from NimbleSDK import NimbleTrainer

class MyTrainer(NimbleTrainer):
    def pre_process(self, **kwargs):
        pass
```

**Functionality:** In the `pre_process` method, you should handle tasks such as downloading training dataset and eval dataset, defining model hyper parameters,  setting up tokenization and creating pipes. This method serves as the entry point of your program.

## **Train**

The actual training of the model is managed through the `train` method.

```python
class MyTrainer(NimbleTrainer):
    def train(self, **kwargs):
        pass
```

**Functionality:** Define your model architecture within this method, load pre-trained models, specify the output format and path, and initiate the training process. This stage is typically the most time-consuming.

## **Evaluate**

After training, assessing your model’s performance is critical.

```python
class MyTrainer(NimbleTrainer):
    def evaluate(self, **kwargs):
        pass
```

**Functionality:** In the `evaluate` method, set the success criteria for your model. While accuracy and precision are popular metrics, consider using those specific metrics for transformers or diffusers. Typically, you will compare your model's performance against pre-trained models using the same dataset to see if yours can outperform them. Or you can compare with other foundational models if you train from scratch. Pre-trained models and foundational models are available in the NimbleSDK.&#x20;

## **Show Example**

Finally, demonstrate the practical application of your model.

```python
class MyTrainer(NimbleTrainer):
    def predict_and_show(self, **kwargs):
        pass
```

**Functionality:** This method should be used to generate a few human-readable outputs such as texts, images, videos, or audios from respective inputs. Remember, the purpose here is illustrative, so limit the number of outputs to avoid excessive use of resources.

## Kick off the training

```
nimble-cli train my_trainer.py 
--GPU_info
--notification
--auto_retry
--report_usage
--validator_type 
--signature
```
