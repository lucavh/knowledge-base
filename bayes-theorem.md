The Bayes' theorem (also known as the Bayes' rule) is a mathematical formula used to determine the conditional [[probability]] of events and describes the [[probability]] of an event based on prior knowledge of conditions that might be related to the event. 

![](https://latex.codecogs.com/gif.latex?\begin{align*}P({A}|{B})%20%20=%20\frac{P({B}|{A})P({A})}{P({B})}\end{align*})

- `B` is the evidence, `A` is the variable we care about. 
- `P(B|A)` is the likelihood
- `P(A)` is the prior
- `P(B)` is the marginal likelihood 
        -> [[law-of-total-probabilities]]: `P(B) = ∑_a P(B|A=a) * P(A=a)`
- `P(A|B)` is the posterior

### Explaining away tric
Given `A -> B <- C` (conditional dependence):

![](https://latex.codecogs.com/svg.image?&space;P(A|B,C)=\frac{P(B|A,C)P(A|C)}{P(B|C)})

![[Pasted image 20240205120300.png]]


![[Screenshot 2023-12-19 at 15.48.20.png]]
![[Screenshot 2023-12-19 at 15.57.23.png]]
![[Screenshot 2023-12-19 at 15.59.19.png]]

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

```
Two test cancer example

P(C)    = 0.01 -> prop. of cancer
P(+|C)  = 0.9  -> prop. of positive test given cancer
P(-|!C) = 0.8  -> prop. of negative test given no cancer

--------------------------------------
=> P(C|T1=+, T2=+) = ?

    prior  +    +     P`      P(C|++)
C   0.01   0.9  0.9   0.0081  0.1698
!C  0.99   0.2  0.9   0.0396  0.8301

P` is non-normalized (don't add up to 1). 

These values can be normalized by dividing them by the sum of the two P` values: 
1. 0.0081 + 0.0396 = 0.0477
2. 0.0081 / 0.0477 = 0.1698 and 
   0.0396 / 0.0477 = 0.8301
3. 0.1698 + 0.8301 = 1

Answer is P(C|T1=+, T2=+) = 0.1698
--------------------------------------
=> P(C|T1=+, T2=-) = ?

    prior  +    -     P`      P(C|++)
C   0.01   0.9  0.1   0.0009  0.0056
!C  0.99   0.2  0.8   0.1584  0.9943

Answer is P(C|T1=+, T2=+) = 0.0056
```

[[bayesian-modeling]]


prior  +    +     P`      P(C|++)
C   0.01   0.9  0.9   0.0081  0.1698
!C  0.99   0.2  0.9   0.0396  0.8301


P(+|C)  = 0.9 
P(+|!C) = 0.2


P(+) = P(+|C) * P(C) + P(+|!C) * P(!C) = (0.9 * 0.01) + (0.2 * 0.99) = 0.009 + 0.198 = 0.207

P(T2=+|T1=+) = P(T1=+ and T2=+) / P(T1=+)

P(C|+)= 0.043

