## Big Data

Characteristics:
- Volume - quantity of data generated and stored
- Variety - type and nature of data
- Velocity - speed of data generation and processing
- Variability - inconsistency of dataset
- Veracity - quality/uncertainty of data captured

### Hadoop vs Spark vs Databricks

- Spark is successor of Hadoop
- Databricks is successor of Databrcks

#### Hadoop

- Open-source framework for distributed processing
- Designed to scale up from single to thousands of servers in parallel

Architecture:
- MapReduce: distributed data processing
- HDFS (Hadoop Distributed File System): distributed storage
- YARN (Yet Another Resource NEgotiator): jog scheduling and resource manager
- Hadoop common: Java Library and utilities
- One master node with `name node` and `data node`
- Multiple worker nodes with `data notes`

Ecosystem:
![[hadoop_ecosystem.webp]]

Disadvantages:
- Inefficient processing
- Batch only
- Huge ecosystem
- No in-memory processing

#### Spark

- Unified analytics engine for large-scale data processing
- In-memory distributed cluster computing
- Provides APIs for development in Java, Python, Scala and R
- Support batch and real-time processing
- Very high speed execution

Architecture:
![[spark_architecture.jpeg]]
- Similar to Hadoop, Spark also has a Master node. This node runs the Driver Program.
- Inside the Driver Program, we create the SparkContext, which will connect to the Spark cluster and contains the configuration, connection requirements for the cluster. It serves as a kind of gateway between the driver and the Spark Cluster.
- The Spark Context can connect with the Cluster Manager to locate resources for the applications.
- Spark acquired the executers on the worker nodes. These executors actually get the data as well as execute the tasks.
- There is no mention of storage. Spark is a unified engine, it does not matter where the data is stored, as long as the worker nodes can access it and load it in memory. 

Ecosystem:
- Spark Core engine which you can use with APIs for Python, R, Scala and Java
- Additional components: Spark SQL, Spark Streaming, Spark MLLib, Spark GraphX, SparkR

Disadvantages:
- Not easy to use
- Develop enrivonment on your own
- Collaboration of work is difficult
- Not developed as cloud-first

#### Databricks

- A wrapper around Spark
- Platform optimized for efficient working with Spark
- Provides workspace to manage Spark and its infrastructure
- Ease of colalboration and integration

Architecture:
![[databricks_architecture.png]]

## Databricks

### Pricing
1. All-Purpose: best for data scientists
2. Jobs: best for data engineers
3. Jobs Light: best for data engineers

### Increasing vCPU Quota Limits
- Databricks requires you to increase "Total Regional vCPUs" to a minimum of 12. You can update this in the Subscription overview > Settings > Usage + quotas

### Databricks clusters
- `Cluster Mode` is about number of concurrent users:
	- High Concurrency: many concurrent users
	- Standard: singe-user clusters
	- Single Mode: no worker nodes
- `Pools` keep a defined number of ready instanced on standby to reduce cluster startup time.
- `Worker Type` is the virtual machine type. Charges are in DBU (Databricks Units).

### Link Azure ML Workspace to Databricks Workspace
- Link an Azure ML workspace through the overview of the Databricks instance in the Azure portal
- Execute AzureML workspaces from Databricks

### Mount Azure Blob Storage containers to DBFS
```python
container_name = "<container-name>"
storage_account_name = "<storage-account-name>"
source = f"wasbs://{container_name}@{storage_account_name}.blob.core.windows.net"
mount_point = "/mnt/iotdata"
scope_name = "<scope-name>"
key_name = "<key-name>"

# Unmount storage container if it already exists
try:
	dbutils.fs.unmount(mount_point)
except:
	print("The mount did not exist.")

# Mount storage container
dbutils.fs.mount(
  source = source,
  mount_point = mount_point,
  extra_configs = {f"fs.azure.account.key.{storage_account_name}.blob.core.windows.net":dbutils.secrets.get(scope = scope_name, key = key_name)})
```

### Run a AzureML training script using DataBricksStep in a pipeline

#### Azure ML set-up steps:
- Part 1:
	1. Create Azure Storage Account
	2. Create Blob Container
	3. Copy the access key for storage account
	4. Upload the data/csv to container
- Part 2:
	1. Create AzureML Workspace
	2. Create AzureML Datastore
	3. Create AzureML Dataset
- Part 3:
	1. Create Databricks Workspace
	2. Create Databricks Cluster
	3. Create and Copy Databricks workspace access key

#### Python job steps:
- Part 1:
	1. Create Workspace object from the config file
	2. Create custom environment and cluster
	3. Create `run_config` for Python script step
	4. Create data reference for input dataset
	5. Create `PipelineData` objects for Input/Output
- Part 2:
	1. Create Databricks Compute configurations parameters with key
	2. Attach the Databricks Cluster as attached computed
- Part 3:
	1. Create `DatabricksStep`
	2. Create `PythonScriptStep`
	3. Create Pipeline using `DatabricksStep` and `PythonScriptStep`

#### Databricks notebook steps:
1. Unmount the input and output data mounts
2. Get the Inputs and Outputs parameters using `dbutils.widgets.get`
3. Mount input and output blob storage folders as DBFS directory
5. Read data from the mounts
6. Perform data processing or functions as desired
7. Make output directories on Blob Storage using dummy blob
8. Save output files using the DBFS mount to Blob Storage
