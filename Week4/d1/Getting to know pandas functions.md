Below is a collection of some specific Pandas functions and attributes that you should become familiar with.

### pd.read_csv()

The `read_csv` function is simple way to read csv (comma separated values) files, which is a commonly used file format for storing data.

### df.head()

The `head()` method returns the first n rows. If no parameter is specified, the number of rows defaults to 5.

```df
df.head(10)
```

### df.describe()

The `describe()` method generates descriptive statistics.

### astype()

The `astype()` method is used to cast a Pandas object to a particular data type. It can be a very helpful function in case your data is not stored in the correct format (data type). For instance, if floating point numbers have somehow been misinterpreted by Python as strings, you can convert them back to floating point numbers with `astype()`.

### to_datetime()

The `to_datetime()` function converts a Python object to datetime format. It can take an integer, floating point number, list, Pandas Series, or Pandas DataFrame as the argument.

### value_counts()

The `value_counts()` method returns a Pandas Series containing the count of unique values. Consider a dataset that contains customer information of 5,000 customers of a company. `value_counts()` will help us in identifying the number of occurrences of each unique value (customer) in a Series. It can be applied to columns containing data like province, the industry of employment, or the age of the customer.

### drop_duplicates()

The `drop_duplicates()` method returns a Pandas DataFrame with duplicate rows removed. There is also an option to keep the first occurrence (record) of the duplicate or the last. You can also specify the `inplace` and `ignore_index` attribute. `df.drop_duplicates(keep='last', inplace=True)`

### groupby()

The `groupby()` method is used to group a Pandas DataFrame by 1 or more columns, and perform some mathematical operation on it. `groupby()` can be used to summarize data in a simple manner, and you will use it very often in your career.

### fillna()

The `fillna()` method helps to replace all NaN values in a DataFrame or Series by imputing these missing values with more appropriate values.

### merge()

The `merge()` method is used to merge two Pandas DataFrame objects or a DataFrame and a Series object on a common column (field). It performs similar task as JOIN in SQL, and it returns the merged DataFrame.

### sort_values()

The `sort_values()` method is used to sort columns in a Pandas DataFrame (or a Pandas Series) by values in ascending or descending order. By specifying the `inplace` argument as `True`, you can make change it directly in the original DataFrame.

### Selecting data

Object selection has had a number of user-requested additions in order to support more explicit location based indexing. Pandas now supports three types of multi-axis indexing.

`.loc` is primarily label based, but may also be used with a boolean array. `.loc` will raise KeyError when the items are not found `.iloc` is primarily integer position based (from 0 to length-1 of the axis), but may also be used with a boolean array. `.iloc` will raise IndexError if a requested indexer is out-of-bounds, except slice indexers which allow out-of-bounds indexing. (this conforms with Python/NumPy slice semantics).

Read more about selecting data in Pandas in [this resource provided by Pandas.org](https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html)

## Conclusion

The functions mentioned above are a small sample of Pandas functions available for us to use. As you work on the various activities in this course and projects in your professional life, it will become more and more second nature for you to know which function to use and when. It might be a good idea to create a list of Pandas functions for your reference!