Exclude features if:

- Too many **missing values**  
- Too little value **variance** (see [VarianceThreshold](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.VarianceThreshold.html#sklearn.feature_selection.VarianceThreshold))
- **High correlation** with the target or other features

Automatic feature selection methods:

- **Statistical testing** where little contributing features are removed (see [SelectKBest](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectKBest.html#sklearn.feature_selection.SelectKBest)).
- **Model-based selection** where a(n often penalized) model is used to the determine and eliminate the least contributing features (see [SelectFromModel](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectFromModel.html#sklearn.feature_selection.SelectFromModel)).

In practice, `SelectFromModel` is most often used in combination a _penalized_ model. By adding a special component to the cost function, complex models are penalized. `Lasso` is most used for regression problems and `LinearSVC(penalty="l1")` for classification problems (linear SVM with Lasso-like penalty term).

[[data-preprocessing]]