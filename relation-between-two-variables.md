```python
# Cross table
pd.crosstab(index=adult_census["education"], columns=adult_census["education-num"])

# Jointplot
num_points_to_plot = 300
_ = sns.jointplot(data=adult_census[:num_points_to_plot], x="age",
y="hours-per-week", marginal_kws=dict(bins=15))
_ = plt.suptitle("Jointplot of 'age' vs 'hours-per-week'", y=1.1)
```

![[Pasted image 20230729155816.png]]

[[exploratory-data-analysis]]
[[pandas|pandas]]