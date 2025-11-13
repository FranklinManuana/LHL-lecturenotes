## Conditional Probability

In this activity, we will look at a simple example to learn how to make _a conditional probability_ simulation with `Python`.

### Example: Soccer Game

You are off to play soccer and want to be the goalkeeper but whether you get to play that position depends on who will be coaching today:

- with coach Sam, the probability of being the goalkeeper is 0.5
- with coach Alex, the probability of being the goalkeeper is 0.3

You also know that Sam coaches more often – about six out of every ten games (a probability of 0.6).

So, what is the probability that you will be the goalkeeper today?

Let's make a simulation of this example using `Python`.

```python
# import numpy 
import numpy as np
```

Now, we have to set the number of times we want to simulate this process and initialize all variables with zero.

```python
# how many times we run the simulation
n_runs = 100000

# initialize variables
SAM = 0
SAM_YES = 0
SAM_NO = 0
ALEX = 0
ALEX_YES = 0
ALEX_NO = 0
YES = 0
NO = 0
```

After we set all the variables to their initial value, we need to write a loop that will simulate the process.

```python
# process simulation
for _ in range(n_runs):
    # Sam (probability of Sam being the coach)
    if np.random.random() < 0.6: 
        SAM += 1

        # YES
        if np.random.random() < 0.5:
            SAM_YES += 1
            YES +=1

        # NO
        else:
            SAM_NO += 1
            NO += 1

    #Alex (probability of Alex being the coach)
    else:
        ALEX += 1

        # YES
        if np.random.random() < 0.3:
            ALEX_YES += 1
            YES += 1

        # NO
        else:
            ALEX_NO += 1
            NO +=1
```

The simulation above is based on a random number generator (`np.random.random`), which generates any number from the interval <0,1> with equal probability. If the generated number is less than 0.6 we can say that the coach is Sam (because Sam is the coach in 60% of games). Then we generate another random number and if the value is less than 0.5 (the chance of being the goalkeeper when Sam is coaching is 50%), it means you will be the goalkeeper. In that case, we will increase the value of variables `SAM_YES` and `YES` by one. It means that in this simulation run you are the goalkeeper and Sam is the coach. We run this process 100,000 times and check the result.

```python
# create probabilities
P_SAM = SAM / n_runs * 100
P_SAM_YES = SAM_YES / n_runs * 100
P_SAM_NO = SAM_NO / n_runs * 100
P_ALEX = ALEX / n_runs * 100
P_ALEX_YES = ALEX_YES / n_runs * 100
P_ALEX_NO = ALEX_NO / n_runs * 100
P_YES = YES / n_runs * 100
P_NO = NO / n_runs * 100
```

Print the probabilities.

```python
print(f'Sam is the coach: {P_SAM}%')
print(f'Sam is the coach and you are the goalkeeper: {P_SAM_YES}%')
print(f'Sam is the coach and you are not the goalkeeper: {P_SAM_NO}%')
print(f'Alex is the coach: {P_ALEX}%')
print(f'Alex is the coach and you are the goalkeeper: {P_ALEX_YES}%')
print(f'Alex is the coach and you are not the goalkeeper: {P_ALEX_NO}%')
print(f'You are the goalkeeper: {P_YES}%')
print(f'You are not the goalkeeper: {P_NO}')
```

As we can see, the probability of being the goalkeeper is around 42%. We can also check the probability of Sam being the coach given that you are the goalkeeper.

```python
# P(Sam | goalkeeper)
P_SAM_GOAL = P_SAM_YES / P_YES
print(P_SAM_GOAL)
```

We computed this probability as the probability of you being the goalkeeper while Sam is the coach, divided by the total probability that you are the goalkeeper. The probability is around 72%, which means that in 72 out of 100 games in which you are the goalkeeper, your coach is Sam.