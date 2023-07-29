## Types of models

- Classification
- Regression
- Clustering
- Anomaly detecton

## What to consider while choosing an algorithm?

1. Accuracy
2. Training time
3. Number of featres
4. Number of parameters
5. Linearity

## Data Science Lifecycle

1. Business Case and Discovery
2. Data Processing
3. Model Planning
4. Model Building and Selection
5. Present Result
6. Deploy

## Performance metrics

### Error metrics

- **MAE**: Mean Absolute Error
- **RMSE**: Root Mean Squared Error
	- Compared to MAE, RMSE amplifies and severely punishes large errors
- **RAE**: Relative Absolute Error, absolute error divided by sum of abs diff to mean

### Regression

- **R-Squared**/**Coefficient of Determination**: How much (what %) of variantion in Y is described by the variation in X? Higher value means that variation in Y is explained by variation in X.

![[r2_score.png]]

### F1 Score 

Weighted average of precision and recall:

```
F1 = (2 * precision * recall ) / (precision + recall)
```

### AUC-ROC

![[roc-curve.webp]]

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


## Data normalization

Normalization is a method to standardise the range of independent variables or features of data.

Most commonly used transformation methods:

- Z-score
	- `Z = (X - mean(x)) / stdev(x)`
	- Data can vary from any negative value to any positive value, but will always have a standard deviation of 1.
- MinMax
	- `Z = (X - min(x)) / (max(x) - min(x))
	- Data will always be on a scale from 0 to 1.
- Logistic
	- `Z = 1 / (1 + exp(-x))

## Python

- Clipping values
	- Clip values between a lower band and upper bound using `.clip()`, all values will be replaced by lower and upper limit:
	- Absolute value: `df[["numeric_column"]].clip(999, 50000)`
	- Percentage: manually compute percentage value using `.quantile()` prior to applying `.clip()`
- Convert string to category index
	- `df["string_column"].cat.codes`
- One-hot encoding
	- `pd.get_dummies(df)`
- Train-test split with scikit-learn
```python
X_train, X_test, Y_train, Y_test = train_test_split(
	X, Y,
	train_size=0.7,
	random_state=1234,
	sratify=Y
)
```

## Classification

### Regression

Types of regression:
- Ordinal Regression: data in rank order categories
- Poisson Regression: predicting event counts
- Fast Forest Quantile Regression: predicting a distribution
- Linear Regression: fast training, linear model
- Bayesian Linear Regression: linear model, small datasets
- Neural Network Regression: accuracy, long training time
- Decision Forest Regression: accuracy, fast training
- Boosted Decision Tree Regression: accuracy, fast training, large memory

**Ordinary Least Squares**: finding the minimum of the sum of squared errors of all data points.

### Logistic Regression

![[linear-vs-logistic-regression.png]]

Model hyperparameters:
- Trainer mode: how you want the model to be trained
	- Single parameter: privde specific set of values
	- Parameter range: specift multiple values and get the optimum set for given configuration
- Optimization tolerance: threshold to stop when model is not optimizing beyond this value
- L2 regularization

#### Regularization

- L1 (Lasso) can shrink some coefficients to zero, performing variable selection.
- L2 (Ridge) shrinks all the coefficients by the same proportions but eliminates none
- Both L1 and L2 regularization prevent overfitting by shrinking (imposing a penalty) on the coefficients.
- With L2, you tend to end up with many small weights, while with L1, you tend to end up with larger weights, but more zeros.

### Decision Tree

#### Ensemble Learning

- Generate a group of base learners and combine results to yield higher accuracy
- Different base learnings can use different: parameters, sequence, training sets, etc.
- Two major Ensemble Learning Methods:
	- Bagging 
	- Boosting

##### Bagging (Decision Forest)

- Various models in parallel using a bag of the data, i.e. splitting the data and creating different bags on which each of the base learner is modelled.
- All models vote to give the final prediction.
- Votes are combined by majority.

##### Boosting

- Train the Decision Tree in a sequence
- Learn from the previous tree by focussing on incorrect observations
- Build new model with higher weight for incorrect observations from previous sequence

### Gradient Descent

- **Rate of change**: the slope of the line. Given a line, the rate of change is computed by the  change in Y divided by the change in X between two points
- **Learning rate** is the stepsize. Too large and you miss the actual optimum, too small and it might take too long to reach the bottom. Common practice is to do large steps in the beginning and smaller steps towards the end.
- Epochs are a single iteration/step in the gradient descent.

**Online or Stochastic Gradient Descent**: reading one observation at a time, modify the coefficient at every step. 

**Mini Batch Gradient Descent**: instead of taking one observation at a time (like with stochastic gradient descent), we take a small batch and modify the coefficient on this small subset each step.