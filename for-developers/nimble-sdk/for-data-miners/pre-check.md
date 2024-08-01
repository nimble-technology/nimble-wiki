# Pre check

Ensure your dataset adheres to the network's data standards, including anonymization and formatting.&#x20;

```
nimble-cli load my_data/ 
--schema
--stream
--report_details
```

Do a local validation before proceeding, including personal information leakage, format, distribution, duplicaiton, etc.

```
nimble-cli check 
--id
--report_details
--stop_early
--signature
```

