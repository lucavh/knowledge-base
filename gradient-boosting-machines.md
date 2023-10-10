Gradient Boosting Machines (GBMs), also known as Gradient Boosting Decision Trees (GBDT), are a potent [[ensemble-learning]] technique widely employed in machine learning for both [[regression]] and [[classification]] tasks. This approach combines the predictions of multiple weak learners, typically [[tree-based-learning]] algorithms, to construct a robust predictive model. GBMs iteratively enhance model performance by adding trees to correct the errors of preceding ones.
## Understanding Gradient Boosting

### Basics for Regression

1. **Initial Prediction**: Start with a leaf that represents the average of the variable to predict.
2. **Building Trees**: Subsequent trees are constructed based on the residuals (observed value - predicted value) from the preceding tree. This residual is termed as the **Pseudo Residual**.
3. **Scaling Contributions**: Each tree's contribution to the final prediction is scaled by a **learning rate**.
4. **Iterative Process**: Repeat the process. With each tree added, the residuals become smaller. Continue until further tree additions no longer significantly reduce residuals.
### For Classification

1. **Initial Prediction**: Begin with a leaf that provides the initial prediction for each individual using the log(odds) (e.g., log(odds) of yes given 4 times yes and 2 times no is 0.7). Convert this to a probability using a Logistic Function.
2. **Building Trees**: Similar to regression, construct trees based on the residuals (Pseudo Residual) from the initial prediction.