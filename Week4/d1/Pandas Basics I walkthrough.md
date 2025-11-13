We will start with the practice of basic operations in Pandas. It is very important to get familiar with this stuff because we will be using it again and again throughout this course.

We will cover an introduction to Pandas, specifically:

- Attributes of Pandas objects
- Counting values in Series
- Altering labels
- `.dt` and `.str` accessors
- Sorting

One of the great things about the frequently used Python packages is that their documentation is really good. We can usually easily google anything we want to do in Pandas. We will also be working intensively with the official documentation throughout this course.

We can continue in the notebook from the [previous activity](https://web.compass.lighthouselabs.ca/fb5a114a-9a8f-4d54-923e-db91bc936def). If you decide to create a new one, don't forget to import the packages.

### Attributes of Pandas objects

`Pandas` objects have a number of attributes enabling us to access metadata:

- Shape: gives the axis dimensions of the object, consistent with ndarray
    
- Axis labels:
    
    - Series: index (only axis)
    - DataFrame: index (rows) and columns

Note

These attributes can be safely assigned to!

```python
In [3]: df = pd.DataFrame(np.random.randn(8, 3), index=range(8),
                      columns=['A', 'B', 'C'])

In [8]: df.columns = [x.lower() for x in df.columns]
In [9]: df
```

We can think of the `Pandas` objects (`Index`, `Series`, `DataFrame`) as containers for arrays, which hold the actual data and do the actual computation. To get the actual data inside an `Index` or `Series`, use the attribute `.array`.

```python
In [10]: df['a'].array
```

The full list of the attributes that are available for each data type can be found in the documentation: - [**Series**](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html) - [**DataFrames**](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)

### Counting values in Series

The `value_counts()` Series method and top-level function computes a histogram of a 1D array of values.

```python
In [117]: data = np.random.randint(0, 7, size=50)

In [118]: data
Out[118]: 
array([6, 6, 2, 3, 5, 3, 2, 5, 4, 5, 4, 3, 4, 5, 0, 2, 0, 4, 2, 0, 3, 2,
       2, 5, 6, 5, 3, 4, 6, 4, 3, 5, 6, 4, 3, 6, 2, 6, 6, 2, 3, 4, 2, 1,
       6, 2, 6, 1, 5, 4])

In [119]: s = pd.Series(data)

In [120]: s.value_counts()
Out[120]: 
6    10
2    10
4     9
5     8
3     8
0     3
1     2
dtype: int64
```

Similarly, we can get the most frequently occurring value(s) (`mode()`) of the values in a Series or DataFrame.

```python
In [122]: s5 = pd.Series([1, 1, 3, 3, 3, 5, 5, 7, 7, 7])

In [123]: s5.mode()
Out[123]: 
0    3
1    7
dtype: int64

In [124]: df5 = pd.DataFrame({"A": np.random.randint(0, 7, size=50),
   .....:                     "B": np.random.randint(-10, 15, size=50)})
   .....: 

In [125]: df5.mode()
Out[125]: 
     A   B
0  1.0  -9
1  NaN  10
2  NaN  13
```

Warning

Even though `mode()` can be called on both Series and DataFrame, `value_counts()` can only be used on 1D arrays, therefore, not on DataFrames.

### `.dt` and `.str` accessors

#### `.dt` accessor

`Series` has an accessor to succinctly return datetime-like properties for the values of the Series, if it is a datetime/period-like Series. This will return a Series, indexed like an existing Series.

```python
# datetime
In [269]: s = pd.Series(pd.date_range('20130101 09:10:12', periods=4))

In [270]: s
Out[270]: 
0   2013-01-01 09:10:12
1   2013-01-02 09:10:12
2   2013-01-03 09:10:12
3   2013-01-04 09:10:12
dtype: datetime64[ns]

In [271]: s.dt.hour
Out[271]: 
0    9
1    9
2    9
3    9
dtype: int64
```

Instruction

Extract the following values from Series `s`: 1. Seconds 2. Day 3. Day of week

```python
In [272]: s.dt.second
In [272]: s.dt.day
In [272]: s.dt.dayofweek
```

We can easily produce timezone-aware transformations:

```python
In [275]: stz = s.dt.tz_localize('US/Eastern')

In [276]: stz
Out[276]: 
0   2013-01-01 09:10:12-05:00
1   2013-01-02 09:10:12-05:00
2   2013-01-03 09:10:12-05:00
3   2013-01-04 09:10:12-05:00
dtype: datetime64[ns, US/Eastern]

In [277]: stz.dt.tz
Out[277]: <DstTzInfo 'US/Eastern' LMT-1 day, 19:04:00 STD>
```

We can also chain these types of operations:

```python
In [278]: s.dt.tz_localize('UTC').dt.tz_convert('US/Eastern')
Out[278]: 
0   2013-01-01 04:10:12-05:00
1   2013-01-02 04:10:12-05:00
2   2013-01-03 04:10:12-05:00
3   2013-01-04 04:10:12-05:00
dtype: datetime64[ns, US/Eastern]
```

#### `.str` accessor

Series is equipped with **a set of string processing methods** that make it easy to operate on each element of the array. These are accessed via the Series’s `str` attribute and generally have names matching the equivalent (scalar) built-in string methods.

```python
In [294]: s = pd.Series(['A', 'B', 'C', 'Aaba', 'Baca', np.nan, 'CABA', 'dog', 'cat'],
                  dtype="string")

In [295]: s.str.lower()
Out[295]: 
0       a
1       b
2       c
3    aaba
4    baca
5    <NA>
6    caba
7     dog
8     cat
dtype: string
```

Note

Using `.str` accessor, we can apply all string functions from standard Python to our Series.

### Sorting

There are three types of sorting in Pandas: 1. Sorting by index labels 2. Sorting by column values 3. Sorting by a combination of both

#### By index

The `Series.sort_index()` and `DataFrame.sort_index()` methods are used to sort a Pandas object by its index levels.

```python
In [296]: df = pd.DataFrame({
        'one': pd.Series(np.random.randn(3), index=['a', 'b', 'c']),
        'two': pd.Series(np.random.randn(4), index=['a', 'b', 'c', 'd']),
        'three': pd.Series(np.random.randn(3), index=['b', 'c', 'd'])})

In [297]: unsorted_df = df.reindex(index=['a', 'd', 'c', 'b'],
                          columns=['three', 'two', 'one'])

In [298]: unsorted_df
Out[298]: 
      three       two       one
a       NaN -1.152244  0.562973
d -0.252916 -0.109597       NaN
c  1.273388 -0.167123  0.640382
b -0.098217  0.009797 -1.299504

# Sort DataFrame by index
In [299]: unsorted_df.sort_index()
Out[299]: 
      three       two       one
a       NaN -1.152244  0.562973
b -0.098217  0.009797 -1.299504
c  1.273388 -0.167123  0.640382
d -0.252916 -0.109597       NaN

# Sort DataFrame by index
In [300]: unsorted_df.sort_index(ascending=False)
Out[300]: 
      three       two       one
d -0.252916 -0.109597       NaN
c  1.273388 -0.167123  0.640382
b -0.098217  0.009797 -1.299504
a       NaN -1.152244  0.562973

# Sort DataFrame by column names
In [301]: unsorted_df.sort_index(axis=1)
Out[301]: 
        one     three       two
a  0.562973       NaN -1.152244
d       NaN -0.252916 -0.109597
c  0.640382  1.273388 -0.167123
b -1.299504 -0.098217  0.009797

# Sort Series by index
In [302]: unsorted_df['three'].sort_index()
Out[302]: 
a         NaN
b   -0.098217
c    1.273388
d   -0.252916
Name: three, dtype: float64
```

#### By values

The `Series.sort_values()` method is used to sort a Series by its values. The `DataFrame.sort_values()` method is used to sort a DataFrame by its column or row values.

```python
In [303]: df1 = pd.DataFrame({'one': [2, 1, 1, 1],
                        'two': [1, 3, 2, 4],
                        'three': [5, 4, 3, 2]})

# Sort DataFrame by column "two"
In [304]: df1.sort_values(by='two')
Out[304]: 
   one  two  three
0    2    1      5
2    1    2      3
1    1    3      4
3    1    4      2

# Sort DataFrame by columns "one" and "two"
In [305]: df1[['one', 'two', 'three']].sort_values(by=['one', 'two'])
Out[305]: 
   one  two  three
2    1    2      3
1    1    3      4
3    1    4      2
0    2    1      5
```

These methods have a special treatment of NA values via the na_position argument:

```python
In [306]: s[2] = np.nan

In [307]: s.sort_values()
Out[307]: 
0       A
3    Aaba
1       B
4    Baca
6    CABA
8     cat
7     dog
2    <NA>
5    <NA>
dtype: string

In [308]: s.sort_values(na_position='first')
Out[308]: 
2    <NA>
5    <NA>
0       A
3    Aaba
1       B
4    Baca
6    CABA
8     cat
7     dog
dtype: string
```

Note

`by` parameter in `sort_values()` method can refer to either columns or index level names.

We can use the name of the index to sort by both an index and a column.

```python
# Build MultiIndex
In [309]: idx = pd.MultiIndex.from_tuples([('a', 1), ('a', 2), ('a', 2),
                                   ('b', 2), ('b', 1), ('b', 1)])

In [310]: idx.names = ['first', 'second']

# Build DataFrame
In [311]: df_multi = pd.DataFrame({'A': np.arange(6, 0, -1)},
                            index=idx)

In [312]: df_multi
Out[312]: 
              A
first second   
a     1       6
      2       5
      2       4
b     2       3
      1       2
      1       1

# Sort DataFrame by 'second' (index) and 'A' (column)
In [313]: df_multi.sort_values(by=['second', 'A'])
Out[313]: 
              A
first second   
b     1       1
      1       2
a     1       6
b     2       3
a     2       4
      2       5
```