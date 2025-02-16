The ==Bayes Network== is a compact representation of a distribution over a very large joint [[probability]] distribution of all of the variables.

They are particularly useful because they provide a compact representation for practically arbitrary distributions, and efficient algorithms exist to sample and perform [[inference]] over the joint distribution.

Once you **specify** the Bayes Network, you can **observe** variables and then compute **probabilities**.

Bayes networks are the building blocks or more advanced AI techniques, such as Particle Filters, Hidden Markov Models, MDP's, POMDP's and Kalman Filters.

![[Pasted image 20231013150757.png]]

Two events are **absolute independence** if the nodes are not connected. However, these two events can become **conditional independence** at the presence of event C.

![[Pasted image 20240205120157.png]]

There are two different types of network:

1. One hidden event that causes two or more observable events, and
2. Two or more independent events that are the confounding cause of an event.

The second type of network is also known as the **explaining away** effect. This effect happens when two absolute independent events can become conditionally independent in the presence of another event.

![[Pasted image 20240205120234.png]]
To simplify the computations in Bayes Nets, we can rewrite the conditional probabilities with **normalization constant**, denoted as **ɑ** (alpha). Given the Bayes Rule, `P(a|b) = P(b|a) P(a) / P(b)`, we can rewrite _P prime_ as `P’ = α P(b|a) P(a)`, where α is a **normalization constant**. Since we know that `P(a|b) + P(¬a | b) = 1`, we can compute `P’(¬a | b)` and get the real [[probability]] of `P(a|b)` by multiplying the normalization constant.

There are two algorithms that to compute _exact inferences_:

1. **Enumeration**: the query’s conditional [[probability]] is computed by summing the terms from the full joint distribution.
2. **Variable Elimination**: an algorithm to reduce the enumeration computation by doing the repeated calculations once and store the results for later re-use.

However, it is computationally expensive to make exact [[inference]] from a large and highly connected Bayes Network. In these cases, we can approximate inferences by sampling. Sampling is a technique to select and count the occurances of the query and evidence variables to estimate the [[probability]] distributions in the network. We looked at four sampling techniques as follows:

1. **Direct sampling**: the simplest form of samples generation from a known [[probability]] distribution. For example, to sample the odds of `Head` or `Tail` in a coin flip, we can randomly generate the events based on uniform [[probability]] distribution (assuming we use a non-bias coin).
2. **Rejection sampling**: generates samples from the known distribution in the network and rejects the non-matching evidence.
3. **Likelihood sampling**: is similar to rejection sampling but generating only events that are consistent with the evidence.
4. **Gibbs sampling**: initiates an arbitrary state and generates the next state by randomly sampling a non-evidence variable, while keeping all evidence variables fixed.


[[bayesian-modeling]]