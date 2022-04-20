# Machine Learning

- [ML cheatsheet glossary](https://ml-cheatsheet.readthedocs.io/en/latest/glossary.html)
- [Google Machine Learning glossary](https://developers.google.com/machine-learning/glossary)
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

## Learning algorithms

### Anatomy of a learning algorithm

Each learning algorithm consists of three parts:

1. a **loss function**, also called **objective** or **objective function**
2. an **optimization criterion** based on the loss function (e.g. a **cost function** - minimizing the loss function)
3. an **optimization routine** leveraging training data to find a solution to the optimization criterion (such as **gradient descent**)

### Notation & terminology

Typical ML model notation: $f(X,w) = y$, where $X$ is a metrix with all the features and `y` is a vector with the target variable.

As $f_{x}$ is usually unknown, but a sample ($X$) is available, we accept to not find the true values, but the **unbiased estimators**.

### Derivate and gradient

**Gradient** is the generalization of **derivative** for functions that take several inputs (or one input in the form of a vector). A gradient of a function is a vector of **partial derivatives**. Partial derivatives are determined by focusing on one of the function's inputs and by considering all other inputs as constant values (notation: $\frac{\partial f}{\partial x}$).

### Hyperparameters & parameters

**Hyperparameters** are external parameters that can be tweaked to optimize the cost function (e.g. number of hidden layers), **parameters** are internal to the model and determined during model fit (e.g. weights).

### Linear regression

- **Squared error loss** is commonly used as loss function, minimization of this objective is also known as **cost function** or **empirical risk**.
- **Intercept problem**: when fitting a linear model, you might want to not fit the intercept (in scikit-learn: `fit_intercept=False`). Additionally you might want to add an offset to the prediction which is the mean of the intercept value (in scikit-learn: `model.predict + offset`)
- **Non-linear relationship**: linear models can be used even in settings where data and target are not linearly linked. A polynomial transformation can be applied to encode non-linear interactions between features.
- **Regularization**: it is advised to always use a penalty to shrink the magnitude of the weights toward zero (also called "l2 penalty"). In scikit-learn, `LogisticRegression` applies such penalty by default (with hyperparameter `C`). However, one needs to use `Ridge` (and even `RidgeCV` to tune the hyperparameter `alpha`) instead of `LinearRegression`.
- **Corrolation**: highly corrolated features can lead to numerical problems. Applying regularization can help overcome these issues.

### Logistic regression

- Utilizes a **standard logistic function** (also known as **sigmoid function**) whose codomain is $(0,1)$.
- Optimization criterion: maximization of the **likelihood**

### Decision tree learning

- **Pruning**: a bottom-up technique against overfitting. Pruning consists of going back through the tee once it's been created and removing branchs that don't contibute significantly enhough to the error reduction by replacing them with leaf notes.

### Support Vector Machines (SVM)

- Finding the **decision boundary** (or hyperplane) with the largest **margin**
- **Hinge loss**: a penalty function for balancing the tradeoff between classifying the training data well (minimizing emperical risk) and classifying future examples well.
- **Kernel trick**: function to implicitly transform the original space into a higher dimension space during the cost function optimization.

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

### Underfitting & overfitting

- Models overfit:
  - number of examples in the training set is too small
  - testing error is much bigger than training error
  - high variance: unstable models
- Models underfit:
  - models fail to capture the shape of the training set
  - even the training error is large
  - high bias: misspecified models

Approach:

- **Compare train and test errors**: identify whether a model is generalizing, overfitting, or underfitting.
  - We observe a ****small training error** (actually zero), meaning that the model is not under-fitting: it is flexible enough to capture any variations present in the training set.
  - However the **significantly larger testing error** tells us that the model is over-fitting: the model has memorized many variations of the training set that could be considered “noisy” because they do not generalize to help us make good prediction on the test set.
  
![](../images/cv_train_test.png)

- **Validation curve**: check influence of a hyperparameter on the tradeoff underfit/overfit.
  - Looking at the curve, we can clearly identify the over-fitting regime of the SVC classifier when `gamma > 1`. The best setting is around `gamma = 1` while for `gamma < 1`, it is not very clear if the classifier is under-fitting but the testing score is worse than for `gamma = 1`.

![](../images/cv_validation_curve.png)

- **Learning curve**: the influence of the number of samples in a dataset, especially on the variability of the errors reported when running the cross-validation.
  - We observe that adding new samples to the training dataset does not seem to improve the training and testing scores. In particular, the testing score oscillates around 76% accuracy. Indeed, ~76% of the samples belong to the class `not donated`.

![](../images/cv_learning_curve.png)