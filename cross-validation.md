### Nested cross-validation

The k-fold cross-validation procedure is used to estimate the performance of machine learning models when making predictions on data not used during training.

This procedure can be used both when optimizing the hyperparameters of a model on a dataset, and when comparing and selecting a model for the dataset. When the same cross-validation procedure and dataset are used to both tune and select a model, it is likely to lead to an optimistically biased evaluation of the model performance.

One approach to overcoming this bias is to nest the hyperparameter optimization procedure under the model selection procedure. This is called **double cross-validation** or **nested cross-validation** and is the preferred way to evaluate and compare tuned machine learning models.

![[Pasted image 20231010102731.png]]

![[nested_cross_validation_diagram.png]]
([source](https://machinelearningmastery.com/nested-cross-validation-for-machine-learning-with-python/))

### Choice of cross-validation

Depending on the dataset and prediction task, you want to select a suitable cross-validation method. See also [Visualizing cross-validation behavior in scikit-learn](https://scikit-learn.org/stable/auto_examples/model_selection/plot_cv_indices.html#sphx-glr-auto-examples-model-selection-plot-cv-indices-py).


[[model-evaluation]] 