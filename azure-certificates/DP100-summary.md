## 1- Objective: Set up an Azure Machine Learning Workspace

- The method `run.wait_for_completion()` with the attribute `show_output=True` configures logging to only show logs after the script execution is completed.
-  You need to update the storage keys in the workspace after regenerating them: `az ml workspace sync-keys`
- AzureML Editions:
	- For image classification projects, the Enterprise edition of AzureML is needed. The Basic edition of AzureML does not support machine learning assisted image classification.
- Setting up an image classification project:
	1.  Choose Image ==Classification Multi-class== as the labeling task type.
	2.  Select or create a ==dataset== associated with storage where the images reside.
	3.  Ensure that the ==Incremental refresh== option is turned on.
	4.  Create the list of ==label classes== against which you want to categorise your images.
	5.  Provide any ==instructions== for the labellers on the process of classification.
	6.  Ensure that the ==Enable ML assisted labeling== is turned off.

```python
# --------------------------------------------------------
# Workspace
# --------------------------------------------------------
ws = Workspace.from_config(path="./.azureml/ws_config.json")
ws = Workspace(
	<subscription_id>, 
	<resource_group>, 
	<workspace_name>
)

# --------------------------------------------------------
# Environment
# --------------------------------------------------------
myenv = Environment(name="MyEnvironment")
myenv_dep = CondaDependencies.create(conda_packages=['scikit-learn'])
myenv.python.conda_dependencies = myenv_dep
myenv.register(ws)

# --------------------------------------------------------
# Compute
# --------------------------------------------------------
compute_config = AmlCompute.provisioning_configuration(
	vm_size="STANDARD_D11_V2",
	max_nodes=2
)
cluster = ComputeTarget.create(
	workspace=ws,
	name="my-cluster-001",
	compute_config=compute_config
)
cluster.wait_for_completion()

# --------------------------------------------------------
# Pipeline
# --------------------------------------------------------
run_config = RunConfiguration()
run_config.environment = myenv
run_config.target = compute_cluster

data_folder = PipelineData(
	"datafolder",
	datastore=ws.get_default_datastore()
)
dataprep_step = PythonScriptStep(
	name="01 Data Preparation",
	source_directory=".",
	script_name="01-dataprep-step.py",
	inputs=inputs,
	outputs=outputs,
	runconfig=run_config,
	arguments=arguments
)
pipeline = Pipeline(
	workspace=ws,
	steps=[dataprep_step]
)

# --------------------------------------------------------
# Experiment
# --------------------------------------------------------
experiment = Experiment(
	workspace=ws,
	name="PipelineExp01"
)

# --------------------------------------------------------
# Run
# --------------------------------------------------------
# With pipeline
run = experiment.submit(config=pipeline)
run.wait_for_completion(show_output=True)

# Without pipeline with script
script_config = ScriptRunConfig(
	source_directory=".",
	script="02-script.py",
	environment=myenv
)
run = experiment.submit(config=script_config)
run.log("Name", value)
run.wait_for_completion()

# Without script and pipeline
run = experiment.start_logging(snapshot_directory=None)
run.complete()

# --------------------------------------------------------
# Step in pipeline
# --------------------------------------------------------
run = Run.get_context()
ws = run.experiment.workspace
df = run.input_datasets["raw_data"].to_pandas_dataframe()
run.complete()

# --------------------------------------------------------
# Datastore
# --------------------------------------------------------
az_store         = Datastore.get(ws, "blob_azureml_sdk_01")
az_default_store = ws.get_default_datastore()

az_store         = Datastore.register_azure_blob_container(
	workspace=ws,
	datastore_name=datastore_name,
	account_name=account_name,
	container_name=container_name,
	account_key=account_key
)

# --------------------------------------------------------
# Dataset
# --------------------------------------------------------
dataset       = Dataset.get_by_name(ws, name='bike_sharing_data')

csv_path     = [(az_store, "bike_sharing/hour.csv")]
bike_dataset = Dataset.Tabular.from_delimited_files(path=csv_path)
bike_dataset = bike_dataset.register(
	workspace=ws,
	name="bike_sharing_data",
	create_new_version=True
)

az_df_from_df = Dataset.Tabular.register_pandas_dataframe(...)

files_list = ["./folder_with_test_data/test.csv"]
az_store.upload_files(files=files_list, target_path="", relative_root="")
az_store.upload(src_dir="", target_path="", overwrite=True)

# --------------------------------------------------------
# Explainer
# --------------------------------------------------------
tab_explainer = TabularExplainer(
	trained_model,
	X_train,
	features=features,
	classes=classes
)

global_explanation = tab_explainer.explain_global(X_train)
global_fi          = global_explanation.get_feature_importance_dict()

X_explain          = X_test[0:5]
local_explanation  = tab_explainer.explain_local(X_explain)
local_features     = local_explanation.get_ranked_local_names()
local_importance   = local_explanation.get_ranked_local_values()

# Uploading to workspace
explain_client     = ExplanationClient.from_run(run)
explain_client.upload_model_explanation(explanation, comment="Label")
downloaded_expl    = explain_client.download_model_explanation()
global_fi          = downloaded_expl.get_feature_importance_dict()

# --------------------------------------------------------
# Hyperdrive / Hyperparameter tuning
# --------------------------------------------------------
hyper_params = GridParameterSampling({
	'--n_estimators': choice(10, 20, 50, 100),
	'--min_samples_leaf': choice(1, 2, 5)
})
hyper_config = HyperDriveConfig(
	run_config=script_config,
	hyperparameter_sampling=hyper_params,
	policy=None, # early-termination
	primary_metric_name='accuracy',
	primary_metric_goal=PrimaryMetricGoal.MAXIMIZE,
	max_total_runs=20,
	max_concurrent_runs=2
)
run = experiment.submit(config=hyper_config)
run.get_best_run_by_primary_metric()

# --------------------------------------------------------
# AutoML
# --------------------------------------------------------
automl_config = AutoMLConfig(
	task='classification',
	compute_target=cluster,
	training_data=input_ds,
	validation_size=0.3,
	label_column_name='Default Next Month',
	primary_metric='norm_macro_recall',
	iterations=10,
	max_concurrent_iterations=2,
	experiment_timeout_hours=0.25,
	featurization='auto'
)
run = experiment.submit(automl_config)
run.get_best_child(metric='accuracy')
```

