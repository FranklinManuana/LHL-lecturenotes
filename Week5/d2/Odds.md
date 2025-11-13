Before defining “odds” lets revisit the concept of “probability”...

### Probability of an Event

Probability is a type of ratio where we compare how many times an outcome can occur compared to all possible outcomes.

Prob(A) = number of desired outcomes / number of all possible outcomes

Probabilities always range between 0 and 1.

## Back to Odds

The odds are defined as the probability that the event will occur divided by the probability that the event will not occur.

odds = prob(A)/ (1-prob(A))

Let’s walk through the concept with an example. Let’s say, the probability of an event occurring = 0.80, then the odds are 0.80 / (1-0.80) = 0.80/0.20 = 4 (i.e., 4 to 1).

- If a racehorse runs 100 races and wins 25 times and loses the other 75 times, the probability of winning is 25/100 = 0.25 or 25%, but the odds of the horse winning are 25/75 = 0.333 or 1 win to 3 losses.
- If the horse runs 100 races and wins 5 and loses the other 95 times, the probability of winning is 0.05 or 5%, and the odds of the horse winning are 5/95 = 0.0526.
- If the horse runs 100 races and wins 50, the probability of winning is 50/100 = 0.50 or 50%, and the odds of winning are 50/50 = 1 (even odds).
- If the horse runs 100 races and wins 80, the probability of winning is 80/100 = 0.80 or 80%, and the odds of winning are 80/20 = 4/1 = 4

### Connections between Probability and Odds

In summary, if the probability of an event (probability of success) is _p_, then the probability of failure is _q_, where _q_ = 1-_p_ and odds can be calculated as:

Odds = _p_ / (1-_p_) = _p_ / _q_

### Odds and Logistic Regression

Recall that the logistic regression model is given by:

ln(pi/(1-pi)) = β0 + β1xi1 + ... + βpxip

where pi denotes the probability of success (namely, the probability of a response variable falling in a particular class).

The left-hand side of the equation above is the natural logarithm of the odds of success.