# Publish

Once you've completed the model training and saved the results, the next step is to publish your model. This section guides you through using the `nimble-cli` to make your model available on the network.

## **Listing Models Ready for Publication**

Before you can publish a model, you need to identify which ones are fully trained and ready. Models still in training are not eligible for publication.

```python
nimble-cli list models
```

This command will display a list of models that are ready to be published.

## **Committing Your Model**

Choose a model to publish. You will need to provide the model's ID and your signature to commit it to the network.

```python
nimble-cli publish 
--id
--storage
--price_tag
--validator_type
--signature
```

## **Validation and Consensus**

Once submitted, your model will undergo a validation process where a model quality consensus algorithm assesses whether the model was properly trained and holds meaningful insights. This step ensures the integrity and reliability of models on the Nimble Network.

## **Final Note**

After your model is published, no further changes can be made to it. If you need to adjust the model or wish to build upon it, you must create a new trainer instance and go through the publication process again. This ensures that each model version remains distinct and traceable.
