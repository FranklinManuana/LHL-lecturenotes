It wouldn't be possible to do a lot with the data if we couldn't merge (join) it together. In this activity, we will practice how to do joins and grouping in Pandas as both are very important operations for efficient data preparation.

Note

You can continue with this activity in the same Notebook as we were using previously. If you decide to create a new one, don't forget to import the packages.

### Merge

`Pandas` provides various facilities for easily combining Series and DataFrame objects with various kinds of set logic for the indexes and relational algebra functionality in the case of join / merge-type operations.

Concatenating Pandas objects together with `concat()` (equivalent to `UNION` in `SQL`):

```python
In [73]: df = pd.DataFrame(np.random.randn(10, 4))

In [74]: df
Out[74]: 
          0         1         2         3
0 -0.548702  1.467327 -1.015962 -0.483075
1  1.637550 -1.217659 -0.291519 -1.745505
2 -0.263952  0.991460 -0.919069  0.266046
3 -0.709661  1.669052  1.037882 -1.705775
4 -0.919854 -0.042379  1.247642 -0.009920
5  0.290213  0.495767  0.362949  1.548106
6 -1.131345 -0.089329  0.337863 -0.945867
7 -0.932132  1.956030  0.017587 -0.016692
8 -0.575247  0.254161 -1.143704  0.215897
9  1.193555 -0.077118 -0.408530 -0.862495

# break it into pieces
In [75]: pieces = [df[:3], df[3:7], df[7:]]

In [76]: pd.concat(pieces)
Out[76]: 
          0         1         2         3
0 -0.548702  1.467327 -1.015962 -0.483075
1  1.637550 -1.217659 -0.291519 -1.745505
2 -0.263952  0.991460 -0.919069  0.266046
3 -0.709661  1.669052  1.037882 -1.705775
4 -0.919854 -0.042379  1.247642 -0.009920
5  0.290213  0.495767  0.362949  1.548106
6 -1.131345 -0.089329  0.337863 -0.945867
7 -0.932132  1.956030  0.017587 -0.016692
8 -0.575247  0.254161 -1.143704  0.215897
9  1.193555 -0.077118 -0.408530 -0.862495
```

Warning

DataFrame also has a method called `.append()`. But even though adding a column to a DataFrame is relatively fast, adding a row requires a copy, and may be expensive. It's faster to concatenate two data-frames than to append rows.

To join two data-frames, we use `merge()` in Pandas (equivalent to `JOIN` in `SQL`).

```python
In [82]: left = pd.DataFrame({'key': ['foo', 'bar'], 'lval': [1, 2]})
In [83]: right = pd.DataFrame({'key': ['foo', 'bar'], 'rval': [4, 5]})
```

Instruction

Make an inner join between tables created above on column `key`:

```python
pd.merge(left, right, on='key')
```

Note

Inner join is done automatically with `merge()`. If you want to do other types of joins like the outer, left or right, you should use the parameter, `how`.

```python
pd.merge(left, right, on='key', how='outer')
```

### Grouping

By `group by`, we are referring to a process involving the following steps:

- Splitting the data into groups based on some criteria
- Applying a function to each group independently
- Combining the results into a data structure

Let's create the DataFrame we will work on.

```python
In [87]: df = pd.DataFrame({'A': ['foo', 'bar', 'foo', 'bar',
                             'foo', 'bar', 'foo', 'foo'],
                        'B': ['one', 'one', 'two', 'three',
                          'two', 'two', 'one', 'three'],
                       'C': np.random.randn(8),
                       'D': np.random.randn(8)})
```

Instruction

Group the DataFrame by column `A` and sum the values of the other columns (`B`, `C`, `D`).

HINT: In SQL it would be following:

```sql
select A,
  STRING_AGG(B,'') as B,
  sum(C) as C,
  sum(D) as D
from df
group by A;
```

```python
In [89]: df.groupby('A').sum()
```

Note

You may have noticed that in the SQL equivalent, we used `STRING_AGG()` for the text column `B`, but didn't do anything differently for `B` in Python. Python and SQL handle 'adding' strings differently. In Python the default behaviour of summing two strings is concatenation (`'one' + 'two' = 'onetwo'`), which is equivalent to `STRING_AGG(column, '')` in SQL, with `''` indicating there should be nothing between each string. If you don't want this interaction in Python, remember that you can filter by data type to get numeric columns only: `df.groupby('A').sum().select_dtypes(include = [bool, float, int])`.

We can also group by multiple columns. This operation will create a new DataFrame with Multilevel Index.

```python
In [90]: df.groupby(['A', 'B']).sum()
Out[90]: 
                  C         D
A   B                        
bar one    1.511763  0.396823
    three -0.990582 -0.532532
    two    1.211526  1.208843
foo one    1.614581 -1.658537
    three  0.024580 -0.264610
    two    1.185429  1.348368
```

Warning

You cannot apply two different aggregation functions in 1 `groupby` statement in Pandas. However, there is an equivalent to

```sql
select A,
  sum(C) as C,
  max(D) as D
from df
group by A;
```

using the `.agg()` method.

```python
In [21]: df.groupby('A').agg({'C': 'sum', 'D': 'max'})
```