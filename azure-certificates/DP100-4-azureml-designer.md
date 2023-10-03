## Running a pipeline in the Designer

- First time you run the pipeline takes significantly longer, as the VM needs to be set up, packages need to be installed, etc.

## Deployment

Two deployment options:

1. Real-time inference pipeline (REST endpoint)
2. Batch inference pipeline (storage csv)

## Using Python Scripts in AzureML Designer

Requirements:
- Method must be called `azureml_main`
- Output has to be a Pandas Dataframe
- It's similar to the `PythonScriptStep` in the AzureML SDK
- You can add a Script bundle ZipFile to add modules that can then be accessed in the `azureml_main` method. Make sure to register ZipFile as registered dataset with dataset type `File`.

Example:

```python
import pandas as pd

def azureml_main(df1 = None, df2 = None):
	df = df1
	df = df.drop(["fw", "edu_num"], axis=1)
	X = df.iloc[:, :-1]
	Y = df.iloc[: -1:]
	return X, Y
```
