### Introduction to SQL JOINs: Relational Concepts

Up until this point, the data you have interacted with was located within a single table. The real power of SQL, however, comes from working with data from multiple tables at once. The power of a relational database lies in its ability to "relate" one table to another when the tables contain common identifiers that allow information from multiple tables to be combined easily.

To “relate” one table with another, you will use a `JOIN` clause. The `JOIN` clause allows you to combine rows from two or more tables, based on a related column between them.

Instruction

Read this article [SQL JOIN Types Explained](https://learnsql.com/blog/sql-joins-types-explained/) to learn about JOINs.

### **Aliases**

Consider the following join:

```sql
SELECT OrderID, CustomerName, OrderDate
FROM Orders
INNER JOIN Customers
ON Orders.CustomerID=Customers.CustomerID;
```

When performing JOINs, it's easiest to give your table name aliases. `Orders` and `Customers` are tedious to type after a while, so in this case, you can give the tables an alias by adding a space after the table name and typing the intended name of the alias. Using aliases, the above SQL query can then be rewritten as:

```sql
SELECT o.OrderID, c.CustomerName, o.OrderDate
FROM Orders o
INNER JOIN Customers c 
ON o.CustomerID=c.CustomerID;
```

### Filter Data in Joins

In an SQL query, data can be filtered in the `WHERE` clause or the `ON` clause of a join. This article [Using ON Versus WHERE Clauses to Combine and Filter Data in PostgreSQL Joins](https://www.pluralsight.com/guides/using-on-versus-where-clauses-to-combine-and-filter-data-in-postgresql-joins) will examine the difference between the two in PostgreSQL.

## Conclusion

The JOIN clause is defined as a method for matching records from different tables based on a specified condition. In an SQL query, data can be filtered in the WHERE clause or the ON clause of a join.