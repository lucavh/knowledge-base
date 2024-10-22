## Real-time inferencing

### Deploy

1. Register a trained model: `Model.register()` or `run.register_model()`
2. Define inference configuration:
	1. Create ==entry script / scoring script==, must include two functions:
		- `init()`: called when the service is initialized to load model fro model registry
		- `run(raw_data)`: called when new data is submitted to generate model predictions
	2. Create an environment `Environment()`
	3. Combine the script and environment in an `InferenceConfig`
```python
InferenceConfig(
	source_directory = 'service_files', 
	entry_script="score.py", 
	environment=service_env
)
```
3. Create cluster 
```python
compute_config     = AksCompute.provisioning_configuration(location='eastus') production_cluster = ComputeTarget.create(ws, cluster_name, compute_config)
```
4. Define a deployment configuration
```python
classifier_deploy_config = AksWebservice.deploy_configuration(
	cpu_cores = 1, 
	memory_gb = 1
)
```
5. Deploy the model
```python
model   = ws.models['classification_model']
service = Model.deploy(
	workspace=ws, 
	name = 'classifier-service', 
	models = [model], 
	inference_config = classifier_inference_config, 
	deployment_config = classifier_deploy_config, 
	deployment_target = production_cluster
)
service.wait_for_deployment(show_output = True)
```
- For ACI or local services, you can omit the **deployment_target** parameter (or set it to **None**).

### Consume

- For testing, you can use the AzureML SDK to call a web service through the **run** method of a **WebService** object that references the deployed service.
- In production, most client applications will consume the service through its **==REST interface==**. You can determine the endpoint of a deployed service in AzureML Studio or by retrieving the `scoring_uri` property of the Webservice object in the SDK.
```python
endpoint = service.scoring_uri
```
- With endpoint known, you can use an **HTTP POST** request with JSON data to call the service.

### Troubleshoot
- Check service state: `print(service.state)`
- Review service logs: `print(servive.get_logs())`
- Deploy to a local container: `LocalWebservice.deploy_configuration(port=8890)`

## Batch inferencing

### Create batch inference pipeline

1. Register a model
2. Create an entry script / scoring script, must include `init()` and `run(mini_batch)`
3. Create a pipeline with a ParallelRunStep
	- Azure Machine Learning provides a type of pipeline step specifically for performing parallel batch inferencing. Using the **ParallelRunStep** class, you can read batches of files from a **File** dataset and write the processing output to a **OutputFileDatasetConfig**. Additionally, you can set the **output_action** setting for the step to "append_row", which will ensure that all instances of the step being run in parallel will collate their results to a single output file named _parallel_run_step.txt_.
```python
parallel_run_config = ParallelRunConfig(
	source_directory='batch_scripts', 
	entry_script="batch_scoring_script.py", 
	mini_batch_size="5", 
	error_threshold=10, 
	output_action="append_row", 
	environment=batch_env, 
	compute_target=aml_cluster, 
	node_count=4
)
parallelrun_step = ParallelRunStep(
	name='batch-score', 
	parallel_run_config=parallel_run_config, 
	inputs=[batch_data_set.as_named_input('batch_data')], 
	output=output_dir, 
	arguments=[], 
	allow_reuse=True
)
pipeline = Pipeline(workspace=ws, steps=[parallelrun_step])
```
4. Run the pipeline and retrieve the step output
	- After your pipeline has been defined, you can run it and wait for it to complete. Then you can retrieve the **parallel_run_step.txt** file from the output of the step to view the results

### Publish batch inference pipeline 

1. Publish batch inferencing pipeline as a **REST service**:
```python
published_pipeline = pipeline_run.publish_pipeline(
	name='Batch_Prediction_Pipeline',
	description='Batch pipeline', 
	version='1.0'
)
rest_endpoint = published_pipeline.endpoint
```
2. Once published you can use the **service endpoint** to initiate a batch inferencing job:
```python
response = requests.post(
	rest_endpoint,
	headers=auth_header,
	json={"ExperimentName": "Batch_Prediction"}
)
run_id = response.json()["Id"]
```
3. You can also schedule the published pipeline to have it run automatically:
```python
weekly = ScheduleRecurrence(
	frequency='Week', 
	interval=1
)
pipeline_schedule = Schedule.create(
	ws, name='Weekly Predictions', 
	description='batch inferencing', 
	pipeline_id=published_pipeline.id, 
	experiment_name='Batch_Prediction', 
	recurrence=weekly
)
```

## Data drift

### Monitoring

To monitor data drift using registered datasets, you need to register two datasets:
- A **baseline** dataset - usually the original training data.
- A **target** dataset that will be compared to the baseline based on time intervals. This dataset requires a timestamp column so the rate of data drift can be measured.
```python
monitor = DataDriftDetector.create_from_datasets(
	workspace=ws, 
	name='dataset-drift-detector', 
	baseline_data_set=train_ds, 
	target_data_set=new_data_ds, 
	compute_target='aml-cluster', 
	frequency='Week', 
	feature_list=['age','height', 'bmi'], 
	latency=24
)
backfill = monitor.backfill(
	dt.datetime.now() - dt.timedelta(weeks=6), 
	dt.datetime.now()
)
```

### Scheduling alerts
```python
alert_email = AlertConfiguration('data_scientists@contoso.com')
monitor = DataDriftDetector.create_from_datasets(
	ws, 
	'dataset-drift-detector', 
	baseline_data_set, 
	target_data_set, 
	compute_target=cpu_cluster, 
	frequency='Week', 
	latency=2, 
	drift_threshold=.3,
	alert_configuration=alert_email
)
```

[[*azure]] [[azureml]]