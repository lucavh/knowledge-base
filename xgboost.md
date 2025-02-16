- Stands for Extreme Gradient Boosting and is a [[gradient-boosting-machines]] algorithm.
- When building __XGBoost Trees__ for __[[Regression]]__ you calculate __Similarity Scores__ and __Gain__ to determine how to split the data and prune the tree by calculating the differences between __Gain__ values and a user defined __Tree Complexity Parameter (gamma)__.
- Then calculate the __Output Values__ for the remaining leaves.
- Lambda is a __[[Regularization]] Parameter__ and when l>0, it results in more [[pruning]], by schrinking the __Similarity Scores__, and it results in smaller __Output Values__ for the leaves.

```code
Similarity Score = (sum of resifuals)^2 / (number of residuals + lambda)

Gain = LeftSimilarity + RightSimilarity - RootSimilarity

Gain - gamma =
 |- if positive, then do not prune
 |- if negative, then prune

 Output Value = sum of residuals / (number of residuals + lambda)
```

Resource: [Video by StatQuest with Josh Starmer](https://www.youtube.com/watch?v=OtD8wVaFm6E&ab_channel=StatQuestwithJoshStarmer)