```python
my_column_name = "year"

# the following does not work
# column name will be called "my_column_name"
df.assign(my_column_name=2021) 

# instead use
df.assign(**{my_column_name:2021})
```

[[pandas]]