# Publish

## **Listing Data Sets Ready for Publication**

Before you can publish a dataset, you need to identify which ones are fully ready.&#x20;

<pre class="language-python"><code class="lang-python"><strong>nimble-cli list data
</strong></code></pre>

This command will display a list of data that are ready to be published.

## **Committing Your Data**

Choose a data set to publish. You will need to provide the dataset ID and your signature to commit it to the network.

```python
nimble-cli publish
--id
--storage
--retention_period
--description
--schema
--signature
```

Again, make sure you mask private data well beforer publishing. Once it's done, all models and applications on chain will have access.&#x20;
