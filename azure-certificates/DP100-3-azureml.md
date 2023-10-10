
## Azure ML workflow

1. __Get the data__
	- Enter data manually
	- Import data from clous services outside of Azure ML
	- Unpack zipped dataset
2. __Prepare the data__
	- Clean missing data
	- Split data in training and test
3. __Feature selection__
	- Filter based feature selection
	- Pearson correlation, etc.
	- Fisher Linear Discriminant Analysis
	- Permutation Feature Importance
4. __Choose and apply learning algorithms__
	- Tweaking model parameters
5. __Train and evaluate the model__

## Azure Machine Learning Archutecture and Concepts

![[azureml-architecture.svg]]
  
- Linked Services > Datasotres aree for training data etc.
- Dependencies > Azure Storage Account us for logs etc.
- Dependencies > Azure Container Registry is for deployment of models

### Data sets or Data assets (AzureML Concept)

Data sets can be used within Azure ML Workspace in:

- Notebook Script
- Automated ML
- Designer
- Experiment

To create a dataset, various input sources can be used:

- From __local files__: create a data asset by uploading files from your local drive.
- From __Azure storage__: create a data asset from registered data storage services including Azure Blob Storage, Azure file share, and Azure Data Lake.
- From __web files__: create a data asset from a single file located at a public web URL.
- From __Open Datasets__: create a dataset with one-click from pre-made data sets. These data sets are created by the general public and published as Azure Open Datasets.

If you use Azure storage as input source, you have to link a storage container (e.g. Blob storage) to the Azure ML workspace using a Datastore.

Datastore stores contain connection information to other data sources within Azure (Blob, Files, Data Lake, Azure SQL, PostgreSQL, MySQL, Azure Databricks, etc.). In that sense it's more like a "Data Connector".

### Compute Resources

#### Azure ML Managed Resources (Compute Instances & Compute Clusters)

Compute Instances & Compute Clusters are directly integrated with AzureML Workspace.

##### Compute Instances:

- __are best for development in notebooks in Python or R environment__
- are workstations for data scientists
- contain R and PythonTools environment, as well as Docker and AzureML SDK
- have everything configured and pre-installed for you

Compute Instances are typically used in a development environment with notebooks and data profiling. Can also be used for small training and inferencing for development and testing.

##### Compute Clusters:

- __are best for development using Designer or AutoML__
- are a group of VMs Single or multiple nodes
- can be used for all authors (Designer, SDK, etc.)
- can be used for traning the pipeline and experiment run

#### Azure ML Linked Services (Compute Target)

##### Remote/Attached Compute:

- __are best for testing your deployment__
- Local MAchine, Compute Instance, Clusters, VMs
- Usef for training or test deployment
- Computer cluster for Batch inferencing

##### Inference Clusters:

- __are best for real-time deploy__
- Azure Kubernetes Services running on AKS Cluster
- Highly scalable production deployment
- For real-time inferencing

## Azure ML Pipeline

### 1. Data Processing

- Data Ingestion
- Data Validation
- Feature Engineering
- Feature Selection

### 2. Build and Train Model
- Model Training
- Cross Validation
- Hyperparameter Tuning
- Model Selection

### 3. Deploy and Monitor

- Model Deployment
- Inferences/Predictions
- Monitor Results

## Benefits new Azure ML Studio

- Datastore to save all the configurations of a storage and then use as many datasets or files from that storage as needed. Can also be used to store intermediate data.
- Possibility to set different compute targets for different steps in the pipeline

## AutoML

AutoML can do: (1) classification, (2) regression, (3) time series forecasting

[[azure]] [[azureml]]