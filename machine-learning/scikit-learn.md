# Scikit-learn

- [scikit-lego](https://scikit-lego.readthedocs.io/en/latest/) repository for custom models not in scikit-learn by default

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