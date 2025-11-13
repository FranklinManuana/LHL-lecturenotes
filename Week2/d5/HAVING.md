The `HAVING` clause is an extension of the `WHERE` clause in SQL, and is used to filter the results of an aggregate query. It allows you to specify a condition that must be met by the result set after the aggregation has taken place.

Note

The `HAVING` clause is typically used in conjunction with the `GROUP BY` clause, which groups rows together based on the values in one or more columns. The aggregate functions are then applied to each group to produce a summary of the data.

To learn more about “HAVING” clause in SQL you can watch the following video:

### Conclusion

The HAVING clause in SQL is used if we need to filter the result set based on aggregate functions such as `MIN()`, `MAX()`, `SUM()`, `AVG()`, and `COUNT()`. The `WHERE` clause places conditions on the selected columns, whereas the `HAVING` clause places conditions on groups created by the `GROUP BY` clause.