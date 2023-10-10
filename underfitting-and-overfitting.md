- Models overfit if:
  - number of examples in the training set is too small
  - testing error is much bigger than training error
  - high variance: unstable models

- Models underfit if
  - models fail to capture the shape of the training set
  - even the training error is large
  - high bias: misspecified models

## Approach to overcome

- **Compare train and test errors**: identify whether a model is generalizing, overfitting, or underfitting.
  - We observe a ****small training error** (actually zero), meaning that the model is not under-fitting: it is flexible enough to capture any variations present in the training set.
  - However the **significantly larger testing error** tells us that the model is over-fitting: the model has memorized many variations of the training set that could be considered “noisy” because they do not generalize to help us make good prediction on the test set.
  
![](cv_train_test.png)

- **Validation curve**: check influence of a hyperparameter on the tradeoff underfit/overfit.
  - Looking at the curve, we can clearly identify the over-fitting regime of the SVC classifier when `gamma > 1`. The best setting is around `gamma = 1` while for `gamma < 1`, it is not very clear if the classifier is under-fitting but the testing score is worse than for `gamma = 1`.
  - Code example

```
import matplotlib.pyplot as plt
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import validation_curve

model = RandomForestRegressor()
n_estimators = [1, 2, 5, 10, 20, 50, 100, 200, 500, 1000]

train_scores, test_scores = validation_curve(
    model, data, target, param_name="n_estimators", param_range=n_estimators, cv=10, n_jobs=2
  )

plt.errorbar(
    n_estimators,
    train_scores.mean(axis=1),
    yerr=train_scores.std(axis=1),
    label="Train score",
)
plt.errorbar(
    n_estimators,
    test_scores.mean(axis=1),
    yerr=test_scores.std(axis=1),
    label="Test score",
)
plt.legend()
plt.xscale("log")
plt.xlabel("Number of trees")
plt.ylabel("R2 score")
plt.ylim([0, 1])
_ = plt.title("Validation curve for Random Forest")
```

![](cv_validation_curve.png)

- **Learning curve**: the influence of the number of samples in a dataset, especially on the variability of the errors reported when running the cross-validation.
  - We observe that adding new samples to the training dataset does not seem to improve the training and testing scores. In particular, the testing score oscillates around 76% accuracy. Indeed, ~76% of the samples belong to the class `not donated`.

![](cv_learning_curve.png)

[[machine-learning]]