Logistic [[regression]] is a statistical technique used for modeling the [[probability]] of a binary outcome based on one or more predictor variables. It is particularly useful when the dependent variable is categorical and has two possible outcomes (e.g., yes/no, 1/0, true/false)

Unlike linear [[regression]], which predicts a continuous outcome, logistic [[regression]] models the [[probability]] of a specific class or category. It employs a standard logistic function, also known as the sigmoid function, to constrain the output between 0 and 1.

![[linear-vs-logistic-regression.png]]

## Model Training

### Hyperparameters

1. **Trainer Mode**:
    - _Single Parameter_: You provide a specific set of values for the model's parameters.
    - _Parameter Range_: You specify a range of values, and the algorithm finds the optimum set within that range for the given configuration.
2. **Optimization Tolerance**: This is a threshold used to stop the training process when the model is not improving beyond a certain value. It helps prevent overfitting.
3. **L2 [[Regularization]]**: This is a technique used to prevent overfitting by adding a penalty term to the loss function. It discourages the model from assigning too much importance to any one feature.
### Optimization Criterion

Logistic [[regression]] aims to maximize the likelihood of the observed data given the model parameters. The likelihood represents the [[probability]] of observing the given data under the assumed model.