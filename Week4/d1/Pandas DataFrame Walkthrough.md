## Pandas DataFrame

For this activity, we can continue in the notebook from the [previous activity](https://web.compass.lighthouselabs.ca/24a9d3d4-185f-4868-9ed1-c10fd4eb155b). If you decide to create a new one, don't forget to import the packages.

`DataFrame` is a 2-dimensional labeled data structure with columns of potentially different types. You can think of it like a spreadsheet or SQL table, or a `dictionary` of `Series` objects. It is generally the most commonly used Pandas object. Like `Series`, `DataFrame` accepts many different kinds of input:

- dictionary of 1D ndarrays, lists, dictionaries, or Series
- 2D NumPy nd.array
- Series
- DataFrame

#### From Dictionary of Series or Dictionaries

The resulting index will be the union of the indexes of the various Series.

```python
In [37]: d = {'one': pd.Series([1., 2., 3.], index=['a', 'b', 'c']),
         'two': pd.Series([1., 2., 3., 4.], index=['a', 'b', 'c', 'd'])} 

In [38]: df = pd.DataFrame(d)

In [39]: df
Out[39]: 
   one  two
a  1.0  1.0
b  2.0  2.0
c  3.0  3.0
d  NaN  4.0

In [40]: pd.DataFrame(d, index=['d', 'b', 'a'])
Out[40]: 
   one  two
d  NaN  4.0
b  2.0  2.0
a  1.0  1.0

In [41]: pd.DataFrame(d, index=['d', 'b', 'a'], columns=['two', 'three'])
Out[41]: 
   two three
d  4.0   NaN
b  2.0   NaN
a  1.0   NaN
```

When data is a `dictionary`, and a `columns` is not passed, the DataFrame columns will be ordered by the `dictionary’s` insertion order. There is no sorting if you have Python version >= 3.6 and Pandas version >= 0.23.

Warning

If you pass an index and/or columns, you are guaranteeing the index and/or columns of the resulting DataFrame. Thus, a `dictionary` of Series plus a specific index and/or columns will discard all data not matching to the passed index and/or columns. See the last example above with an empty column labeled `three`.

#### From Dictionary of ndarrays or lists

The `ndarrays` must all be of the same length. If an index is passed, it **must** also be of the same length as the arrays. If no index is passed, the result will be `range(n)`, where n is the array length.

```python
In [44]: d = {'one': [1., 2., 3., 4.],
         'two': [4., 3., 2., 1.]}


In [45]: pd.DataFrame(d)
Out[45]: 
   one  two
0  1.0  4.0
1  2.0  3.0
2  3.0  2.0
3  4.0  1.0

In [46]: pd.DataFrame(d, index=['a', 'b', 'c', 'd'])
Out[46]: 
   one  two
a  1.0  4.0
b  2.0  3.0
c  3.0  2.0
d  4.0  1.0
```

#### From a Series

The result will be a `DataFrame` with the same index as the input `Series`, and with one column whose name is the original name of the `Series` (only if no other column name is provided).

```python
in [57]: pd.DataFrame(pd.Series(np.random.randn(5), name='something'))
```

### Column selection, addition, deletion

You can treat a `DataFrame` semantically like a dictionary of like-indexed `Series` objects. Getting, setting, and deleting columns works with the same syntax as the analogous dictionary operations:

```python
In [61]: df['one']
Out[61]: 
a    1.0
b    2.0
c    3.0
d    NaN
Name: one, dtype: float64

In [62]: df['three'] = df['one'] * df['two']

In [63]: df['flag'] = df['one'] > 2

In [64]: df
Out[64]: 
   one  two  three   flag
a  1.0  1.0    1.0  False
b  2.0  2.0    4.0  False
c  3.0  3.0    9.0   True
d  NaN  4.0    NaN  False
```

Columns can be deleted like with a dictionary:

```python
In [65]: del df['two']
```

When inserting a scalar value, it will naturally be propagated to fill the column:

```python
In [68]: df['foo'] = 'bar'

In [69]: df
Out[69]: 
   one  three   flag  foo
a  1.0    1.0  False  bar
b  2.0    4.0  False  bar
c  3.0    9.0   True  bar
d  NaN    NaN  False  bar
```

When inserting a `Series` that does not have the same index as the `DataFrame`, it will be conformed to the `DataFrame’s` index.

```python
In [70]: df['one_trunc'] = df['one'][:2]

In [71]: df
Out[71]: 
   one   flag  foo  one_trunc
a  1.0  False  bar        1.0
b  2.0  False  bar        2.0
c  3.0   True  bar        NaN
d  NaN  False  bar        NaN
```

Operations with scalars are just as you would expect:

```python
In [91]: df = pd.DataFrame(np.random.randn(8, 3), index=range(8), columns=list('ABC'))

In [92]: df * 5 + 2
Out[92]: 
                   A         B         C
2000-01-01 -4.134126  5.849018 -4.406237
2000-01-02 -1.638535  1.393469  1.510587
2000-01-03  5.478873  3.708672  6.798628
2000-01-04 -3.551681 -1.099880  2.748742
2000-01-05 -1.661697  5.438692  2.882222
2000-01-06  4.016548  1.225246  3.508122
2000-01-07 -8.899303 -4.849247 -2.771039
2000-01-08  9.313480 -6.715805 -2.132955

In [93]: 1 / df
Out[93]: 
                   A         B          C
2000-01-01 -0.815112  1.299033  -0.780489
2000-01-02 -1.374179 -8.243600 -10.216313
2000-01-03  1.437247  2.926250   1.041965
2000-01-04 -0.900628 -1.612966   6.677871
2000-01-05 -1.365487  1.454041   5.667510
2000-01-06  2.479485 -6.453662   3.315381
2000-01-07 -0.458745 -0.730007  -1.047990
2000-01-08  0.683669 -0.573671  -1.209788

In [94]: df ** 4
Out[94]: 
                    A         B         C
2000-01-01   2.265327  0.351172  2.694833
2000-01-02   0.280431  0.000217  0.000092
2000-01-03   0.234355  0.013638  0.848376
2000-01-04   1.519910  0.147740  0.000503
2000-01-05   0.287640  0.223714  0.000969
2000-01-06   0.026458  0.000576  0.008277
2000-01-07  22.579530  3.521204  0.829033
2000-01-08   4.577374  9.233151  0.466834
```

Boolean operators are vectorized as well:

```python
In [95]: df1 = pd.DataFrame({'a': [1, 0, 1], 'b': [0, 1, 1]}, dtype=bool)

In [96]: df2 = pd.DataFrame({'a': [0, 1, 1], 'b': [1, 1, 0]}, dtype=bool)

In [97]: df1 & df2
Out[97]: 
       a      b
0  False  False
1  False   True
2   True  False

In [98]: df1 | df2
Out[98]: 
      a     b
0  True  True
1  True  True
2  True  True

In [99]: df1 ^ df2
Out[99]: 
       a      b
0   True   True
1   True  False
2  False   True

In [100]: -df1
Out[100]: 
       a      b
0  False   True
1   True  False
2  False  False
```

Note

Quick reminer of boolean operators: `&` is `AND` - True when both are True. `|` is `OR` - True when at least one is True. `^` is `XOR` - True when exactly one is True (not both or neither)