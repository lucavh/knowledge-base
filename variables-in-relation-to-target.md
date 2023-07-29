```python
# We will plot a subset of the data to keep the plot readable and make the plotting faster
n_samples_to_plot = 5000
columns = ["age", "education-num", "hours-per-week"]
_ = sns.pairplot(
	data=adult_census[:n_samples_to_plot],
	vars=columns,
	hue=target_column,
	plot_kws={"alpha": 0.2},
	height=3,
	diag_kind="hist",
	diag_kws={"bins": 30},
)
```

![[Pasted image 20230729160038.png]]

[[exploratory-data-analysis]]
[[pandas|pandas]]