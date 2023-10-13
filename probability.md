==Binominal experiment== (Bernoulli trial)
- Fixed number of trials (e.g. 100 taste tests)
- Each trial has 2 possible outcomes (classification)
- Probability og success is the same in each trial
- Assumption: trials are independent

==Probability== is the study of events and outcomes involving an element of uncertainty.

If you flip a coin 4 times in a row, you van never know the outcome in advance with certainty. Yet, you can determine in advance that some outcomes (two heads - two tails) are more likely than others. 

The probability of event A **AND** event B happening is `P(A) * P(B)` -> no dependence.
The probability of event A **OR** event B happening is `P(A) + P(B)`.

## Expected value

Probability allows you to calculate the ==expected value==. That is the sum of all different outcomes, each weighted by its probability and pay-off.

Exemple:
- A game in which you roll a single dice
- Pay off: 1 - $1, 2 - $2, 3 - $3, etc.
- Probability: `1/6` for each possible outcome
- Expected value: `1/6 * $1 + 1/6 * $2 + ... + 1/6 * $6 = $3.50`
- Suppose you have to pay $3 to play the game, then the expected value is higher than the cost of playing. Thus, it's worth taking the risk.

![[Screenshot 2023-10-13 at 12.18.14.png]]
## Problems with probability

1. Assuming events are ==independent== when they are not, e.g. engine failures of an airplane.
2. Not understanding when events are independent:
	1. ==Gamblers fallacy==: mistaken belief that a certain random event is (more) likely to occur given previous events.
	2. ==Not hand fallacy==: mistaken belief that a person who experiences a succesful outcome has a greater success in further attempts.
3. ==Clusters happen==: given enough repetition, unlikely events become more and more likely.
4. ==Prosecutor's fallacy==: when the context around statistical evidence is neglected, the chances of finding a coincidental one in a million match are relatively high if you run a sample through a database of a million records.
5. ==Reversion to the mean== (or regression to the mean): any outlier is likely to be followed by outcomes that are more consistent with the long-term given enough repeated samples ([[law-of-large-numbers]]).
6. ==Statistical discrimination==: statistics often contain social complications, it is wrong to unreasonable discriminate against someone on the basis of irrelevant factors using statistics.

[[statistics]]
