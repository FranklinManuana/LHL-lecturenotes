In this activity, we will learn what "stacking" means and what "pivot tables" are. These are very important Pandas tools that don't exist in the usual relational database management systems.

Note

We will continue using the same DataFrames as in the previous tutorial. Therefore you can continue in the same Notebook. If you decide to create a new one, don't forget to import the packages.

### Stack

The `stack()` method "compresses" a level in the DataFrame's columns. Let's give it a try.

Firstly, we are going to create the data frame to work with.

```python
In [91]: tuples = list(zip(*[['bar', 'bar', 'baz', 'baz',
                         'foo', 'foo', 'qux', 'qux'],
                        ['one', 'two', 'one', 'two',
                         'one', 'two', 'one', 'two']]))

In [92]: index = pd.MultiIndex.from_tuples(tuples, names=['first', 'second'])

In [93]: df = pd.DataFrame(np.random.randn(8, 2), index=index, columns=['A', 'B'])

In [94]: df2 = df[:4]
```

Now, we are going to use the `stack()` function to "compress" the columns into the index.

```python
In [96]: stacked = df2.stack()
In [97]: stacked
Out[97]: 
first  second   
bar    one     A   -0.727965
               B   -0.589346
       two     A    0.339969
               B   -0.693205
baz    one     A   -0.339355
               B    0.593616
       two     A    0.884345
               B    1.591431
dtype: float64
```

Instruction

Check the type of variable `stack` and think about why it has such a type.

With a "stacked" DataFrame or Series (having a MultiIndex as the index), the inverse operation of stack() is unstack(), which by default unstacks the **last level**:

```python
In [98]: stacked.unstack()
Out[98]: 
                     A         B
first second                    
bar   one    -0.727965 -0.589346
      two     0.339969 -0.693205
baz   one    -0.339355  0.593616
      two     0.884345  1.591431

In [99]: stacked.unstack(1)
Out[99]: 
second        one       two
first                      
bar   A -0.727965  0.339969
      B -0.589346 -0.693205
baz   A -0.339355  0.884345
      B  0.593616  1.591431

In [100]: stacked.unstack(0)
Out[100]: 
first          bar       baz
second                      
one    A -0.727965 -0.339355
       B -0.589346  0.593616
two    A  0.339969  0.884345
       B -0.693205  1.591431
```

### Pivot Tables

Once more, let's create the data that we'll work with:

```python
In [101]: df = pd.DataFrame({'A': ['one', 'one', 'two', 'three'] * 3,
                       'B': ['A', 'B', 'C'] * 4,
                       'C': ['foo', 'foo', 'foo', 'bar', 'bar', 'bar'] * 2,
                       'D': np.random.randn(12),
                       'E': np.random.randn(12)})
```

We can produce pivot tables from this data very easily:

```python
In [103]: pd.pivot_table(df, values='D', index=['A', 'B'], columns=['C'])
Out[103]: 
C             bar       foo
A     B                    
one   A  2.395985 -1.202872
      B  1.395433 -1.814470
      C -0.392670 -0.055224
three A -0.595447       NaN
      B       NaN  1.928123
      C  0.166599       NaN
two   A       NaN  0.007207
      B  1.552825       NaN
      C       NaN  1.018601
```

If you need more information about pivot tables there is a great explanation in [this guide](https://www.lumeer.io/pivot-table-complete-guide/).