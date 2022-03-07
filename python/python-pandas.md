# Python - Pandas

## Unpacking

```python
my_column_name = "year"

# the following does not work
# column name will be called "my_column_name"
df.assign(my_column_name=2021) 

# instead use
df.assign(**{my_column_name:2021})
```

## Stateless vs statefull

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

## Pipelines

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

## Lambda's & string functions

```python
# as an alternative for
df.rename(columns = lambda column: lower(column))

# use
df.rename(columns = str.lower)
```