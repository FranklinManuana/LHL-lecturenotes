We will continue with the practice of basic operations in Pandas. To extend what we're already learned, we'll cover:

- Boolean comparisons
- Objects comparison
- Descriptive statistics
- Iterations

Instruction

Start your Notebook and import required libraries:

```python
In [1]: import numpy as np
In [2]: import pandas as pd
```

### Boolean Comparisons

`Series` and `DataFrame` have the binary comparison methods `eq`, `ne`, `le`, `lt`, `ge`, and `gt` whose behavior is vectorized:

- eq (equivalent to ==) — equals to
- ne (equivalent to !=) — not equals to
- le (equivalent to <=) — less than or equals to
- lt (equivalent to <) — less than
- ge (equivalent to >=) — greater than or equals to
- gt (equivalent to >) — greater than

```python
In [18]: df = pd.DataFrame({
        'one': pd.Series(np.random.randn(3), index=['a', 'b', 'c']),
        'two': pd.Series(np.random.randn(4), index=['a', 'b', 'c', 'd']),
        'three': pd.Series(np.random.randn(3), index=['b', 'c', 'd'])})

In [19]: df2 = df.copy()
In [46]: df.gt(df2)
Out[46]: 
     one    two  three
a  False  False  False
b  False  False  False
c  False  False  False
d  False  False  False

In [47]: df2.ne(df)
Out[47]: 
     one    two  three
a  False  False   True
b  False  False  False
c  False  False  False
d   True  False  False
```

Warning

`np.nan` == `np.nan` returns `False`.

You can apply the reductions: `empty`, `any()`, `all()`, and `bool()` to provide a way to summarize a boolean result.

```python
In [48]: (df > 0).all()
Out[48]: 
one      False
two       True
three    False
dtype: bool

In [49]: (df > 0).any()
Out[49]: 
one      True
two      True
three    True
dtype: bool

In [50]: (df > 0).any().any()
Out[50]: True
```

Warning

You might be tempted to do the following:

```python
if df:
  pass
```

or

```python
df and df2
```

These will both produce errors as you are trying to compare multiple values.

To evaluate single-element pandas objects in a boolean context, use the method `bool()`:

```python
In [53]: pd.Series([True]).bool()
Out[53]: True

In [54]: pd.Series([False]).bool()
Out[54]: False

In [55]: pd.DataFrame([[True]]).bool()
Out[55]: True

In [56]: pd.DataFrame([[False]]).bool()
Out[56]: False
```

### Objects comparison

You can conveniently perform element-wise comparisons when comparing a pandas data structure with a scalar value:

```python
In [65]: pd.Series(['foo', 'bar', 'baz']) == 'foo'
Out[65]: 
0     True
1    False
2    False
dtype: bool
```

Pandas also handles element-wise comparisons between different array-like objects of the same length:

```python
In [67]: pd.Series(['foo', 'bar', 'baz']) == pd.Index(['foo', 'bar', 'qux'])
Out[67]: 
0     True
1     True
2    False
dtype: bool
```

Warning

Trying to compare `Index` or `Series` objects of different lengths will create a `ValueError`:

```python
In [55]: pd.Series(['foo', 'bar', 'baz']) == pd.Series(['foo', 'bar'])
ValueError: Series lengths must match to compare
```

Often you may find that there is more than one way to compute the same result. For example, consider `df + df` and `df * 2`. To test that these two computations produce the same result, given the tools shown above, you might imagine using `(df + df == df * 2).all().all()`.

Instruction

Compare the two operations, `df + df` and `df * 2`, using the technique mentioned above.

The result is `False` but why is that? Let's dive deeper:

```python
In [58]: (df + df == df * 2).all()
Out[58]: 
one      False
two       True
three    False
dtype: bool

In [57]: df + df == df * 2
Out[57]: 
     one   two  three
a   True  True  False
b   True  True   True
c   True  True   True
d  False  True   True
```

This happens because of the problem mentioned above that

```python
In [59]: np.nan == np.nan
Out[59]: False
```

So, Pandas objects (such as `Series` and `DataFrames`) have an `equals()` method for testing equality, with NaNs in corresponding locations treated as equal.

```python
In [60]: (df + df).equals(df * 2)
Out[60]: True
```

Note

Note that the `Series` or `DataFrame` index needs to be in the same order for the equality to be `True`.

### Descriptive Statistics

There exists a large number of methods for computing descriptive statistics and other related operations on Series, DataFrame. All of them are vectorized. Most of them are aggregations and produce a lower-dimensional result.

Generally speaking, these methods take an axis as an argument and the axis can be specified by name or integer:

```python
# Aggregation for each column
In [78]: df.mean(0)
Out[78]: 
one      0.811094
two      1.360588
three    0.187958
dtype: float64

# Aggregation for each index
In [79]: df.mean(1)
Out[79]: 
a    1.583749
b    0.734929
c    1.133683
d   -0.166914
dtype: float64
```

By applying vectorized operations, we can describe various statistical procedures, like **standardization** (rendering data zero mean and standard deviation 1), very concisely:

```python
n [82]: ts_stand = (df - df.mean()) / df.std()

In [83]: ts_stand.std()
Out[83]: 
one      1.0
two      1.0
three    1.0
dtype: float64
```

In the picture below, we can find a list of the most popular descriptive statistics in Pandas.

