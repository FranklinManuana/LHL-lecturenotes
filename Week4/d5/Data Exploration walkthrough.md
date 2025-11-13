If you haven't already, you may need to install some of the following packages for this activity:

```python
conda install matplotlib seaborn
```

## Data Exploration

Let’s start practicing how to explore data. We will work with a dataset from a Kaggle competition: [**House Prices: Advanced Regression Techniques**](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/overview).

As usual, let's start with importing the right packages:

```python
import pandas as pd
import numpy as np

import matplotlib.pyplot as plt
import seaborn as sns
```

Instruction

Load the data into a Pandas dataframe called `df_train`. It can be found [**here**](https://drive.google.com/file/d/1rca0X0lIPey2xw60EBV6_DVJkmWp4afi/view?usp=sharing) and display the first five rows of the data.

Next, check how many variables and observations we're dealing with:

```python
print(df_train.shape)
```

Now, check the column names and their data types. We can do everything using one command we already know:

```python
df_train.dtypes
```

Let’s check if we have any duplicate ids in our data and remove them:

```python
# check for duplicates for Id
idsUnique = len(set(df_train.Id))
idsTotal = df_train.shape[0]
idsdupe = idsTotal - idsUnique
print(idsdupe)
# drop id col
df_train.drop(['Id'],axis =1,inplace=True)
```

We see that there are no duplicates, which is good, so we can continue.

### Exploring the Target Variable

The goal of this competition was to predict the price of a house. These values are stored in the variable `SalePrice`.

Let's check the descriptive statistics and the histogram:

```python
# descriptive statistics
df_train['SalePrice'].describe()
# histogram
sns.histplot(df_train['SalePrice'])
```

![](https://i.imgur.com/5GcMtnt.png)

In the graph above we can observe the following things: - It slightly deviates from a normal distribution. - It's skewed. - It has some outliers (i.e. really huge prices).

### Relationship Between the Target Variable and Predictors

Firstly, let's start with some common sense (or domain knowledge):

- Do we think about this variable when we are buying a house? (e.g. when we think about the house of our dreams, do we care about its 'Masonry veneer type'?).
- If so, how important would this variable be? (e.g. what is the impact of having 'Excellent' material on the exterior instead of 'Poor'? And of having 'Excellent' instead of 'Good'?).
- Is this information already described in any other variable? (e.g. if 'LandContour' gives the flatness of the property, do we really need to know the 'LandSlope'?).

We can print a list of all columns:

```python
sorted(list(df_train.columns))
```

Instruction

Let's go through the list above using the documentation and think about what could be useful.

We've done the exercise as well and came up with the following variables:

- OverallQual - a tricky variable, an interesting exercise would be to predict 'OverallQual' using all the other variables available
- YearBuilt
- Neighborhood
- TotalBsmtSF
- GrLivArea

Now, we are going to check the relationship of these variables with the target variable `SalePrice`. You can continue with our list or feel free to replicate the steps with your own list.

#### Numerical Variables

```python
# scatter plot grlivarea vs. SalePrice
var = 'GrLivArea'
data = df_train[['SalePrice',var]]
data.plot.scatter(x=var, y='SalePrice', ylim=(0,800000))
```

![](https://i.imgur.com/8bAv3ot.png)

We can see a linear relationship in the picture above.

```python
# scatter plot totalbsmtsf/saleprice
var = 'TotalBsmtSF'
data = df_train[['SalePrice',var]]
data.plot.scatter(x=var, y='SalePrice', ylim=(0,800000))
```

![](https://i.imgur.com/wgMDhq4.png)

Here, we can see a quadratic relationship.

#### Categorical Variables

```python
# overallqual
var = 'OverallQual'
data = df_train[['SalePrice',var]]
f, ax = plt.subplots(figsize=(8, 6))
fig = sns.boxplot(x=var, y="SalePrice", data=data)
fig.axis(ymin=0, ymax=800000)
```

![](https://i.imgur.com/xsyd62P.png)

```python
# Neighborhood
var = 'Neighborhood'
data = df_train[['SalePrice', var]]
plt.figure(figsize=(8, 6))
sns.boxplot(x=var, y="SalePrice", data=data)
plt.ylim(0, 800000)
plt.xticks(rotation=90)
plt.show()
```

![](https://i.imgur.com/ck8emwm.png)

```python
# YearBuilt
var = 'YearBuilt'
data = df_train[['SalePrice', var]]
plt.figure(figsize=(16, 8))
sns.boxplot(x=var, y="SalePrice", data=data)
plt.ylim(0, 800000)
plt.xticks(rotation=90)
plt.show()
```

![](https://i.imgur.com/7OF4Itn.png)

### Multivariate Analysis

Let's look at a correlation matrix between numeric attributes:

```python
# correlation matrix
corrmat = df_train.corr(numeric_only=True)
f, ax = plt.subplots(figsize=(12, 9))
sns.heatmap(corrmat, vmax=.8, square=True,cmap="RdYlGn_r")
```

![](https://i.imgur.com/lSSOl2q.png)

To make it more readable we can plot only those variables that correlate with the target variable more than `0.5`:

```python
# most correlated features with SalePrice
corrmat = df_train.corr(numeric_only=True)
top_corr_features = corrmat.index[abs(corrmat["SalePrice"])>0.5]
plt.figure(figsize=(10,10))
g = sns.heatmap(df_train[top_corr_features].corr(numeric_only=True),annot=True,cmap="RdYlGn_r")
```

![](https://i.imgur.com/oNU0ykS.png)

These are the variables most correlated with `SalePrice`. Our thoughts on this:

- _'OverallQual'_, _'GrLivArea'_ and _'TotalBsmtSF'_ are strongly correlated with **'SalePrice'**. Check!
- _'GarageCars'_ and _'GarageArea'_ are also among the most strongly correlated variables. The number of cars that fit into a garage is a consequence of the garage area. _'GarageCars'_ and _'GarageArea'_ are like twin brothers. You'll never be able to distinguish them. Therefore, we just need one of these variables in our analysis (we can keep _'GarageCars'_ since its correlation with **'SalePrice'** is higher).
- _'TotalBsmtSF'_ and _'1stFloor'_ also seem to be twin brothers. We can keep _'TotalBsmtSF'_ just to be able to say that our first guess was right :).
- _'FullBath'_ - the number of bathrooms in the house could certainly be correlated with sale price.
- _'TotRmsAbvGrd'_ and _'GrLivArea'_ – twin brothers again.
- _'YearBuilt'_: It seems that _'YearBuilt'_ is slightly correlated with **'SalePrice'**. Therefore, we could also look at the problem as `time-series analysis` but we will get into that later.

Note

We will continue with the tutorial in the [Outlier Detection](https://web.compass.lighthouselabs.ca/41c6950b-b2c2-4a42-93aa-0c44ff8e2c15) activity.