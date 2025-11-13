In this activity, we will learn how to generate random values from various distributions using the `Numpy` library. You will also learn how to plot **a probability mass function (PMF)** for a discrete random variable and **a probability density function (PDF)** for a continuous random variable.

Instruction

Before we start, get familiar with [this Python tool called `Counter`](https://docs.python.org/3.8/library/collections.html#collections.Counter).

### Importing Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
from collections import Counter

# set the plot style
plt.style.use('fivethirtyeight')
```

To generate a random number between 0 and 1 (zero included, one excluded) we will use `random()` function from `numpy.random` module.

```python
random_num = np.random.random()
random_num
```

In case we want to generate a list of `n` random numbers we will also use `random()` with `n` as an argument.

```python
# generate 4 random numbers from the interval  <0,1)
random_num = np.random.random(4)
random_num
```

Warning

`numpy.random.random()` is a pseudorandom number generator. It is a mathematical function that generates a sequence of nearly random numbers. It takes a parameter to start the sequence, called **the seed**. The function is deterministic, meaning, given the same _seed_, it will produce the same sequence of numbers every time.

If we want to set _the seed_ to obtain the same result each run, we can use the following command before every generation:

```python
# this sets the seed to number 42
np.random.seed(42)
```

### Binomial Distribution (Discrete Distribution)

Note

**Binomial distribution** with parameters `n` and `p` is a discrete probability distribution.

We will demonstrate _binomial distribution_ with a coin-flipping example. Imagine we toss a fair coin (the probability of getting heads or tails is 0.5) ten times. We want to know the probability of getting four heads as an outcome. Let's simulate this process in `Python`.

```python
# n = the number of coin tosses
# p = the probability of getting heads
# size = the number of repeats 

n = 10
p = 0.5
size = 1000

samples = np.random.binomial(n, p, size)
```

As we can see, `samples` is an array with the size of 1,000. Each number in the array represents how many times, out of 10 tosses, we get heads. Now we have to compute how many times each number occurs in the array.

```python
# count the occurrence of each number
head_occu_count = Counter(samples) 
```

Calculate the probabilities:

```python
# calculate the probabilities as the number of occurences / size
head_proba = [val/size for val in head_occu_count.values()]
```

Plot the distribution:

```python
plt.scatter(x=head_occu_count.keys(), y=head_proba)
plt.xlabel('number of heads out of 10 tosses')
plt.ylabel('probability')

# show the plot
plt.show()
```

From the distribution, we can see that the probability of having four heads out of ten trials is around 0.2.

### Normal Distribution (Continuous Distribution)

Note

**Normal distribution** with the `mean` and `variance` parameters is a continuous probability distribution.

_A normal distribution_, also known as a **Gaussian distribution**, is a probability distribution that is symmetric around the mean, showing that data near the mean are more frequent in occurrence than data far from the mean. In a graph, the normal distribution will appear as a bell curve.

Let's generate _normally distributed_ data with `Numpy`:

```python
# loc = mean (“a centre”) of the distribution.
# scale = standard deviation (a spread or “a width”) of the distribution.

samples = np.random.normal(loc=0, scale=1, size = 1000000)
```

Warning

`np.random.normal()` takes `mean` and `standard deviation` as input parameters.

In the example above, we generated _a normal distribution_ with `mean = 0` and `std = 1`.

Let's plot the distribution, i.e. _the probability density function_:

```python
plt.hist(samples, density=True, histtype="step", bins=100)

# show the plot
plt.show()
```

Warning

For a continuous random variable, _the probability density function_ provides the height, or value, of the function for any particular value of _x_. It does not directly give us the probability of the random variable taking on a specific value. However, the area under the graph corresponding to a certain interval provides the probability that the variable will take on a value within that interval.

The probability that we take a number smaller than zero from our `sample` array from the previous example equals 0.5 (because the area under _the PDF_ from minus infinity to zero is 0.5).

But how does our `PDF` change with different parameters of _the normal distribution_?

Let's try a couple of options and plot the results. In the first example, we will change the values of `std` parameter.

```python
samples_std1 = np.random.normal(20, 1, size=100000)
samples_std3 = np.random.normal(20, 3, size=100000)
samples_std10 = np.random.normal(20, 10, size=100000)

# make histograms
plt.hist(samples_std1, density = True, histtype="step", bins=100)
plt.hist(samples_std3, density = True, histtype="step", bins=100)
plt.hist(samples_std10, density = True, histtype="step", bins=100)

# make a legend, set limits, and show the plot
plt.legend(('std = 1', 'std = 3', 'std = 10'))
plt.ylim(-0.01, 0.42)
plt.show()
```

As we can see from _the PDFs_, the higher the `std` value is the more spread out the distribution.

But what will happen when we change the values of the `mean` parameter?

```python
samples_std1 = np.random.normal(10, 3, size=100000)
samples_std3 = np.random.normal(20, 3, size=100000)
samples_std10 = np.random.normal(30, 3, size=100000)

# make histograms
plt.hist(samples_std1, density = True, histtype="step", bins=100)
plt.hist(samples_std3, density = True, histtype="step", bins=100)
plt.hist(samples_std10, density = True, histtype="step", bins=100)

# make a legend, set limits, and show the plot
plt.legend(('mean = 10', 'mean = 20', 'mean = 30'))
plt.ylim(-0.01, 0.42)
plt.show()
```

In this case, the width of our distributions did not change but the distributions shifted along the x-axis.

Instruction

Explore more functions from [the `numpy.random` module](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.random.html).