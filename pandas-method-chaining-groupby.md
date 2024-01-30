In [[pandas-method-chaining]], operations are applied to a dataframe in a sequence. Some operations can be tricky to formulate correctly in a chain, such as te `groupby` operation.

Given a sample dataset:
```python
df = pd.DataFrame({
   "Item": ["A","A","B","B"],
   "Value": [1,2,3,4],
   "Another value": [10,45,30,24]
})
```

| | Item | Value | Another value |
|---:|-------:|--------:|:----------------|
| 0 | A | 1 | 10 |
| 1 | A | 2 | 45 |
| 2 | A | 3 | 30 |
| 3 | A | 4 | 24 |

## Problem one: keep original index with aggregated values

```python
(
	df
	.set_index("Item")
	.groupby("Item")
	.transform("max")
)
```

| Item | Value | Another value |
|:-------|--------:|----------------:|
| A | 2 | 45 |
| A | 2 | 45 |
| B | 4 | 30 |
| B | 4 | 30 |


```python
(
	df
	.set_index("Item")
	.assign(new_value = lambda x: x.groupby("Item")["Value"].max())
)
```

| Item | Value | Another value | new_value |
|:-------|--------:|----------------:|------:|
| A | 2 | 45 | 2 |
| A | 2 | 45 | 2 |
| B | 4 | 30 | 4 |
| B | 4 | 30 | 4 |

## Problem two: aggregate df, but without multilevel columns

```python
(
	df
	.groupby("Item")
	.agg(
		value_list = ("Value", list),
		value_mean = ("Value", "mean"),
		another_value_max = ("Another value", "max")
	)
)
```

| Item | value_list | value_mean | another_value_max |
|:-------|:-------------|-------------:|--------------------:|
| A | [1, 2] | 1.5 | 45 |
| B | [3, 4] | 3.5 | 30 |