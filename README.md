# MLOps-Challenge

This project is part of a challenge series from End-to-End MLOps with Azure Machine Learning Course.


## Notes

- Create a data asset
[az ml data (V2)](https://learn.microsoft.com/en-us/cli/azure/ml/data?view=azure-cli-latest)
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

- Jobs
1. Command Jobs
2. Pipleline Jobs
3. Sweep Jobs

Run the Job using the following command
```
az ml job create --file job.yml
```

[CLI (v2) command job YAML schema](https://learn.microsoft.com/en-us/azure/machine-learning/reference-yaml-job-command?view=azureml-api-2)
[Example Jobs](https://github.com/Azure/azureml-examples/tree/main/cli/jobs)
[az ml Job reference](https://learn.microsoft.com/en-us/cli/azure/ml/job?view=azure-cli-latest)

e.g.
```yml
$schema: https://azuremlschemas.azureedge.net/latest/commandJob.schema.json
code: 
  local_path: src
command: >-
  python main.py 
environment: azureml:basic-env-scikit:1
compute: azureml:testdev-vm
experiment_name: customer-churn
description: Train a classification model on a sample customer dataset.
```

## Learning Resources

[ MLOps (v2) solution accelerator](https://github.com/Azure/mlops-v2).

[ az ml job reference documentation](https://learn.microsoft.com/en-us/cli/azure/ml/job?view=azure-cli-latest)

[ Manage workspace assets with CLI (v2)](https://learn.microsoft.com/en-us/training/modules/create-azure-machine-learning-resources-cli-v2/4-manage-workspace-assets)

At the time of writing this Documentation Azure CLI(V2)'s documentation in the above link had some outdated documentation of (V)1 

## Challenges
1. Use an Azure Machine Learning job for automation	0: Convert a notebook to production code - `Completed`
2. Use an Azure Machine Learning job for automation	1: Create an Azure Machine Learning job - Access not available to create compute resources
3. Trigger Azure Machine Learning jobs with GitHub Actions	2: Trigger the Azure Machine Learning job with GitHub Actions - Access not available to create compute resources
4. Trigger GitHub Actions with trunk-based development	3: Trigger GitHub Actions with trunk-based development
5. Work with linting and unit testing in GitHub Actions	4: Work with linting and unit testing
6. Work with environments in GitHub Actions	5: Work with environments
7. Deploy a model with GitHub Actions	6: Deploy and test the model

## Best practices

### Folder Structure
The proposed top-level folder structure for a MLOps (machine learning operations) repository is illustrated in the following diagram:

![repository-structure](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/cloud-scale-analytics/images/repository-structure.png)

The following purposes apply to each folder in the repository:

|Folder|Purpose|
|------|-------|
|**`.cloud`**|Store cloud-specific code and artifacts in this folder. The artifacts include configuration files for the Azure Machine Learning workspace, including compute target definitions, jobs, registered models, and endpoints.|
|**`.ado/.github`**|Store Azure DevOps or GitHub artifacts like YAML pipelines or code owners in this folder.|
|**`code`**|Include the actual code that's developed as part of the project in this folder. This folder can contain Python packages and some scripts that are used for the respective steps of the machine learning pipeline. We recommend separating individual steps that need to be done in this folder. Common steps are preprocessing, model training, and model registration. Define dependencies like Conda dependencies, Docker images, or others for each folder|
|**`docs`**|Use this folder for documentation purposes. This folder stores Markdown files and images to describe the project.|
|**`pipelines`**|Store Azure Machine Learning pipelines definitions in YAML or Python in this folder.|
|**`tests`**|Write unit and integration tests that need to be executed to discover bugs and issues early during the project in this folder.|
|**`notebooks`**|Separate Jupyter notebooks from the actual Python project with this folder. Inside the folder, each individual should have a subfolder to check in their notebooks and prevent Git merge conflicts.|