![](https://i.imgur.com/ZDOek2T.png)

#### Describe

There is a convenient `describe()` function which computes a variety of summary statistics about a `Series` or the columns of a `DataFrame`:

```python
In [93]: series = pd.Series(np.random.randn(1000))

In [94]: series[::2] = np.nan

In [95]: series.describe()
Out[95]: 
count    500.000000
mean      -0.021292
std        1.015906
min       -2.683763
25%       -0.699070
50%       -0.069718
75%        0.714483
max        3.160915
dtype: float64

In [96]: frame = pd.DataFrame(np.random.randn(1000, 5),
   ....:                      columns=['a', 'b', 'c', 'd', 'e'])
   ....: 

In [97]: frame.iloc[::2] = np.nan

In [98]: frame.describe()
Out[98]: 
                a           b           c           d           e
count  500.000000  500.000000  500.000000  500.000000  500.000000
mean     0.033387    0.030045   -0.043719   -0.051686    0.005979
std      1.017152    0.978743    1.025270    1.015988    1.006695
min     -3.000951   -2.637901   -3.303099   -3.159200   -3.188821
25%     -0.647623   -0.576449   -0.712369   -0.691338   -0.691115
50%      0.047578   -0.021499   -0.023888   -0.032652   -0.025363
75%      0.729907    0.775880    0.618896    0.670047    0.649748
max      2.740139    2.752332    3.004229    2.728702    3.240991
```

For a non-numerical Series object, `describe()` will give a simple summary of the number of unique values and the most frequently occurring values:

```python
In [100]: s = pd.Series(['a', 'a', 'b', 'b', 'a', 'a', np.nan, 'c', 'd', 'a'])

In [101]: s.describe()
Out[101]: 
count     9
unique    4
top       a
freq      5
dtype: object
```

#### Index of Min/Max Values

The `idxmin()` and `idxmax()` functions on `Series` and `DataFrame` compute the index labels with the minimum and maximum corresponding values:

```python
In [107]: s1 = pd.Series(np.random.randn(5))

In [108]: s1
Out[108]: 
0    1.118076
1   -0.352051
2   -1.242883
3   -1.277155
4   -0.641184
dtype: float64

In [109]: s1.idxmin(), s1.idxmax()
Out[109]: (3, 0)

In [110]: df1 = pd.DataFrame(np.random.randn(5, 3), columns=['A', 'B', 'C'])

In [111]: df1
Out[111]: 
          A         B         C
0 -0.327863 -0.946180 -0.137570
1 -0.186235 -0.257213 -0.486567
2 -0.507027 -0.871259 -0.111110
3  2.000339 -2.430505  0.089759
4 -0.321434 -0.033695  0.096271

In [112]: df1.idxmin(axis=0)
Out[112]: 
A    2
B    3
C    1
dtype: int64

In [113]: df1.idxmax(axis=1)
Out[113]: 
0    C
1    A
2    C
3    A
4    C
dtype: object
```

### Iterations

The behaviour of basic iterations over pandas objects depends on the type. When iterating over a `Series`, it is regarded as array-like, and basic iterations produces the values. `DataFrames` follow the dict-like convention of iterating over the `keys` of the objects.

In short, basic iteration (for i in object) produces:

- Series: values
- DataFrame: column labels

```python
In [250]: df = pd.DataFrame({'col1': np.random.randn(3),
                     'col2': np.random.randn(3)}, index=['a', 'b', 'c'])

In [251]: for col in df:
        print(col)
col1
col2
```

To iterate over the rows of a `DataFrame`, you can use the following methods:

- `items()`: to iterate over the `(key, value)` pairs.
- `iterrows()`: Iterate over the rows of a DataFrame as (index, Series) pairs. This converts the rows to Series objects, which can change the dtypes and has some performance implications.
- `itertuples()`: Iterate over the rows of a DataFrame as namedtuples of the values. This is a lot faster than iterrows() and is in most cases preferable to use to iterate over the values of a DataFrame.

Warning

Iterating through Pandas objects is generally slow. In many cases, iterating manually over the rows is not needed and can be avoided.

#### Warning

You should never modify something you are iterating over. This is not guaranteed to work in all cases.

#### items

Consistent with the dict-like interface, `items()` iterates through key-value pairs:

- Series: (index, scalar value) pairs
- DataFrame: (column, Series) pairs

For example:

```python
In [252]: df = pd.DataFrame({'a': [1, 2, 3], 'b': ['a', 'b', 'c']})

In [255]: for label, ser in df.items():
        print(label)
        print(ser) 
a
0    1
1    2
2    3
Name: a, dtype: int64
b
0    a
1    b
2    c
Name: b, dtype: object

```

#### iterrows

`iterrows()` allows you to iterate through the rows of a DataFrame as Series objects. It returns an iterator yielding each index value along with a Series containing the data in each row:

```python
In [256]: for row_index, row in df.iterrows():
        print(row_index, row, sep='\n')

0
a    1
b    a
Name: 0, dtype: object
1
a    2
b    b
Name: 1, dtype: object
2
a    3
b    c
Name: 2, dtype: object
```

#### itertuple

The `itertuples()` method will return an iterator yielding a namedtuple for each row in the DataFrame. The first element of the tuple will be the row’s corresponding index value, while the remaining values are the row values.

For example:

```python
In [268]: for row in df.itertuples():
        print(row)

Pandas(Index=0, a=1, b='a')
Pandas(Index=1, a=2, b='b')
Pandas(Index=2, a=3, b='c')
```