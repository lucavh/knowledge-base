```python
def set_index(df, col):
    return df.set_index(col).sort_values(col)

def filter_years(df, start_year="2004", end_year="2014"):
    return df.loc[start_year:end_year]

(
    df
    .pipe(set_index, col="date")
    .pipe(filter_years)
)
```

[[pandas]]