## 2 - Objective: Run Experiments and Train Models

- The `polling_interval` configures the frequency at which the datastore is checked for any changes. It does not set an experiment run interval.
- The `script_params` property consists of the dictionary of command-line arguments to pass to the training script specified in the `entry_script` property.
- Data in pipelines
	- You need to ensure that files can be passed between pipeline steps using a named datastore:
		1.  Register a new Azure Storage file container datastore.
		2.  Create a PipelineData object. Specify a name and output datastore.
		3.  Specify a PipelineData object for data output.
	- Several options to store experiment output:
		1. Storage on local compute, but not persistent
		2. Datastore
		3. Write to `./outputs` or `./logs` folder, `./logs` folder are uploaded in real time
	- You can use the Select Columns in Dataset module to identify the columns that should be processed and sent to the next pipeline element. By default, no columns are selected, and you will receive an error indicating that a value is required until you select at least one column.
	- You design and log a monitoring solution for a Linux-based ==Azure HDInsight== solution that is used to analyse large volumes of data. Various operations will execute continuously on the cluster. You need the logging solution to be able to monitor the performance of the cluster. You want to minimise the configuration effort associated with implementing the monitoring solution. You should use ==Apache Ambari==, this simplifies the management and monitoring of Hadoop clusters by providing an easy-to-use web UI backed by its REST APIs. Ambari is provided by default with a Linux-based HDInsight cluster, so configuration efforts are reduced. 
	- To consume data from the ==default workspace== datastore in an experiment when using the AzureML SDK, either:
		1.  Use the `get_default_datastore` method of the workspace object
		2.  Create a reference to `workspaceblobstore` using the `Datastore` class
