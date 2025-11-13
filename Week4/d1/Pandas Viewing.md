In this activity, we will practice how to explore data in Pandas. This is a very important part of any data analysis.

Instruction

Start your Notebook and import required libraries:

```python
In [1]: import numpy as np
In [2]: import pandas as pd
```

### Object Creation

Instruction

Create a Series by passing a list of values with default integer index

```python
In [3]: s = pd.Series([1, 3, 5, np.nan, 6, 8])

In [4]: s
Out[4]: 
0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64
```

Instruction

Create a DataFrame by passing a Numpy array with a datetime index and labeled columns.

```python
In [5]: dates = pd.date_range('20130101', periods=6)

In [6]: dates
Out[6]: 
DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04', '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')

In [7]: df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list('ABCD'))

In [8]: df
```

Instruction

Create a DataFrame from a dict of objects

````python
In [9]: df2 = pd.DataFrame({'A': 1.0,
                        'B': pd.Timestamp('20130102'),
                        'C': pd.Series(1, index=list(range(4)), dtype='float32'),
                        'D': np.array([3] * 4, dtype='int32'),
                        'E': pd.Categorical(["test", "train", "test", "train"]),
                        'F': 'foo'})

In [10]: df2

The columns of the resulting DataFrame have different dtypes.

```python
In [11]: df2.dtypes
Out[11]: 
A           float64
B    datetime64[ns]
C           float32
D             int32
E          category
F            object
dtype: object
````

In Jupyter, `tab` completion for column names (as well as public attributes) is automatically enabled. Here’s a subset of the attributes that can be completed:

```python
In [12]: df2.<TAB>  # noqa: E225, E999
df2.A                  df2.bool
df2.abs                df2.boxplot
df2.add                df2.C
df2.add_prefix         df2.clip
df2.add_suffix         df2.clip_lower
df2.align              df2.clip_upper
df2.all                df2.columns
df2.any                df2.combine
df2.append             df2.combine_first
df2.apply              df2.consolidate
df2.applymap
df2.D
```

Warning

The list above is only **subset** of what is possible to do on top of the DataFrame

### Viewing Data

Here is how to view the top and bottom rows of the frame:

```python
In [13]: df.head()
Out[13]: 
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401

In [14]: df.tail(3)
Out[14]: 
                   A         B         C         D
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
2013-01-06 -0.673690  0.113648 -1.478427  0.524988
```

Instruction

Display the index and columns:

```python
In [15]: df.index
```

```python
In [16]: df.columns
```

Instruction

Convert DataFrame to numpy array.

```python
In [17]: df.to_numpy()
```

Warning

NumPy arrays have one dtype for the entire array, while Pandas DataFrames have one dtype per column. When you call DataFrame.to_numpy(), Pandas will find the NumPy dtype that can hold all of the dtypes in the DataFrame. This may end up being an object, which requires casting every value to a Python object. This can lead to very expensive (time and memory-consuming) operations.

The function `describe()` shows a quick statistic summary of your data.

```python
In [19]: df.describe()
Out[19]: 
              A         B         C         D
count  6.000000  6.000000  6.000000  6.000000
mean   0.073711 -0.431125 -0.687758 -0.233103
std    0.843157  0.922818  0.779887  0.973118
min   -0.861849 -2.104569 -1.509059 -1.135632
25%   -0.611510 -0.600794 -1.368714 -1.076610
50%    0.022070 -0.228039 -0.767252 -0.386188
75%    0.658444  0.041933 -0.034326  0.461706
max    1.212112  0.567020  0.276232  1.071804
```

Instruction

Tranpose your data

```python
 In [20]: df.T
```

and sort by column name

```python
In [21]: df.sort_index(axis=1, ascending=False)
```

We can also sort DataFrame by values in specific column.

```python
In [22]: df.sort_values(by='B')
Out[22]: 
                   A         B         C         D
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-06 -0.673690  0.113648 -1.478427  0.524988
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
```