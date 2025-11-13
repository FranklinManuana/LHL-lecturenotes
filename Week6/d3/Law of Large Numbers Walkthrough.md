

Recall that the Law of Large Numbers says that when we repeat an experiment a large number of times, the average result will be very close to _the expected result_, i.e. in the long run, random events tend to average out at _the expected value_.

In this activity, we will focus on visualizing of _the law of large numbers_ using `Python`.

`Example`: Flipping a coin

- If we flipped a coin just 10 times we would not be surprised to get 7 heads (even though _the expected value_ is 5).
    
- But if we flip it 10,000 times we are very unlikely to get 7,000 heads. The result will likely be within a few percent of 5,000.
    

Let's simulate this coin-flipping example with `Python`.

```python
# import numpy
import numpy as np

# set a random seed to replicate the results
np.random.seed(42)

# import matplotlib to visualize the experiment
import matplotlib.pyplot as plt
```

We will begin by running the coin-flipping simulation ten times. We can say that the head is represented by number one and the tail is represented by zero so that we can generate ten random values from a discrete uniform distribution (0 and 1 have the same probabilities).

```python
# generate ten random numbers (0 or 1) with equal probabilities
coin_flips_10 = np.random.randint(0,2,10)
```

Calculate how many heads we got in those ten coin flips.

```python
# how many heads in 10 coin flips
count_heads = sum(coin_flips_10 == 1)
print(count_heads)
```

We can see that the number of heads in these ten coin flips was three, rather than the expected 5. Let's simulate a different number of coin flips and store the results.

```python
# empty list used to store the results
heads_ratio_nflips = []

# generate integers from 5 to 10,000
n_flips = np.arange(5,10000)

for flips in n_flips:
    # how many heads / flips
    heads_ratio = sum(np.random.randint(0,2,flips) == 1) / flips

    # append ratios
    heads_ratio_nflips.append(heads_ratio)
```

Now that we have computed the heads ratio for each number from 5 flips to 10,000 flips, we can plot the results.

```python
# set plot size
plt.figure(figsize=(10,8))

# number of flips on the x axe and heads ratio on y axe
plt.plot(n_flips, heads_ratio_nflips)

# expected ratio
plt.plot(n_flips, len(n_flips)*[0.5], 'r--')

# plot settings
plt.figure(figsize=(10,8))
plt.xlabel('Flips')
plt.ylabel('Heads ratio')
plt.show()
```

In the chart above, we can see that when the number of flips increases the heads ratio converges to _the expected value_.

---