- Training video game machine learning models uses a process known as ==reinforcement learning== (RL). Because RL is compute intense, it is typically performed across multiple compute nodes, known as head and worker nodes. In Azure Machine Learning, RL requires that you specify a virtual network that does not block the ports that nodes need to communicate.
- You can use Azure ML SDK to create, manage workspaces and experiments. If you want to use Azure ML Studio to view associated experiment graphs or individual runs, you can call the ==experiment variable== to generate an ==Azure ML Studio link==. Following this link takes you to the Azure ML Studio page for your experiment.
- Regularization:
	- L1 (Lasso) can shrink some coefficients to zero, performing variable selection.
	- L2 (Ridge) shrinks all the coefficients by the same proportions but eliminates none


## 3 - Objective: Optimise and Manage Models

You need to monitor and analyse drift in your data as new information is collected from your IoT devices:
-   You define a dataset monitor and configure a target dataset with timeseries trait. 
-  You can define a dataset monitor if you want to monitor for statistical changes and data drift in your datasets. 
- Each dataset monitor requires a baseline dataset and a target dataset.
- This target dataset must have the timeseries trait set, which is typically done by adding a timestamp column.

### Explainability

- `TabularExplainer` calls one of the tree ==SHAP explainers== (`TreeExplainer`, `DeepExplainer` or `KernelExplainer`)
- `TabularExplainer` automatically selects the most appropriate one for use case. 
- Only `KernelExplainer` is model agnostic, rest of SHAP explainers is model specific.
- `MimicExplainer` creates a surrogate model to ==mimic the behavior== of a black box model
- `PFIExplainer` ==permutation feature importance==

### Hyperparameter tuning

