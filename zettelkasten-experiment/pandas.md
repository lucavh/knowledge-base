## Category data type

Strings are not efficient representations of data. If there are a lot of recurring values in your dataframe, converting the datatype to `category` can provide a significant memory reduction. Pandas does not infer categorical data types automatically. 

```python
df[column] = df[column].astype("category")
```


[[python]]