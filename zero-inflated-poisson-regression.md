If we assume that **_y_** is a Poisson distributed random variable, we can build a Poisson regression model for this data set. The Poisson model is made up of two parts:

1. A Poisson **P**robability **M**ass **F**unction (PMF) denoted as _P(y_i=k)_ used to calculate the probability of observing _k_ events in any unit interval given a mean event rate of λ events / unit time.
2. A link function that is used to express the mean rate λ as a function of the regression variables **_X_.**

Normally, we assume that there is some underlying process that is producing the observed counts as per the Poisson _PMF: P(y_i=k)_.

The intuition behind the Zero Inflated Poisson model is that **_there is a second underlying process that is determining whether a count is zero or non-zero_**. Once a count is determined to be non-zero, the regular Poisson process takes over to determine its actual non-zero value based on the Poisson process’s PMF.

Thus, a **ZIP** regression model consists three parts:

1. A PMF _P(y_i=0)_ which is used to calculate the probability of observing a zero count.
2. A second PMF _P(y_i=k)_ which is used to calculate the probability of observing _k_ events, _given that k > 0_.
3. A link function that is used to express the mean rate λ as a function of the regression variables **_X_.**

![[Pasted image 20240430133526.png]]