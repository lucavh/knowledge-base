
## Recap

- [Recap on decision trees and Gini impurity](https://www.youtube.com/watch?v=7VeUPuFGJHk&ab_channel=StatQuestwithJoshStarmer)
- [Recap on Random Forests](https://www.youtube.com/watch?v=J4Wdy0Wc_xQ&ab_channel=StatQuestwithJoshStarmer)
  - Bootrstapping the data plus using AGGregate to make a decision is called __bagging__.
  - Validation: proportion of __Out-Of-Bag samples__ that were correctly classified, called __Out-Of-Bag error__.
  - Procedure:
    1. Create bootstrapped data set
    2. Create decision tree using bootstrapped dataset, but only use a random subset of variables (i.e. columns) to chose from at each step of the tree.
            - Optimal number can be determined using hyperparameter tuning and Out-Of-Bag error. Typically, you start by using the square of the number of variables and then try a few settings above and below that value.
    3. Repeat step 1-2 for 100's of times
    4. For prediction, run data through all trees and select label with most votes.
- [Recap on AdaBoost](https://www.youtube.com/watch?v=LsK-xG1cLYA&ab_channel=StatQuestwithJoshStarmer)
  - Combines a lot of "weak learnings" (usually __stumps__) to make classifications.
  - Some stumps get more say in the final classification than others. Determined based on how well samples are classified (__Amount of Say__).
  - The errors that the first stump makes, influence how the second stump is made, etc (__Sample Weights__). If you have a __Weighted Gini Function__, you use it with the __Sample Weights__, otherwise you use the __Sample Weights__ to make a new dataset that reflects those weights.
  - AdaBoost vs Gradient Boost:
    - Gradient Boost starts by making a single leaf, instead of a tree or stump. This leaf represents an initial guess for the Weights of all of the samples. For a continuous value, the first guess is the average value. Then Gradient Boost builds a tree.
    - Like AdaBoost, Gradient Boost builds fixed sized trees (usually 8-32 leaves) based on the previous tree's errors. But unlike AdaBoost, each tree can be larger than a stump.
    - Like AdaBoost, Gradient Boost scales the trees. However, Gradient Boost scales all trees by the same amount.
- [Recap Regularization](https://www.youtube.com/watch?v=Q81RR3yKn30&ab_channel=StatQuestwithJoshStarmer)
  - Apply a penalty to a loss function to prevent overfitting.

## Gradient Boost ([link 1](https://www.youtube.com/watch?v=3CC4N4z3GJc&ab_channel=StatQuestwithJoshStarmer) - [link 2](https://www.youtube.com/watch?v=jxuNLH5dXCs&ab_channel=StatQuestwithJoshStarmer))

- Sequential decision trees. Each tree will be built based on the previous tree's residuals. Predictions are then made by the sum of all those residuals.

### For regression

1. Start with a leaf that is the average of the variable we want to predict.
2. Build a tree based on the residuals from the first tree (__Pseudo Residual__ = observed value - predicted value).
3. Scale the tree's contribution to the final prediction with a __learning rate__.
4. Repeat. Each time you add a tree to the prediction, the residuals get smaller. Keep adding trees untill you reach the maximum specified or adding additional trees does not significantly reduce the size of the residuals.

- Most common Loss Function for regression is `1/2 * (Observed - Predicted)^2`. Loss function is differentiable (`-(Observed - Predicted)`).

### For Classification

1. Start with a leaf that is the initial prediction for every individual, use __log(odds)__ (e.g. 4 times yes, 2 times no, log(odds) that it is yes is `log(4/2) = 0.7`). Then, convert it to a probability with a Logistic Function (`e^log(odds) / (1 + e^log(odds))`).
2. Build a tree based on the residuals from the first tree (__Pseudo Residual__ = observed value - predicted value, use probability for predicted value).
3. ...
