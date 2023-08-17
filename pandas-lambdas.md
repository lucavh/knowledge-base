An example of using lambda's:
```python
df.rename(columns = lambda column: lower(column))
```

In some cases, default functions can be used, such as string functions:
```python
df.rename(columns = str.lower)
```

[[pandas]]