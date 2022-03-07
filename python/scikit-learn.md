# Scikit-learn

- [scikit-lego](https://scikit-lego.readthedocs.io/en/latest/) repository for custom models not in scikit-learn by default

## Model parameters (scikit-learn convention)

If an attribute is learned from the data, its name ends with an underscore (i.e. `_`), as in `mean_` and `scale_` for the `StandardScaler`.

## Preprocessing

### Select features based on their column type

```python
from sklearn.compose import make_column_selector as selector

numerical_columns_selector = selector(dtype_exclude=object)
categorical_columns_selector = selector(dtype_include=object)

numerical_columns = numerical_columns_selector(data)
categorical_columns = categorical_columns_selector(data)
```

## Preprocessing pipeline with `ColumnTransformer`

```python
from sklearn.preprocessing import OneHotEncoder, StandardScaler
from sklearn.compose import ColumnTransformer

categorical_preprocessor = OneHotEncoder(handle_unknown="ignore")
numerical_preprocessor = StandardScaler()

preprocessor = ColumnTransformer([
    ('one-hot-encoder', categorical_preprocessor, categorical_columns),
    ('standard_scaler', numerical_preprocessor, numerical_columns)])
```

### Feature scaling

Some reasons for scaling features:

- Models that rely on the distance between a pair of samples, for instance k-nearest neighbors, should be trained on normalized features to make each feature contribute approximately equally to the distance computations.
- Many models such as logistic regression use a numerical solver (based on gradient descent) to find their optimal parameters. This solver converges faster when the features are scaled.

Whether or not a machine learning model requires scaling the features depends on the model family. Linear models such as logistic regression generally benefit from scaling the features while other models such as decision trees do not need such preprocessing (but will not suffer from it).

## Encoding of categorical variables

In general `OneHotEncoder` is the encoding strategy used when the
downstream models are **linear models** while `OrdinalEncoder` is often a good strategy with **tree-based models**.

Using an `OrdinalEncoder` will output ordinal categories. This means
that there is an order in the resulting categories (e.g. `0 < 1 < 2`). The impact of violating this ordering assumption is really dependent on the downstream models. Linear models will be impacted by misordered categories while tree-based models will not.

You can still use an `OrdinalEncoder` with linear models but you need to be sure that:

- the original categories (before encoding) have an ordering;
- the encoded categories follow the same ordering than the original
  categories.

One-hot encoding categorical variables with high cardinality can cause computational inefficiency in tree-based models. Because of this, it is not recommended to use `OneHotEncoder` in such cases even if the original categories do not have a given order.

### Ordinal categories

```python
from sklearn.preprocessing import OrdinalEncoder

encoder = OrdinalEncoder(categories=["S", "M", "L", "XL"])
data_encoded = encoder.fit_transform(data[["size"]])
```

### Nominal categories (without assuming any order)

```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder(sparse=False)
data_encoded = encoder.fit_transform(data_categorical)

columns_encoded = encoder.get_feature_names_out(data_categorical.columns)
data_encoded = pd.DataFrame(data_encoded, columns=columns_encoded)
```

## Cross validation

- __Train-test split__: evaluate the generalization performance on unseen data
- __Cross-valudation__: evaluate the variability of your estimation of the generalization performance

```python
from sklearn.model_selection import cross_val_score

# Basic cv
cv = KFold(n_splits=5, shuffle=False)

# Bootstrapping cv
cv = ShuffleSplit(n_splits=2,  test_size=0.2, random_state=0)

test_scores = cross_val_score(model, data, target, cv=cv)
```

```python
from sklearn.model_selection import cross_validate

cv_results = cross_validate(model, X, y)

scores = cv_results["test_score"]
print("The mean cross-validation accuracy is: {scores.mean():.3f} +/- {scores.std():.3f}")
```

## Template for custom transformer

```python
from sklearn.base import BaseEstimator, TransformerMixin

class CustomTransformer(BaseEstimator, TransformerMixin):

    def __init__(self, my_arg):
        # super().__init__() --> use __init__() of parent class, in this case not needed as BaseEstimator does not have init method
        self.my_arg = my_arg
        
    def fit(self, X, y=None):
        self.my_param_ = ... # trailing _ to indicate that parameter is set during fitting/training
        return self
    
    def transform(self, X):
        X_transformed = ...
        return X_transformed
```

## Template for custom estimator

```python
from sklearn.base import BaseEstimator

class CustomEstimator(BaseEstimator):
    
    def __init__(self, my_arg):
        # super().__init__() --> use __init__() of parent class, in this case not needed as BaseEstimator does not have init method
        self.my_arg = my_arg
        
    def fit(self, X, y=None, **fit_params):
        estimator = ...
        self.estimator_ = estimator.fit(X, y=y)  # trailing _ to indicate that parameter is set during fitting/training
        return self
    
    def predict(self, X, **predict_params):
        check_is_fitted(self, ["estimator_"])
        return self.estimator_.predict(X)
```
