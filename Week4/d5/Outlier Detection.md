## Outlier Detection

Another important part of EDA and data preparation is the **Outlier Detection**. Sometimes, we have to deal with observations that are "extreme". Left ignored, these extremes can interfere with our model so it is important to address them at the outset.

### What is an Outlier?

An _an outlier_ is an observation that appears far away and diverges from an overall pattern in a sample. Outliers require close attention, or else they can result in wildly wrong estimations.

We have two main types of _outliers_:

- **Univariate**: we are looking at one variable at a time
- **Multivariate**: even though there are no univariate _outliers_, we can spot some extreme values if we look at the values of multiple variables at the same time.

There are a lot of reasons why _outliers_ occur:

- **Data Entry Errors** – e.g. people make mistakes when filling in a survey.
- **Measurement Errors** – e.g. a device recording various measurements can be faulty.
- **Experimental Errors** – we can make a mistake when experimenting.
- **Intentional Outliers** – people can make "mistakes" intentionally, for example, in a loan application.
- **Sampling Errors** – e.g. we might take a sample which is too small.
- **Natural Outliers** – e.g. there might be a lot of snow one year and no snow in the following one.

### What is the Impact of Outliers on a Dataset?

_Outliers_ can drastically change the results of data science projects. There are numerous impacts of _outliers_ in a data set:

- They increase the error variance, therefore, reducing the power of statistical tests.
- They can bias or influence estimates that may be of substantive interest.
- They can also impact the basic assumption of a regression, and other statistical model assumptions.

To better understand the impact, let’s take a look at an example to see what happens to a data set with and without _outliers_ in the data set.

![](https://i.imgur.com/3lvBLoA.png)

As we can see, the data with _outliers_ have a very different mean and standard deviation. In the first scenario, we will say that the mean is 5.45. But with _the outlier_, the mean soars to 30.

### How to Detect Outliers?

In this section, we are going to present the most commonly used techniques of _the outlier detection_, which are:

1. Statistical tests
2. Distance-based approaches
3. Density-based approaches
4. Visualization

#### Statistical Tests

In this approach, we assume that normal data objects follow a (known) distribution and occur in a high probability region of this distribution.

_Outliers_, on the other hand, strongly deviate from this distribution.

There are a couple of rules of thumb that we can use to remove _the outliers_:

- Any value which is beyond the range of `-1.5 x IQR` to `1.5 x IQR` (Interquartile Range - difference between 75th and 25th percentile)
- Any value which is out of the range of 5th and 95th percentile.
- Any value which is 3 or more standard deviations away from the mean.

**BUT**, there are two main problems with this approach:

1. We need to fit data to one of the known distributions.
2. The mean, standard deviation, and IQR are affected by _the outliers_ we are trying to remove.

#### Distance-based Approaches

The general idea is to judge a point based on the distance(s) to its neighbours. We assume that normal data objects have a dense neighbourhood.

_Outliers_, on the other hand, are far apart from their neighbours, i.e., have a less dense neighbourhood.

The most popular distance-based algorithm is `kNN (k nearest neighbours)`. It simply computes the distances between observations and compares them.

![](https://i.imgur.com/JJTDy0W.png)

It computes the distance to **the nearest** neighbour of a point `X` and compares it with the same distance for **k nearest** neighbours. If the distance is significantly higher we consider point `X` as _an outlier_.

For example, the closest point to `O3` in the image above is probably the point on the bottom right corner of `C2`. If we consider this point, the distances between it and its neighbors (the other points at the corner of `C2`) are much smaller than the distance to `O3`, so `O3` is an outlier! Selecting how many `k` neightbors to consider is an important consideration for tuning the sensitivity of this algorithm.

Note

The kNN algorithm is closer to a machine learning concept but if you are interested in the details of the process, you can take a look at the following resources:

- [k-NN (k-Nearest Neighbor): Overview, Simple Example by Statistics How to](https://www.statisticshowto.com/k-nn-k-nearest-neighbor/)
    
- [Outlier detection algorithm based on k-nearest neighbors-local outlier factor](https://journals.sagepub.com/doi/full/10.1177/17483026221078111)
    

#### (STRETCH) Density-Based Approaches

In density-based approaches, we assume that the density around a normal data object is similar to the density around its neighbours.

_Outliers_, on the other hand, have a considerably different density than their neighbours.

The most common density-based technique is `LOF (Local Outlier Factor)`. You can read more about how it works in the PDF copy of this Towards Data Science article [Local Outlier Factor for Anomaly Detection](https://drive.google.com/file/d/16U-WhGoAtSQjgY2Ua0MV6txFUfvEvTXQ/view?usp=drive_link).

#### Visualization

We can also identify _outliers_ visually. Depending on the type of _the outliers_ we are looking for we can use different graph types to identify _outliers_.

For univariate analysis: - A boxPlot

![](https://i.imgur.com/tkbljxs.png)

- A histogram

![](https://i.imgur.com/Yn0BZv9.png)

For multivariate analysis:

- A scatterPlot

![](https://i.imgur.com/fXuKB8v.png)