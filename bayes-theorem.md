The Bayes' theorem (also known as the Bayes' rule) is a mathematical formula used to determine the conditional probability of events and describes the probability of an event based on prior knowledge of conditions that might be related to the event. 

## Mathematical notation

![](https://latex.codecogs.com/gif.latex?\begin{align*}P({A}|{B})%20%20=%20\frac{P({B}|{A})P({A})}{P({B})}\end{align*})

- `B` is the evidence, `A` is the variable we care about. 
- `P(B|A)` is the likelihood
- `P(A)` is the prior
- `P(B)` is the marginal likelihood 
        -> [[law-of-total-probabilities]]: `P(B) = ∑_a P(B|A=a) * P(A=a)`
- `P(A|B)` is the posterior

## Example
```
P(C)   = 0.01
P(¬C)  = 0.99

P(+|C)  = 0.9
P(-|C)  = 0.1
P(+|¬C) = 0.2
P(-|¬C) = 0.8

Joint probabilities:
P(+, C) = 0.01 * 0.9 = 0.009
P(-, C) = 0.01 * 0.9 = 0.001
P(+, ¬C) = 0.01 * 0.9 = 0.198
P(-, ¬C) = 0.01 * 0.9 = 0.792

Chance of having cancer if you have a positive test:
P(C|+) = 0.009 / (0.009 + 0.198) = 0.043

P(C|+) = (P(+|C) * P(C)) / P(+) 
       = (0.9    * 0.01) / (0.9 * 0.01 + 0.2 * 0.99)
```

[[bayesian-modeling]]