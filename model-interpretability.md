Benefits of having insights into interpretability: 

- Explain the entire model behavior or individual predictions locally as wel as in Azure
- Enable interpretability techniques for engineered features
- Use a dashboard to interact with your model explanations ([[data-visualization]])
- Deploy a scoring explainer alongside your model to observe explanations during inferencing

## Shapley Value

- How much cost or gain can be associated to a feature

## Interpretability techniques

- Global interpretability:
	- Top important features for the entire prediction set
	- Takes into account entire training or test dataset
	- Example: Which features are important to get this accuracy?

- Local interpretability:
	- Top important features for an individual prediction
	- Takes into accoun just one record of independent features
	- Example: which top features predicted that Bob has an income higher than 50k?

| Technique | Description | Type |
| --------- | ----------- | ---- |
| SHAP Tree Explainer | Support for Tree algorithms | Model specific |
| SHAP Deep Explainer | Support for deep learning models | Model specific 
| SHAP Linear Explainer | Support for linear models (e.g. linear/logistic regression) | Model specific 
| SHAP Kernel Explainer | Supports every model | Model Agnostic |
| Mimic Explainer | Creates a surrogate model to mimix the behavior of a black box model | Model Agnostic |
| Permutation Feature Importance Explainer | Randomly shuffels features | Model Agnostic |

## Package InterpretML (`azureml-interpret`)

- https://interpret.ml/

[[model-evaluation]]
[[machine-learning]]