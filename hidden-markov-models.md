A continuous **Hidden Markov Model (HMM)** is a probabilistic model that assumes two qualitatively distinct unobserved states - in this context, 'pre-crisis' and 'crisis'. Each state is assumed to generate data points from a normal distribution with fixed mean and variance. The model allows for transitions between states at any point in time, including the possibility of remaining in the same state, and identifies the transition from 'pre-crisis' to 'crisis' as the changepoint of interest. 

Of these transitions the move from pre-crisis to crisis only happens once. This is the transition identifying our changepoint of interest. To model time we fix the reverse transition [[probability]] from crisis to pre-crisis to zero in the so-called transition matrix and initialize all others to 50%. During training the HMM fitting algorithm will estimate all non-zero transitions. In addition a mean and variance for each of the two states will be estimated.

To match the assumptions of continuous HMMs better, we first detrend the time series. That is, we don’t model the time series values themselves, but model the difference between consecutive time points. This means that our HMM will be based on the assumption that within each period the mean change per time point is constant with stable variance. This is analogous to the linear assumptions we made in our piecewise linear [[regression]] approach. Below we show two plots:

1. The detrended time series on which the HMM was trained.
2. The periods on the original time series identified by the HMM assuming two distinct time periods or states.

![[Pasted image 20240130091232.png]]
Daily delta value of the original SPYD stock time series.

![[Pasted image 20240130091237.png]]
Two qualitatively different periods identified by the HMM.

The different colors indicate the identified periods. We can therefore use the transition between periods as the detected change point.

Because of their probabilistic nature, HMMs can result in different solutions when fitted multiple times, or worse, not converge at all. These are warning signs that the model assumptions do not match the observed data well. It can sometimes help to smoothen a time series before fitting it to dampen the effect of large outliers.

Resource: https://medium.com/bigdatarepublic/dealing-with-abrupt-market-changes-in-your-analysis-a-brief-tutorial-on-time-series-change-point-3b624295afda