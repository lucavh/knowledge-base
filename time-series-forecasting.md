## Take-aways from demand forecasting

### Model

- Strategy:
    1. Find very simple baseline, e.g. sales of last week, 7d moving average, 7d exponential moving average.
    2. Apply a baseline non-linear mode, such as [[LightGBM]] on a limited set of features.
    3. Obtain improvements by adding additional features and optimise model with hyperparameter tuning, etc.
- Train one model per X days ahead forecast. E.g if you want to predict the coming 14 days, train 14 different models.

### Features

- [Cyclic feature encoding](https://towardsdatascience.com/cyclical-features-encoding-its-about-time-ce23581845ca): create features to represent weekly, monthly and yearly patterns.  
- Target encoding: encode the product hierarchy levels as a feature
- Seasonality:
  - Create seasonality vector: divide monthly sales by total sales of a product.
  - Cluster each product by similar seasonal patters and add cluster as feature to the model.  
- Price change: add price change of the product (compared to 7d ago) as a feature

```markdown
# TODO
- With bike rental data set follow strategy above and make some nice graphs like the heatmap as EDA.
- Look into weafflet coefficient 
```

## Tools

- [tsfresh](https://tsfresh.readthedocs.io/en/latest/) - automatically calculates a large number of time series feeatures
- [SHAP](https://shap.readthedocs.io/en/latest/) - explain the output of a machine learning model
- [tsai](https://timeseriesai.github.io/tsai/) - state-of-the-art deep learning library for time series and sequences.

[[machine-learning]]