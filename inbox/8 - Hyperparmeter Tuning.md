## Sampling methods

1. Random Sampling
	- Discrete & continuous hyperparemters
	- Selects combination with best results
	- Supports early termination
2. Grid Sampling
	- Only discrete hyperparameters
	- Selects combination with best results
	- Supports early termination
3. Bayesian Sampling
	- Discrete & continuous hyperparemters
	- Selects combination by learning from the previous run
	- Uses Bayesian optimization for getting the best combination
	- Does not support early termination

## Early termination options

1. No termination policy
2. Bandid Policy
	- Checks if the `primary metric` of the new epoch is less than `primary metric` of best epoch minus the `slack amount` or `slack factor`. If so, terminate run.
	- Example: during the first 10 epochs, if epoch 5 provides the best accuracy of `0.90`, then if any epoch (`evaluation_interval`) after the 10th one (`delay_evaluation`), reports accuracy less than `0.90 - 0.10 (slack_amount) = 0.80` the run will be terminated.
3. Median Stopping Policy
	- Calculates running average of all runs. After delay period, it will check if the primary metric is less than the median of all the previous runs. if so, it will terminate the run.
4. Truncation Selection Policy
	- Exclude the bottom X% of the iterations after every interval.

When to apply early termination?
- Algorithms with learning rate and epochs, such as SGDClassifier, SGDRegressor, XGBoost, Deep Learning.

