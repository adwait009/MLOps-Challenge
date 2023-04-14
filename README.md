# MLOps-Challenge

This project is part of a challenge series from End-to-End MLOps with Azure Machine Learning Course.


## Notes

- Create a data asset
[az ml data (V2 ](https://learn.microsoft.com/en-us/cli/azure/ml/data?view=azure-cli-latest)
[CLI (v2) data YAML schema](https://github.com/Azure/azureml-examples/tree/main/cli/assets/data)

e.g.
``` yml
$schema: https://azuremlschemas.azureedge.net/latest/data.schema.json
name: diabetes-dev-file
version: 1
description: Dataset created from local file.
type: uri_file
path: experimentation/data/diabetes-dev.csv
```

## Learning Resources

[ MLOps (v2) solution accelerator](https://github.com/Azure/mlops-v2).

[ az ml job reference documentation](https://learn.microsoft.com/en-us/cli/azure/ml/job?view=azure-cli-latest)

[ Manage workspace assets with CLI (v2)](https://learn.microsoft.com/en-us/training/modules/create-azure-machine-learning-resources-cli-v2/4-manage-workspace-assets)

At the time of writing this Documentation Azure CLI(V2)'s documentation in the above link had some outdated documentation of (V)1 