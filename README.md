# MLOps-Challenge

This project is part of a challenge series from End-to-End MLOps with Azure Machine Learning Course.


## Notes

- Create a dataset asset

To create a dataset asset from a local file, you'll need to:

- Create a YAML specification file referring to the local file.
- Run the az ml dataset create command.

In the YAML file you'll include:

- The name of the dataset asset as it will show in the workspace.
- The version of the dataset asset.
- The local path to the data file.
- Optionally, you can add a description.

``` yml
$schema: https://azuremlschemas.azureedge.net/latest/asset.schema.json
name: diabetes-dev-folder
version: 1
local_path: diabetes-dev.csv
description: Dataset pointing to customer churn CSV on local computer. Data will be uploaded to default datastore.
```

## Learning Resources

[ MLOps (v2) solution accelerator](https://github.com/Azure/mlops-v2).

[ az ml job reference documentation](https://learn.microsoft.com/en-us/cli/azure/ml/job?view=azure-cli-latest)

[ Manage workspace assets with CLI (v2)](https://learn.microsoft.com/en-us/training/modules/create-azure-machine-learning-resources-cli-v2/4-manage-workspace-assets)