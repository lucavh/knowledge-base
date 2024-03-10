**Piecewise linear regression (PLR)** is a technique used in statistics deal with abrupt changes in your time series data. The main idea is to fit a time series by minimizing the mean squared error of **several connected lines**, as opposed to the standard linear regression, which minimizes mean squared error.

In PLR, transitioning from one line to another can occur anywhere, making it a challenging problem. To prevent overfitting, it is crucial to limit the number of lines used. 

The connection of the lines in PLR can be utilized to identify when one period transitions into another, with the slope indicating the average change in the metric or index during these periods. 

While PLR is conceptually simple and effectively identifies abrupt transition points and rate of change within each period, a notable disadvantage is the somewhat arbitrary nature of choosing the number of lines without a ground truth, emphasizing the importance of verifying the solution.

![[Pasted image 20240130090610.png]]
Fit of piecewise linear regression (green) on a smoothened version (orange) of the stock value time series (blue).

[[linear-regression]]