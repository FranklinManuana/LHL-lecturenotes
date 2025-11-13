Sometimes you want to return a set of results that are the product of several queries. If you have the PKs and FKs, you can write a query with the appropriate joins to get there. However, in the absence of PKs and FKs to do the joins, you have to build the queries separately and put the results together. This operation can be done with the help of the `UNION` operator.

The `UNION` operator is used to combine the result set of two or more `SELECT` statements when the following are true:

- Every `SELECT` statement within `UNION` must have the same number of columns.
    
- The columns must also have similar data types.
    
- The columns in every `SELECT` statement must also be in the same order.
    

### Union and Union All

**UNION:** this command is used to select the tuples which have related information from two or more tables. It’s similar to `JOIN` command, but when you are using `UNION` command, the selected columns must be of the same data type. It **removes** all the **duplicate records** from the final result.

**UNION ALL:** this command is the same as `UNION` command; it just concatenates the records. Unlike `UNION`, `UNION ALL` pulls all the values from all the tables; it doesn’t eliminate duplicate records.

Instruction

Read more on the topic with this article [PostgreSQL UNION](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-union/).

## Conclusion

`UNION` operator combines the result sets from multiple queries into a single result set in the absence of PKs and FKs between tables. The `UNION` operator removes all duplicate rows from the combined data set.