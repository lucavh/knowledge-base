
- Clip values between a lower band and upper bound using `.clip()`, all values will be replaced by lower and upper limit:
- Absolute value: `df[["numeric_column"]].clip(999, 50000)`
- Percentage: manually compute percentage value using `.quantile()` prior to applying `.clip()`

[[pandas]]
[[data-preprocessing]]