Sometimes, pre-built Pandas functions are not enough, and therefore, it's important to know how to apply your own functions to Pandas objects. In this activity, we will learn how to apply built-in functions, as well as our own Python functions, to Pandas objects in an efficient way.

To apply your own library's functions, or another library’s functions to Pandas objects, you should be aware of the methods below. The appropriate method to use depends on whether your function expects to operate on an entire `DataFrame` or `Series`, or row- or column-wise.

- tablewise function application: `pipe()`
- row or column-wise function application: `apply()`

### Tablewise Function Application

`DataFrames` and `Series` can be passed into functions without any problems.

```python
In [138]: def extract_city_name(df):
   .....:     """
   .....:     Chicago, IL -> Chicago for city_name column
   .....:     """
   .....:     df['city_name'] = df['city_and_code'].str.split(",").str.get(0)
   .....:     return df

In [139]: def add_country_name(df, country_name=None):
   .....:     """
   .....:     Chicago -> Chicago-US for city_name column
   .....:     """
   .....:     col = 'city_name'
   .....:     df['city_and_country'] = df[col] + country_name
   .....:     return df

In [140]: df_p = pd.DataFrame({'city_and_code': ['Chicago, IL']})


In [141]: add_country_name(extract_city_name(df_p), country_name='US')
Out[141]: 
  city_and_code city_name city_and_country
0   Chicago, IL   Chicago        ChicagoUS
```

Pandas encourages us to use `pipe()` for the problem above, which is known as 'method chaining'. `pipe` makes it easy to use your own or another library’s functions in method chains, alongside Pandas’ methods. Compare the first approach with the following:

```python
In [142]: (df_p.pipe(extract_city_name)
         .pipe(add_country_name, country_name="US"))
Out[142]: 
  city_and_code city_name city_and_country
0   Chicago, IL   Chicago        ChicagoUS
```

### Row or Column-wise Function Application

Arbitrary functions can be applied along the axes of a `DataFrame` using the `apply()` method, which, like the descriptive statistics methods, takes an optional axis argument.

```python
In [18]: df = pd.DataFrame({
        'one': pd.Series(np.random.randn(3), index=['a', 'b', 'c']),
        'two': pd.Series(np.random.randn(4), index=['a', 'b', 'c', 'd']),
        'three': pd.Series(np.random.randn(3), index=['b', 'c', 'd'])})

# pre-build numpy function
In [146]: df.apply(np.mean)
Out[146]: 
one      0.811094
two      1.360588
three    0.187958
dtype: float64

# pre-build numpy function
In [147]: df.apply(np.mean, axis=1)
Out[147]: 
a    1.583749
b    0.734929
c    1.133683
d   -0.166914
dtype: float64

# own lambda function
In [148]: df.apply(lambda x: x.max() - x.min())
Out[148]: 
one      1.051928
two      1.632779
three    1.840607
dtype: float64

# pre-build numpy function
In [149]: df.apply(np.cumsum)
Out[149]: 
        one       two     three
a  1.394981  1.772517       NaN
b  1.738035  3.684640 -0.050390
c  2.433281  5.163008  1.177045
d       NaN  5.442353  0.563873

# pre-build numpy function
In [150]: df.apply(np.exp)
Out[150]: 
        one       two     three
a  4.034899  5.885648       NaN
b  1.409244  6.767440  0.950858
c  2.004201  4.385785  3.412466
d       NaN  1.322262  0.541630
```

You can use `apply()` to apply your own function:

```python
def own_function(x):
    return x*x

In [150]: df.apply(own_function)
```

You may also pass additional arguments and keyword arguments to the `apply()` method. For instance, consider the following function you would like to apply:

```python
def subtract_and_divide(x, sub, divide=1):
    return (x - sub) / divide
```

You may then apply this function as follows:

```python
df.apply(subtract_and_divide, args=(5,3))
```

Warning

`args` has to be iterable. Therefore, even if you pass only 1 argument, you have to pass it as a tuple:

`args=(5,)`

```python
def subtract(x, sub):
    return (x - sub)

df.apply(subtract, args=(5,))
```