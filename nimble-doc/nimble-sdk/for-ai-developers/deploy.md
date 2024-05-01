# Deploy

After your model has been successfully committed to the network, you have the opportunity to deploy it to make it public to internet, or private to nimble network only. This allows functionality similar to well-known model providers, but from different domains. In this section, we'll guide you through the deployment process using the `nimble-cli` tool.

## **Listing Deployable Models**

Not all models may be ready for deployment. To check which models can be deployed:

```python
nimble-cli list models
```

This command will display a list of models that are ready and eligible for deployment.

## **Deploying Your Model**

Select a model that is ready for deployment and provide your signature to authorize the deployment:

```python
nimble-cli deploy 
--id
--auto_scaling
--public
--example_input
--example_output
--price_tag
--signature
```

## **Accessing Your Model**

After deploying your model, it will take a few minutes to activate. Once activated, you will receive a dedicated API endpoint. This API allows users to interact with your model similar to how they would with other online AI services.

## **Earning Tokens**

An exciting aspect of deploying your model is the potential to earn tokens. Each time someone accesses your model via the API, you will receive tokens as a form of compensation for providing computational resources and model access.
