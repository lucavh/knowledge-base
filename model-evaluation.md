## Train/test/validation split

- A typical train/test/validation split would be to use 60% of the data for training, 20% of the data for validation, and 20% of the data for testing.
- **Train-test split**: evaluate the [[generalization]] performance on unseen data
- **[[cross-validation]]**: evaluate the variability of your estimation of the [[generalization]] performance
- [[scikit-train-test-split]]

## Evaluation metrics
### [[Classification]] metrics

```code
accuracy = (TP + TN) / (P + N)
```

```code
balanced accuracy = (1 / 2) * ((TP / P) + (TN / N))
```

- In the case of class imbalance, one could look at balanced accuracy instead of regular accuracy. Balanced accuracy is the average recall obtained on each class.

```code
precision = TP / (TP + FP)
```

```code
recall = TP / (TP + FN)
```

```code
F1 = 2 * (precision * recall) / (precision + recall)
```

- The f1 metric measures the balance between precision and recall. 
- When the value of f1 is high, this means both the precision and recall are high. 
- A lower f1 score means a greater imbalance between precision and recall.

```code
precision-recall curve (precision vs recall)

-> average precision (AP) = sum([recalls(k) - recalls(k+1)] * precisions(k))
```

- Each point in the curve corresponds to a level of [[probability]] which is used as a decision threshold.
- A perfect classifier would have a precision of 1 for all recall values.
- A metric characterizing the curve is linked to AUC and is named average precision (AP). With an ideal classifier, the average precision would be 1.
- The average precision is a way to summarize the precision-recall curve into a single value representing the average of all precisions.

```code
sensitivity = recall = TP / (TP + FN)
```

```code
specificity = TN / (TN + FP)
```

```
F1 = (2 * precision * recall ) / (precision + recall)
```

- Weighted average of precision and recall

#### AUC-ROC

![[roc-curve.webp]]

```code
receiver operating characteristic (ROC) curve (sensitivity vs (1 - specificity))

->  area Under the ROC curve (AUC-ROC) 
```

- Receiver operating characteristic (ROC) curve can be used to compromise between accurately discriminating the positive class and accurately discriminating the negative classes
### Macro recall

```
macro recall = average of recall of all classes`
```

When one of the classes dominates heavenly, macro recall needs to be normalized:

```
norm macro recall = (macro recall - R) / (1 - R)
R = 1 / C
C = number of classes
```


### Error metrics

```code
(Root) Mean Squared Error ((R)MSE)
```

- The raw (R)MSE can be difficult to interpret. One way is to rescale the MSE by the variance of the target. This score is known as the R2 score. 
- Compared to MAE, RMSE amplifies and severely punishes large errors

```code
Mean Absolute Percentage Error (MAPE) for relative scaling
```

```
Relative Absolute Error (RAE) = absolute error divided by sum of abs difference to mean
```

### [[Regression]] metrics

```
R-Squared or Coefficient of Determination (R^2) = 1 - (sum of squares of residuals / total sum of squares)
```

![[r2_score.png]]

- How much (what %) of variantion in Y is described by the variation in X?  Higher value means that variation in Y is explained by variation in X.
- The best score possible is 1 but there is no lower bound.
- In the best case, the modeled values exactly match the observed values, which results in `sum of squares of residuals = 0` and `R^2 = 1`. 
- A baseline model, which always predicts the mean of the observed data, will have `R^2 = 0`. Models that have worse predictions than this baseline will have a negative R2.

```code
Adjusted R-Squared penalizes for high number of features.
```

[[machine-learning]]
