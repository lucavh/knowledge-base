
==Probability== is the study of events and outcomes involving an element of uncertainty.

If you flip a coin 4 times in a row, you van never know the outcome in advance with certainty. Yet, you can determine in advance that some outcomes (two heads - two tails) are more likely than others. 

The probability of event A **AND** event B happening is `P(A) * P(B)` -> no dependence.
The probability of event A **OR** event B happening is `P(A) + P(B)`.

Probability allows you to calculate the [[expected-value]]. 
### Notations

- Probability of event A occurring: `P(A)`
- Probability of event A not occurring (complementary): `P(¬A) = 1 - P(A)`
- Probability of sequential events: `P(A,A,A) = P(A) * P(A) ** P(A)`
- Joint probability of both event A and event B occurring: `P(A,B) = P(A & B) = P(A∧B)`
- Conditional probability of event A given event B occurring: `P(A|B)`
### Independent Events

Event A and B are independent if knowing one event does not provide any information about the other event, i.e. events to not influence each other.

Mathematical notations for independence events are as follows:

![](https://latex.codecogs.com/gif.latex?\begin{align*}P({A}\cap%20{%20B})%20&=%20P({A})P({B})%20\\P({A}|{B})%20&=%20P({A})\\\end{align*})
### Conditional Independence

Two independent events of A and B can become conditionally independent in the presence of event C.

![](https://latex.codecogs.com/gif.latex?\begin{align*}P({A}\cap%20{B}|{C})%20=%20P({A}|{C})P({B}|{C})\end{align*})

Example:
```

P(D_1 = sunny)               = 0.9
P(D_2 = sunny | D_1 = sunny) = 0.8
P(D_2 = rainy | D_1 = sunny) = 0.2
P(D_2 = sunny | D_1 = rainy) = 0.6
P(D_2 = rainy | D_1 = rainy) = 0.4
P(D_2 = sunny)               = (0.9 * 0.8) + 
                               (0.1 * 0.6) 
P(D_3 = sunny)               = (0.9 * 0.8 * 0.8) + 
                               (0.9 * 0.2 * 0.6) + 
                               (0.1 * 0.4 * 0.6) + 
                               (0.1 * 0.6 * 0.8)
```

## Problems with probability

1. Assuming events are ==independent== when they are not, e.g. engine failures of an airplane.
2. Not understanding when events are independent:
	1. ==Gamblers fallacy==: mistaken belief that a certain random event is (more) likely to occur given previous events.
	2. ==Not hand fallacy==: mistaken belief that a person who experiences a succesful outcome has a greater success in further attempts.
3. ==Clusters happen==: given enough repetition, unlikely events become more and more likely.
4. ==Prosecutor's fallacy==: when the context around statistical evidence is neglected, the chances of finding a coincidental one in a million match are relatively high if you run a sample through a database of a million records.
5. ==Reversion to the mean== (or [[regression]] to the mean): any outlier is likely to be followed by outcomes that are more consistent with the long-term given enough repeated samples ([[law-of-large-numbers]]).
6. ==Statistical discrimination==: [[statistics]] often contain social complications, it is wrong to unreasonable discriminate against someone on the basis of irrelevant factors using [[statistics]].

[[statistics]]
