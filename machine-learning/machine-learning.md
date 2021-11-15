# Machine Learning

Typical ML model notation: `f(X,w) = y`, where `X` is a metrix with all the features and `y` is a vector with the target variable.

__Hyperparameters__ are external parameters that can be tweaked to optimize the cost function (e.g. number of hidden layers), __parameters__ are internal to the model and determined during model fit (e.g. weights). 

## Imputing missing data

- Empty values can be removed or handled with imputation (e.g. fill with mean)

## Encoding for categorical variables
- __Ordinal encoding__: 
    - One column with a vector, e.g. `[1,0]`
    - Advantage: easily make (textual) categories numerical
    - Disadvantage: ML is based on linear algebra, thus, the model will take into account the vector distances, which is undesired behavior.
- __One-hot encoding__: 
    - Produces one column with boolean value per category, e.g. `1`
    - Advantage: value is either 1 or 0, thus distances between all categories are equal. 
    - Disadvantage: this approach might blow up your feature space if you have many categories. Possible solution is to only use the top X categories and make the rest "Other". 
- __Target encoding__:
    - Alternative for one-hot encoding
    - Replace the categorical value with the some descriptive statistic (e.g. mean) of the target variable per category (e.g. the average housing price of the neighbourhood instead of the neighbourhood as a category).

## Feature selection

Exclude features if:

- Too many **missing values**  
- Too little value **variance** (see [VarianceThreshold](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.VarianceThreshold.html#sklearn.feature_selection.VarianceThreshold))
- **High correlation** with the target or other features

Automatic feature selection methods:

- **Statistical testing** where little contributing features are removed (see [SelectKBest](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectKBest.html#sklearn.feature_selection.SelectKBest)). 
- **Model-based selection** where a(n often penalized) model is used to the determine and eliminate the least contributing features (see [SelectFromModel](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectFromModel.html#sklearn.feature_selection.SelectFromModel)).

In practice, `SelectFromModel` is most often used in combination a _penalized_ model. By adding a special component to the cost function, complex models are penalized. `Lasso` is most used for regression problems and `LinearSVC(penalty="l1")` for classification problems (linear SVM with Lasso-like penalty term). 

## Feature engineering

* **Date and time features** Creating features from the dates available, e.g. is a holidays or day of the week. 
* **Group values** Grouping various numeric elements to a categorical variable, e.g. the months December (12), January (1) and February (2) to the season Winter. 
* **Grouping sparse classes** If you have a feature with an individual low sample count, you might group various values together under some other category. For example: if we had a column `bike_type` it would make sense to have stand-alone values such as `race`, `road` or `grandma`, whereas you might want to group values lik `penny farthing`, `unicycle` and `tricycle` together under a single `other` category since they are rarely rented.
* **Group from threshold** A new grouped variable for other variables, e.g. `warm` and `cold` based on the temperature.
* **Indicator from threshold** An indicator variable (0 or 1) based on a threshold on a column, e.g. eligible to vote/work based on age. 
* **Interaction of variables** The sum, difference, product or quotient of two features. E.g. `profit` as result of the difference between income and expenses. 

## Machine Learning Models

### Linear regression
- Intercept problem: when fitting a linear model, you might want to not fit the intercept (in scikit-learn: `fit_intercept=False`). Additionally you might want to add an offset to the prediction which is the mean of the intercept value (in scikit-learn: `model.predict + offset`)

## Evaluation metrics

### Classification
```
precision = TP / (TP + FP)
```
```
recall = TP / (TP + FN)
```
```
F1 = 2 * (precision * recall) / (precision + recall)
```
```
Area Under the ROC curve (AUC-ROC) (sensitivity and (1- specificity))
```

### Regression
```
Root Mean Squared Error (RMSE)
```
```
R^2 = MSE(model) / MSE(baseline)
```
```
Adjusted R-Squared penalizes for high number of features.
```

### How do I know if I overfit?
Look at the evaluation metrics (e.g. MAE) on the train and test set. If the performance on the train set is much higher compared to the performance on the test set, you might be overfitting. You want the differences in performance to be minimal. You could apply __bootstrapping__ to determine statistical significance.

