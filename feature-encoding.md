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

[[data-preprocessing]]