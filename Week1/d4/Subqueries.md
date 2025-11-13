A subquery is a query nested within a larger query, such as:

- Nested in the `SELECT` and/or `FROM` clauses
    
- Nested in the `WHERE` and/or `HAVING` clauses of a main query:
    
    - The operator used to evaluate the subquery depends on the number of rows the subquery gives as a result:
    - One row and one column: =, <>, !=, <, <=, >, >=
    - Multiple rows: IN, NOT IN

- From the syntax point of view, write the subquery within brackets i.e., ()

In DBMSs, it is important to understate the evaluation of the subquery which is as follows:

- The subquery is executed once and gives a result.
    
- The main query is executed using the result of the subquery.
    

Instruction

Read more on the topic with this article [PostgreSQL Subquery](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-subquery/).

### Subquery in the `SELECT` Clause

A subquery in the `SELECT` clause can only display a scalar value.

In the following query, compare the **total due by product by order** to the **average total due by product by order**.

```sql
SELECT orderid,
productid,
(unitprice * quantity) AS total_due,
(SELECT AVG(unitprice * quantity) FROM order_details) AS avg_total_due
FROM order_details
```

![select sub query](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/3.+Accessing+Data/select_sub_query.PNG)

### Subquery in the `FROM` Clause

A subquery in the `FROM` clause gives a virtual table. It is possible to write a query on this virtual table from the main query. A virtual table is a set of columns that have specific names and data types and that is used in a main query.

In the following query, the main query filters the virtual table on `orderid`.

```sql
SELECT *
FROM (
    SELECT orderid,
    productid,
    quantity
    FROM order_details
) AS virtual_table
WHERE orderid = 10250
```

![from sub query](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/3.+Accessing+Data/from_sub_query.PNG)

### Subquery in the `WHERE` Clause Example #1

A subquery in the `WHERE` clause can give a single row and a single column (i.e., a single value). It is possible to apply a comparison according to the type of data displayed.

In the following query, the two subqueries return the minimum and maximum order dates for `customerid` = 'AROUT'. The main query returns all orders of all customers between these two dates.

```sql
SELECT *
FROM orders
WHERE orderdate BETWEEN 
    (SELECT MIN(orderdate)
    FROM orders
    WHERE customerid = 'AROUT')
AND
    (SELECT MAX(orderdate)
    FROM orders
    WHERE customerid = 'AROUT')
```

![where sub query](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/3.+Accessing+Data/where_sub_query_1.PNG)

### Subquery in the `WHERE` Clause Example #2

A subquery in the `WHERE` clause can give several rows and a single column (i.e., several values). It is possible to apply: IN, NOT IN

```sql
SELECT *
FROM customers
WHERE customerid NOT IN (SELECT DISTINCT(customerid) FROM orders)
```

![where sub query](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/3.+Accessing+Data/where_sub_query_2.PNG)

### Subquery in the `HAVING` Clause Example #1

A subquery in the `HAVING` clause can give a single row and a single column (i.e., a single value). It is possible to apply a comparison according to the type of data displayed.

```sql
SELECT productid, AVG(quantity) AS avg_quantity
FROM order_details
GROUP BY productid
HAVING AVG(quantity) > (SELECT AVG(quantity) FROM order_details)
```

![Having sub query](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/3.+Accessing+Data/having_sub_query_1.PNG)

## Conclusion

A subquery is used to return data in a main query as a condition to further restrict data retrieval. Subqueries can be used with the SELECT, FROM, WHERE, and HAVING clauses.

---

