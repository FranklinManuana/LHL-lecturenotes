

The **value transformation** in machine learning is another part of _data preparation_, consisting of transforming data into the right or more useful format for modeling and making predictions.

### Why do We Care?

In Machine Learning, we need data in a numeric format for modeling. Furthermore, some of the algorithms work best with normally distributed data.

Many statistical and machine learning algorithms assume that the data is normally distributed, or approximately normally distributed. This is because many algorithms have been developed and optimized under the assumption of a normal distribution. For example, linear regression models, which are widely used for predictive modeling, assume that the errors are normally distributed. The normal distribution has some desirable properties, such as the central limit theorem, which states that the sum of many independent and identically distributed random variables will converge to a normal distribution, even if the individual variables are not normally distributed.

When the data is normally distributed, it makes certain statistical assumptions easier to work with and can simplify the calculation of probabilities and statistical inferences. This can lead to more accurate and robust models. However, not all datasets are normally distributed, and even if a dataset is approximately normally distributed, there can still be significant outliers or skewness that can affect the performance of algorithms that assume normality. In these cases, transforming the data or using algorithms that are robust to non-normal distributions may be necessary.

Therefore, during _the data preparation phase_, we need to apply various _transformations_ to improve our data quality and maximize the quality of the results. For this, we have again a couple of options, depending on the type of variable we are dealing with.

Some of the common basic transformations include:

- Scaling: Rescaling the data to a common range, such as between 0 and 1 or between -1 and 1.
- Normalization: Adjusting the data so that it has a mean of 0 and a standard deviation of 1.
- Logarithmic transformation: Applying a logarithmic function to the data to reduce the impact of extreme values or skewness.
- Encoding: Converting categorical variables into numerical representations, such as one-hot encoding.

Other transformations include:

- Binning
- Dummy variables

#### Basic Transformations

We can see an example of a logarithmic transformation in the charts below, which are showing the relationship between the size of a brain and the size of a body for animals.

![Logarithmic transformation charts. First chart shows body relative to brain and second shows log(body) to Log(brain) size in animals, depicting a logarithmic relationship that as body size increases, so does brain size logarithmically.](https://i.imgur.com/eGKvRlX.png)

We can see that the relationship between these two variables is much clearer when _a logarithmic transformation_ is applied.

We can always test more of these transformations (logarithmic, exponential, quadratic) and combine them with the hypothesis tests or scatter plots to see what gives us the best relationship.

#### Binning

Binning as a process is very important for a couple of use cases:

- Decision trees (mentioned in the video)
- The interpretability of regression algorithms - which will be covered in more detail later.

Instruction

We will learn about _binning_ from the following video: 

This process is very important for a couple of use cases:

- Decision trees (mentioned in the video)
- The interpretability of regression algorithms - we will learn more about it later.

#### Scaling

Scaling in data science refers to the process of transforming the values of numerical variables so that they have the same scale. This is an important step in many data science pipelines, particularly in the preprocessing phase before building machine learning models. Scaling is necessary because many machine learning algorithms are sensitive to the scale of the input features and perform better when the features have the same scale.

The scaling process is also **very important** for a couple of additional use cases:

- Interpretability of regression algorithms
- Unsupervised learning

Instruction

Follow this short, but straight-to-the-point article to learn [**How, When, and Why Should You Normalize / Standardize / Rescale Your Data?**](https://towardsai.net/p/data-science/how-when-and-why-should-you-normalize-standardize-rescale-your-data-3f083def38ff).

#### Dummy Variables

In the context of machine learning, dummy variables (also known as indicator variables) are binary variables used to represent categorical variables. Categorical variables are variables that can take on one of a limited number of values, such as "Employed" or "Unemployed"

Since most machine learning algorithms work with numerical data, categorical variables must be transformed into numerical variables in order to be included in the model. One approach to doing this is to create a set of binary variables, each representing one of the possible categories. Each observation is then given a value of 1 for the category it belongs to and 0 for all other categories.

For example, if the categorical variable is "Employment Status" with two possible values "Employed" and "Unemployed", two dummy variables can be created: "status-employed" and "status-unemployed". An observation with the value "Employed" would be given a value of 1 for "status-employed" and a value of 0 for "status-unemployed", while an observation with the value "Unemployed" would be given a value of 1 for "status-unemployed" and a value of 0 for "status-employed".

Using dummy variables allows the categorical information to be included in the model in a form that can be understood by the machine learning algorithm.

Instruction

First, check this statistic dictionary entry to learn what [**a dummy variable**](https://stattrek.com/statistics/dictionary.aspx?definition=dummy-variable) is.

The process of _creating dummy variables_ refers to the transformation of categorical variables into variables with `0s` and `1s` only.

|ID|Employment Status|status-employed|status-unemployed|
|---|---|---|---|
|A001|Employed|1|0|
|A002|Unemployed|0|1|
|A003|Unemployed|0|1|
|A004|Employed|1|0|
|A005|Unemployed|0|1|
|A006|Employed|1|0|
|A007|Employed|1|0|

We can see the example in the table above, we have created two binary variables from the variable `Employment Status`.

Instruction

Do we need both variables `status-employed` and `status-unemployed`?