- **Squared error loss** is commonly used as loss function, minimization of this objective is also known as **cost function** or **empirical risk**.
- **Intercept problem**: when fitting a linear model, you might want to not fit the intercept (in scikit-learn: `fit_intercept=False`). Additionally you might want to add an offset to the prediction which is the mean of the intercept value (in scikit-learn: `model.predict + offset`)
- **Non-linear relationship**: linear models can be used even in settings where data and target are not linearly linked. A polynomial transformation can be applied to encode non-linear interactions between features.
- **[[Regularization]]**: it is advised to always use a penalty to shrink the magnitude of the weights toward zero (also called "l2 penalty"). In scikit-learn, `LogisticRegression` applies such penalty by default (with hyperparameter `C`). However, one needs to use `Ridge` (and even `RidgeCV` to tune the hyperparameter `alpha`) instead of `LinearRegression`.
- **[[Correlation]]**: highly correlated features can lead to numerical problems. Applying [[regularization]] can help overcome these issues.

[[learning-algorithms]]
[[statistics]]