- Sampling methods
	- ==Random Sampling== (you can't specify specific discrete values)
	- ==Grid Sampling== (only discrete values)
	- ==Bayesian Sampling== (does not support early terminatioin & you can't specify specific discrete values)
- Early termination
	- ==Bandid Policy== (slack/slack factor)
	- ==Median Stopping== Policy
	- ==Truncation Selection== Policy (exclude lowest X% runs)

### AutoML

- Algorithms that can be used by AutoML models and support exporting to ONNX (Open Neural Network Exchance) models are: Random Forest and Decision Tree. 
	- Auto-ARIMA is only suited for time series forecasting and cannot be exported to ONNX models. 
	- Linear SVC based classification models can be exported to ONNX models, but they are only suited for data classification problems.

## 4 - Objective: Deploy and Consume Models

| Compute target | Usage | Description |
|----------------|-------|-------------|
| Local web service | Testing/debug | Good for limited testing and troubleshooting.|
| Azure Kubernetes Service (AKS) - inference clusters | Real-time inference | Good for high-scale production deployments. Provides autoscaling, and fast response times. |
| Azure Container Instances (ACI) | Testing | Good for low scale, CPU-based workloads. |
| Azure Machine Learning Compute Clusters | Batch inference | Run batch scoring on serverless compute. Supports normal and low-priority VMs. |
| Azure IoT Edge | (Preview) IoT module | Deploy & serve ML models on IoT devices. |

- Compute:
	- **Managed Resources**:
		- **==Compute Instances==** are best small training/inferencing tasks for development/testing
		- **==Compute Clusters==** are best for traning the pipeline and experiment run
			- Scalable ML platforms consisting of one or more CPU or GPU nodes. 
			- Use low-priority VMs and can scale, but may not scale to the load required.
			- VM availability is not guaranteed, thus the provided service is not real-time.
			- Not for pipeline deployment, this is not supported. 
	- **Linked Services**:
		- **==Remote/Attached Compute==** are best for training or testing deployment and to be used with Databricks (local, VMs)
		- **==Inference Clusters==** are best for real-time deployment (AKS Cluster)

- You create a model using the Designer. You click train the model, click Publish button on the designer canvas, select the Create new radio button and click Publish:
	- ==Publish== button 
		- will publish the pipeline with a REST endpoint to the pipeline that other users/developers can make calls to. It provides an endpoint with a key-based authentication.
		- will not deploy model as a web service endpoint. 
		- does not run the pipeline (requires ==Submit==)
	- ==Deploy== button
		- will deploy model as a web service endpoint.

- ==You use Azure ML Designer to create an inference pipeline and train a predictive model. You need to deploy your pipeline as a web service that can autoscale based on workload:==
	1.  Convert the training pipeline into a real-time inference pipeline
	2.  Create an Azure Kubernetes Service (AKS) cluster
	3.  Deploy a real-time endpoint
	
- ==You use Azure ML to train and deploy a model as a web service. Your web service requires authentication. You need to test the deployment to ensure that requests to the web service will be successful:==
	1.  Retrieve the `scoring_uri` property of a Webservice object. When a model is deployed as a web service, a REST interface is defined, which client applications can use to consume the service. You determine the service endpoint by using the Azure ML SDK to retrieve the `scopring_uri` property of a Webservice object.
	2. Specify `bearer authentication` in the header. As the published model requires authentication, you will need to define an HTTP request header in your code that specifies bearer authentication. 
	3. Issue an `HTTP POST` request with JSON data. Once your code is complete, you can issue an HTTP POST request to the published service endpoint you discovered using the `scoring_uri` property

- You use AzureML to deploy. Model to an Azure Kubernetes Service cluster. During testing, you receive a large number of HTTP 503 errors. The HTTP 503 error indicates that the service is operational but is unable to respond to requests. This often indicates that the server is overloaded and does not have the resources to process the request. You need to reduce the incidence of HTTP 503 errors:
	-   Change the minimum number of ==replicas==. This parameter defines the minimum number of nodes that should be online in an AKS cluster. 
	-   Modify the `autoscale_max_replicas` parameter. By default an AKS cluster can scale up to 10 containers.
	-   Change the ==utilisation level== at which containers autoscale up: if there is a sudden increase in requests, the cluster may not be able to add nodes quickly enough to handle the requests. By reducing this threshold, you allow the cluster to scale up under lighter loads.

## Real time inferencing

- You create and train a model using Azure ML Studio. The model takes in CSV data as the source. You need to identify the steps to deploy the model as a real-time service and ensure that the endpoints are accessible to users of the service:
	1.  Create pipeline
	2.  Test endpoint
	3.  Deploy enpoint 
	4.  Create inferencing cluster
- You plan to deploy the model as a real-time web service using your local system:
	1.  Install Docker on your local machine
	2.  Specify the service’s endpoint port where requests will be accepted
		- Models deployed locally as a web service will accept requests on an HTTP endpoint. Once your container has the required dependencies installed, you will need to define the port where the HTTP endpoint will listen for service requests. 

## Batch inferencing

- You use Azure ML to create and publish a batch inference pipeline. To meet regularory requirements, your pipeline endpoint has been scanned for vulnerabilities. You want to test some changes, but you need to ensure that the existing pipeline is not modified. You also need to ensure that the pipeline endpoint is not changed:
	1.  Create a new pipeline that implements your changes.
	2.  Publish the pipeline to your scanned endpoint
		- AzureML allows you to publish multiple pipelines under the same endpoint. When this occurs, each published pipeline is assigned to a version number, which can be provided in REST API calls. 
	3.  Include the test pipeline version in your REST calls
		- In this question, you want to preserve the existing pipeline, so you should create a new pipeline that implements your changes. You can then publish this pipeline under your existing endpoint. 
- You use AzureML Designer to create a batch inference pipeline. You plan to publish the pipeline using a web service. You need to ensure that the pipeline can make predictions on the new data supplied at runtime. Therefore, you should create a ==parameter for your dataset==. This option allows consumers to provide a dataset to your pipeline at runtime. 

### `ParallelRunStep`

- Your clients want to be able to make calls to a batch inference pipeline to execute a large volume of data that is periodically uploaded to a storage account. You want to create a pipeline that leverages the `ParallelRunStep` to run an inferencing script to provide outcomes to your client. You need to write a batch inference script, you should include:
	- `init()` for any costly or common preparation for later inference
	- `run(mini_batch)` to write code that would evaluate and append the outputs of the evaluation 
- You create a batch inference pipeline that leverages `ParallelRunStep` for multi-node processing. 
	- To stream run logs and monitor the run status you add: `pipeline_run.wait_for_completion()`. This method is used to monitor the status and by default , it will store the logs to the output determined by the `sys.stout` configuration. 
	- The `pipeline_run.get_status()` will retrieve the status of the run, but it will not provide streaming logs while the pipeline is being executed.

## Authentication

- **Key**: Requests are authenticated by specifying the key associated with the service.
	- Assuming you have an authenticated session established with the workspace, you can retrieve the keys for a service by using the **get_keys** method of the **WebService** object associated with the service.
- **Token**: Requests are authenticated by providing a JSON Web Token (JWT).
	- For token-based authentication, your client application needs to use service-principal authentication to verify its identity through Azure Active Directory (Azure AD) and call the **get_token** method of the service to retrieve a time-limited token.
- Default ACI is disabled and AKS is key-based.
- Both token-based and key-based authentication cannot be enabled at the same time

## 5 - Other

### Differential privacy

- Seeks to protect individual data values by adding statistical "noise" to the analysis process.
- The lower the epsilon, the less impact an individual's data has on aggregated results, and therefore the risk of exposure is reduced.

### Model fairness

- Let's say that we find that the recall for validation cases where the applicant is 25 or younger is 0.50, and recall for cases where the applicant is over 25 is 0.83. The disparity in prediction performance between the groups is 33%, with the model predicting significantly more false negatives for the younger age group.
- Causes of disparity:
	- Data imbalance
	- Indirect correlation
	- Societal biases
- Mitigating bias:
	- Balance training and valudation data
	- Perform extensive deature selection and engineering analysis
	- Evaluate models for disparity based on significant features
	- Trade-off overall predictive performance for the lower disparity in predictive performance between sensitive feature groups.
- Fairlearn python package
	- Mitigation techniques:
		- Exponentiated Gradient: A _reduction_ technique that applies a cost-minimization approach to learning the optimal trade-off of overall predictive performance and fairness disparity.
		- Grid Search: A simplified version of the Exponentiated Gradient algorithm that works efficiently with small numbers of constraints
		- Threshold Optimizer: A _post-processing_ technique that applies a constraint to an existing classifier, transforming the prediction as appropriate

### Security concepts

#### Role-based access control

- Custom roles can be created by defining possible `Actions` permitted and `NotActions` to restrict specific activities or access.
- Authentication with Azure AD:
	- **Interactive**: during experimentation and iterative development.
	- **Service Principal**: used when you need an automated process to authenticate to the service.
	- **Azure CLI session**: used during experimentation and iterative development, or when you need an automated process to authenticate to the service using a pre-authenticated session.
	- **Managed Identity**: allows the VM to connect to the workspace using the managed identity, without storing credentials in code or prompting the user to authenticate.
- Managed Identites:
	- **System-assigned**: only that Azure resource can use this identity to request tokens from Azure AD, and when the resource is deleted, Azure automatically deletes the identity for you.
	- **User-assigned**: identity is managed separately from the resources that use it and will persist if a resource using it is removed.

#### Secure your AzureML network

- An **Azure VNet (Virtual Network)** is the fundamental building block for your private network in Azure. VNet enables Azure resources, such as Azure Blob Storage and Azure Container Registry, to securely communicate with each other, the internet, and on-premises networks. VNet is similar to a traditional network that you'd operate in your own data center, but brings with it additional benefits of Azure's infrastructure such as scale, availability, and isolation.\
- Typical structure for VNet is comprised of:
	- **IP address space**
	- **Subnets**: subnets enable you to segment the virtual network into one or more sub-networks and allocate a portion of the virtual network's address space to each subnet, enhancing security and performance.
	- **Network Interfaces (NIC)**: interconnection between a VM and a virtual network (VNet)
	- **Network security groups (NSG)** can contain multiple inbound and outbound security rules that enable you to filter traffic to and from resources by source and destination IP address, port, and protocol.
	- **Load balancers** can be configured to efficiently handle inbound and outbound traffic to VMs and VNets, while also offering metrics to monitor the health of VMs.
- Azure Private Link:
	- **Private endpoint** – a network interface connected to your virtual network, assigned with a private IP address. It is used to connect privately and securely to a service powered by Azure Private Link or a Private Link Service that you or a partner might own.
	- **Private Link Service** – your own service, powered by Azure Private Link that runs behind an Azure Standard Load Balancer, enabled for Private Link access. This service can be privately connected with and consumed using Private Endpoints deployed in the user's virtual network.

### MLflow

- **MLflow tracking**: built around runs, runs can be combined together into experiments.
- **MLflow projects:** method of packaging data science code. Each project includes at least one **entry point**, which is a file (either **.py** or **.sh**) that is intended to act as the starting point for project use. Projects also specify details about the **environment**. This includes the specific packages (and versions of packages) used in developing the project, as new versions of packages may include breaking changes.
- **Mlflow models:** A **model** in MLflow is a directory containing an arbitrary set of files along with an **MLmodel** file in the root of the directory. MLflow allows models to be of a particular **flavor**, which is a descriptor of which tool or library generated a model.
- **MLflow Model registry**: 
	- The MLflow Model Registry allows a data scientist to keep track of a **model** from MLflow Models. In other words, the data scientist **registers** a model with the Model Registry, storing details such as the name of the model. 
	- Each registered model may have multiple **versions**, which allow a data scientist to keep track of model changes over time.
	- It is also possible to **stage** models. Each model version may be in one stage, such as **Staging**, **Production**, or **Archived**. 

##### MLFlow & AzureML
In order to configure MLflow Tracking and connect Azure Machine Learning as the backend for MLFlow experiments, you need to follow these steps as shown in the code snippet:
```python
import mlflow 
from azureml.core import Workspace 

# Get your AML workspace 
ws = Workspace.from_config() 

# Get the unique tracking URI address to the AML workspace 
tracking_uri = ws.get_mlflow_tracking_uri() 

# Set up MLflow tracking URI to point to AML workspace 
mlflow.set_tracking_uri(tracking_uri)

# Configure a MLflow experiment
mlflow.set_experiment('MLflow-AML-Exercise')

# Run experiment
with mlflow.start_run() as run: 
	...
	mlflow.log_metric('rmse', rmse)
	mlflow.log_artifact("./outputs/results.png")
```

##### Running pipeline step on Databricks Compute
Azure Machine Learning supports a specialized pipeline step called **DatabricksStep** with which you can run a notebook, script, or compiled JAR on an Azure Databricks cluster. In order to run a pipeline step on a Databricks cluster, you need to do the following steps:

1.  Attach Azure Databricks Compute to Azure Machine Learning workspace.
2.  Define DatabricksStep in a pipeline.
3.  Submit the pipeline.

```python
# Define DatabricksStep
spark_conf = {"spark.databricks.delta.preview.enabled": "true"} 
databricksStep = DatabricksStep(
	name = "process_data", 
	run_name = "process_data", 
	python_script_params=["--dataset_name", "nyc-taxi-dataset"], 
	spark_version = "7.3.x-scala2.12", 
	node_type = "Standard_DS3_v2", 
	spark_conf = spark_conf, 
	num_workers = 1, 
	python_script_name = "process_data.py",
	source_directory = "./scripts", 
	pypi_libraries = [
		PyPiLibrary(package = 'scikit-learn'), 
		PyPiLibrary(package = 'scipy'), 
		PyPiLibrary(package = 'azureml-sdk'), 
		PyPiLibrary(package = 'azureml-dataprep[pandas]')
	], 
	compute_target = databricks_compute, 
	allow_reuse = False
)

# Construct the pipeline 
pipeline = Pipeline(
	workspace = ws, 
	steps = [databricksStep]
) 

# Create an experiment and run the pipeline 
experiment = Experiment(
	workspace = ws, 
	name = "process-data-pipeline"
) 
pipeline_run = experiment.submit(pipeline)
```

### Distributed deel learning with Horovod and Azure Databricks

When Horovod is used on top of one of the deep learning frameworks (TensorFlow, PyTorch or Keras), it trains multiple models on different batches of the input dataset on separate workers. In other words, multiple models are trained in parallel on separate workers using different subsets of the data.

At the end of an epoch, the weights are communicated between workers and the average weight of all workers is calculated. Next, a new epoch can start using the new average weight and during which again, multiple models are trained in parallel.

To distribute the training of a deep learning model using HorovodRunner, you should do the following:
-   Prepare and test single-node code with TensorFlow, Keras, or PyTorch.
-   Migrate the code to Horovod.
-   Use `HorovodRunner` to run the code and distribute your work.

[[azure]] [[databricks]] [[azureml]]