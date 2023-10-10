Train-test split with scikit-learn:
```python
X_train, X_test, Y_train, Y_test = train_test_split(
	X, Y,
	train_size=0.7,
	random_state=1234,
	sratify=Y
)
```

[[python]]
[[data-preprocessing]]