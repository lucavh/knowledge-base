==Regression analysis== allows you to quantify the relationship beween a particular variable and an outcome that you care about while controlling for other variables.

The regression algorithm seeks to find the "best fit" for a ==linear relationship== between two variables. Fitting regression line using ordinary least squared (OLS) -> `y = ax + b`

==Dependent variable==: variable that is being explained.
==Explanatory variables==: variables used to explain the dependent variable. Also referred to as independent or control variables.

==R^2== is a measure for the total amount of variation explained by the regression equation (see also [[model-evaluation]]).

==T-distribution== if sample is `n < 30`, looks like the normal distribution with fatter tails. When the number of degrees of freedom gets large, the t-distribution converges to the normal distribution.
## Common regression mistakes

1. Use regression to analyse non-linear relationship.
2. Correlation does not equal causation.
3. Reverse causality: don't use explanatory variable that might be affected by the dependent variable.
4. Ommited variable bias: when you leave out crucial explanatory variables, another variable might "pick-up" the effect.
5. Highly correlated explanatory variables (multi-collinearity): use either one or create one combined variable.
6. Extrapolating beyond the data: results are valid only for a population that is similar to the sample on which the analysis is performed.
7. Data mining: with too many variables, one is bound to meet the threshold for significance just by chance.
## Common types of regression

- Ordinal Regression: data in rank order categories
- Poisson Regression: predicting event counts
- Fast Forest Quantile Regression: predicting a distribution
- [[linear-regression]]: fast training, linear model
- [[bayesian-modeling]] Linear Regression: linear model, small datasets
- [[neural-networks]] Regression: accuracy, long training time
- Decision Forest Regression: accuracy, fast training
- Boosted Decision Tree Regression: accuracy, fast training, large memory

[[statistics]] [[machine-learning]]