**Hyperparameters** are external parameters that can be tweaked to optimize the cost function (e.g. number of hidden layers), **parameters** are internal to the model and determined during model fit (e.g. weights).
## Common Hyperparameters

1. **Learning rate:** determines the step size at which the model parameters are updated during training. It is a critical hyperparameter in gradient-based optimization algorithms like [[stochastic-gradient-descent]] (SGD).
2. **[[regularization]] strength (Lambda):** controls the degree of regularization applied to the model. In L1 and L2 regularization, it influences the balance between fitting the training data and preventing overfitting.
3. **Depth of a Decision Tree:** for [[tree-based-learning]] like decision trees and random forests, the maximum depth of the tree is a crucial hyperparameter. It governs the complexity of the tree and directly impacts its ability to capture intricate patterns.
4. **Number of Hidden Units:** in [[neural-networks]], the number of hidden units or neurons in each layer is a critical hyperparameter. It determines the capacity of the network to learn complex relationships within the data.
5. **Number of Trees:** for ensemble methods like random forests and [[gradient-boosting-machines]], the number of individual trees in the ensemble is a key hyperparameter. It affects the trade-off between bias and variance.
6. **Kernel Type and Parameters**:** [[support-vector-machines]] (SVMs) have hyperparameters related to the choice of kernel (e.g., linear, polynomial, radial basis function) and associated parameters like the kernel width.
7. **Batch Size:** in [[deep-learning]] and optimization algorithms like mini-batch gradient descent, the batch size determines the number of training examples used in each iteration of parameter updates.
8. **Activation Function:** the choice of activation function in [[neural-networks]] (e.g., ReLU, sigmoid, tanh) is a crucial hyperparameter that influences the non-linearity of the model.
9. **Number of Clusters:** For [[clustering-algorithms]] like [[k-means]], the hyperparameter 'k' represents the number of clusters to partition the data into.
10. **Epsilon:** in Support Vector Machines, the epsilon hyperparameter controls the width of the margin around the decision boundary.
11. **Number of Neighbors:** in the [[k-nearest-neighbors]] algorithm, the hyperparameter 'k' represents the number of nearest neighbors to consider when making predictions.
## Early Termination Strategies

1. **No Termination Policy**: this strategy implies that the training process will run until the predefined number of epochs is reached, regardless of the performance improvement.
2. **Bandit Policy**: this policy monitors the primary metric of each epoch. If the current epoch's metric falls below the best epoch's metric by a specified margin (slack amount or slack factor), the run is terminated.
        - _Example:_ If epoch 5 achieves the best accuracy of `0.90` within the first 10 epochs, any subsequent epoch reporting accuracy less than `0.80` (`0.90 - 0.10 (slack_amount) = 0.80`) will trigger termination.
3. **Median Stopping Policy**: this policy calculates the running average of all runs. After a specified delay period, it checks if the primary metric falls below the median of all previous runs. If so, it terminates the run.
4. **Truncation Selection Policy**: this policy excludes a certain percentage (X%) of the lowest-performing iterations after a defined interval.

Early termination is particularly useful for algorithms that involve learning rate and epochs, such as `SGDClassifier`, `SGDRegressor`, [[xgboost]], and [[deep-learning]] models.