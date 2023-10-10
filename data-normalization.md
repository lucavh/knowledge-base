Data normalization is a method to standardise the range of independent variables or features of data.

Most commonly used transformation methods:

- Z-score
	- `Z = (X - mean(x)) / stdev(x)`
	- Data can vary from any negative value to any positive value, but will always have a standard deviation of 1.
- MinMax
	- `Z = (X - min(x)) / (max(x) - min(x))
	- Data will always be on a scale from 0 to 1.
- Logistic
	- `Z = 1 / (1 + exp(-x))


[[data-preprocessing]]