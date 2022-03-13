# Machine Learning

## Preprocessing

### Imputing missing data

- Empty values can be removed or handled with imputation (e.g. fill with mean)

### Feature scaling

Some reasons for scaling features:

- Models that rely on the distance between a pair of samples, for instance k-nearest neighbors, should be trained on normalized features to make each feature contribute approximately equally to the distance computations.
- Many models such as logistic regression use a numerical solver (based on gradient descent) to find their optimal parameters. This solver converges faster when the features are scaled.

Whether or not a machine learning model requires scaling the features depends on the model family. Linear models such as logistic regression generally benefit from scaling the features while other models such as decision trees do not need such preprocessing (but will not suffer from it).

### Encoding of categorical variables

- **Ordinal encoding**:
  - One column with a number representation of the category
  - Ordinal encoding is often a good strategy with tree-based models. Using ordinal encoding will output ordinal categories. This means that there is an order in the resulting categories (e.g. `0 < 1 < 2`). The impact of violating this ordering assumption is really dependent on the downstream models. Linear models will be impacted by misordered categories while tree-based models will not.
  - You can still use an ordinal encoding with linear models but you need to be sure that:
    - the original categories (before encoding) have an ordering;
    - the encoded categories follow the same ordering than the original
  categories.
  - Advantage: easily make (textual) categories numerical
  - Disadvantage: most ML is based on linear algebra, thus, the model will take into account the vector distances, which is undesired behavior.
- **One-hot encoding**:
  - Produces one column with boolean value per category, e.g. `1`
  - In general one-hot encoding is the encoding strategy used when the downstream models are linear models.
  - One-hot encoding categorical variables with high cardinality can cause computational inefficiency in tree-based models. Because of this, it is not recommended to use one-hot encoding in such cases even if the original categories do not have a given order.
  - Advantage: value is either 1 or 0, thus distances between all categories are equal.
  - Disadvantage: this approach might blow up your feature space if you have many categories. Possible solution is to only use the top X categories and make the rest "Other".
- **Target encoding**:
  - Alternative for one-hot encoding
  - Replace the categorical value with the some descriptive statistic (e.g. mean) of the target variable per category (e.g. the average housing price of the neighbourhood instead of the neighbourhood as a category).

### Feature selection

Exclude features if:

- Too many **missing values**  
- Too little value **variance** (see [VarianceThreshold](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.VarianceThreshold.html#sklearn.feature_selection.VarianceThreshold))
- **High correlation** with the target or other features

Automatic feature selection methods:

- **Statistical testing** where little contributing features are removed (see [SelectKBest](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectKBest.html#sklearn.feature_selection.SelectKBest)).
- **Model-based selection** where a(n often penalized) model is used to the determine and eliminate the least contributing features (see [SelectFromModel](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectFromModel.html#sklearn.feature_selection.SelectFromModel)).

In practice, `SelectFromModel` is most often used in combination a _penalized_ model. By adding a special component to the cost function, complex models are penalized. `Lasso` is most used for regression problems and `LinearSVC(penalty="l1")` for classification problems (linear SVM with Lasso-like penalty term).

### Feature engineering

- **Date and time features** Creating features from the dates available, e.g. is a holidays or day of the week.
- **Group values** Grouping various numeric elements to a categorical variable, e.g. the months December (12), January (1) and February (2) to the season Winter.
- **Grouping sparse classes** If you have a feature with an individual low sample count, you might group various values together under some other category. For example: if we had a column `bike_type` it would make sense to have stand-alone values such as `race`, `road` or `grandma`, whereas you might want to group values lik `penny farthing`, `unicycle` and `tricycle` together under a single `other` category since they are rarely rented.
- **Group from threshold** A new grouped variable for other variables, e.g. `warm` and `cold` based on the temperature.
- **Indicator from threshold** An indicator variable (0 or 1) based on a threshold on a column, e.g. eligible to vote/work based on age.
- **Interaction of variables** The sum, difference, product or quotient of two features. E.g. `profit` as result of the difference between income and expenses.

## Models

### Notation

Typical ML model notation: `f(X,w) = y`, where `X` is a metrix with all the features and `y` is a vector with the target variable.

### Hyperparameters & parameters

**Hyperparameters** are external parameters that can be tweaked to optimize the cost function (e.g. number of hidden layers), **parameters** are internal to the model and determined during model fit (e.g. weights).

### Linear regression

- Intercept problem: when fitting a linear model, you might want to not fit the intercept (in scikit-learn: `fit_intercept=False`). Additionally you might want to add an offset to the prediction which is the mean of the intercept value (in scikit-learn: `model.predict + offset`)

## Model evaluation

### Cross-validation vs train/test split

- **Train-test split**: evaluate the generalization performance on unseen data
- **Cross-valudation**: evaluate the variability of your estimation of the generalization performance

### Evaluation metrics for classification

```code
precision = TP / (TP + FP)
```

```code
recall = TP / (TP + FN)
```

```code
F1 = 2 * (precision * recall) / (precision + recall)
```

```code
Area Under the ROC curve (AUC-ROC) (sensitivity and (1- specificity))
```

### Evaluation metrics for regression

```code
Root Mean Squared Error (RMSE)
```

```code
R^2 = MSE(model) / MSE(baseline)
```

```code
Adjusted R-Squared penalizes for high number of features.
```

### Overfitting

Look at the evaluation metrics (e.g. MAE) on the train and test set. If the performance on the train set is much higher compared to the performance on the test set, you might be overfitting. You want the differences in performance to be minimal. You could apply **bootstrapping** to determine statistical significance.
