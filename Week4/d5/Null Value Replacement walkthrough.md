## Null Value Replacement

Let's go back to our _House Price Prediction Project_ data set to practice handling missing data.

We can continue in the same notebook as in the [Data Exploration activity](https://web.compass.lighthouselabs.ca/6603399c-6f1e-44e7-8163-75e126ac95c0).

As a first step, we will check whether we have some columns with missing values.

```python
# missing data
total = df_train.isnull().sum().sort_values(ascending=False)
percent = (df_train.isnull().sum()/df_train.isnull().count()).sort_values(ascending=False)
missing_data = pd.concat([total, percent], axis=1, keys=['Total', 'Percent'])
missing_data.head(20)
```

We can see the results in the table below:

![](https://i.imgur.com/lGIwMyS.png)

There are a couple of columns, where most of the values are missing. We can get rid of these since they don't have any value for us.

```python
# drop 5 columns with the biggest ratio of null values
to_drop = missing_data.head(5).index.tolist()
df_train.drop(to_drop, axis=1, inplace=True)
```

Warning

Be careful when removing columns. Sometimes a column can give us some relevant information even if 50% of values are `Null`. It's always good to be cautious when removing columns.

We don't want to remove more than 5 columns because the rest don't have a lot of missing values.

Instruction

Let's check the data types of the columns with missing values.

```python
# extract the names of columns with missing values
cols_with_missing = missing_data[missing_data.Percent > 0].index.tolist()
# remove column names that are already removed from dataset
missing_cols = list(set(cols_with_missing) - set(to_drop))
# check the datatype
df_train.dtypes[missing_cols]
```

We can see that we have a few numeric variables and some with text inside. First, we will take a look at the numeric ones.

### Numeric Variables

We will create a separate column to keep the information whether the value was missing. This way, we will have this information available in this column after we replace the value in the original one.

```python
num_cols_with_missing = df_train.dtypes[missing_cols][df_train.dtypes[missing_cols] == 'float'].index.tolist()
# create new variable with the information that it was missing
for cl in num_cols_with_missing:
    df_train[cl + "_missing_ind"] = 0
    df_train.loc[df_train[cl].isnull(), cl + "_missing_ind"] = 1
```

Now we can work on the `Null value replacement`.

```python
df_train["LotFrontage"] = df_train["LotFrontage"].fillna(df_train["LotFrontage"].mean())
df_train["GarageYrBlt"] = df_train["GarageYrBlt"].fillna(df_train["GarageYrBlt"].min())
df_train["MasVnrArea"] = df_train["MasVnrArea"].fillna(0)
```

- `LotFrontage` – We replace the missing values with the mean.
- `GarageYrBlt` – If the house has a garage and the year is missing, we assume it's the same year the house was built.
- `MasVnrArea` – If the veneer area is missing, we assume it's 0.

### Object (String) Variables

Instruction

Find the variables with the `dtype == "object"` and having at least one missing value.

```python
# 2. for categorical variables:
df_train.dtypes[missing_cols][df_train.dtypes[missing_cols] == 'object']
cat_cols_with_missing = df_train.dtypes[missing_cols][df_train.dtypes[missing_cols] == 'object'].index.tolist()
```

With the help of the data documentation we have, we can figure out that the missing values in _`Garage`_, _`Fireplace`_ and _`Basement`_ variables mean no garage, no fireplace and no basement respectively. Therefore, we will replace the missing values with `"None"`.

```python
# GarageFinish : data description says NA means "no garage"
df_train["GarageFinish"] = df_train["GarageFinish"].fillna("None")
# GarageCond : data description says NA means "no garage"
df_train["GarageCond"] = df_train["GarageCond"].fillna("None")
# GarageQual : data description says NA means "no garage"
df_train["GarageQual"] = df_train["GarageQual"].fillna("None")
# GarageType : data description says NA means "no garage"
df_train["GarageType"] = df_train["GarageType"].fillna("None")

# FireplaceQu: data description says NA means "no fireplace"
df_train["FireplaceQu"] = df_train["FireplaceQu"].fillna("None")

# BsmtExposure : data description says NA means "no basement"
df_train["BsmtExposure"] = df_train["BsmtExposure"].fillna("None")
# BsmtFinType2 : data description says NA means "no basement"
df_train["BsmtFinType2"] = df_train["BsmtFinType2"].fillna("None")
# BsmtFinType1 : data description says NA means "no basement"
df_train["BsmtFinType1"] = df_train["BsmtFinType1"].fillna("None")
# BsmtCond : data description says NA means "no basement"
df_train["BsmtCond"] = df_train["BsmtCond"].fillna("None")
# BsmtQual : data description says NA means "no basement"
df_train["BsmtQual"] = df_train["BsmtQual"].fillna("None")
```

The information about `Electrical` is missing in the documentation. Since we are dealing with a categorical variable, we will create a new category for a missing value.

```python
df_train["Electrical"] = df_train["Electrical"].fillna("Empty")
```

Finally, we can run the missing values check once more to see if we have filled in all the data.

Instruction

Check if you have any missing values in the dataset.