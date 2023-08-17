Stateless programming is often preferred.

```python
# statefull (df is modified)
def set_year(df):
    df["year"] = 2021
    return df

# stateless (df is not modified)
def set_year(df):
    return df.assign(year=2021)
```

[[pandas]]