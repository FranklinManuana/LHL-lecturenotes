We already discussed filtering results using restriction criteria in the `WHERE` clause. You should use the `WHERE` clause to filter the records and fetch only the necessary records.

Instruction

Read more about the `WHERE` operator in [this resource](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-where/) provided by PostgreSQL Tutorials.

`Where` specifies the search condition for the rows returned by a `DELETE`, `SELECT`, or `UPDATE` statement and limits the number of rows returned by or affected by the statement.

Note

It is important to note that we can have several conditions in a `WHERE` clause. However, we must pay attention to the **order of these conditions** and their associations.

To indicate associations between conditions, we use parentheses to specify the order of execution of the different conditions (as in algebra).

```sql
SELECT DISTINCT(contacttitle) FROM customers WHERE contacttitle LIKE '%Sales%'

SELECT DISTINCT(contacttitle) FROM customers WHERE contacttitle LIKE '%Sales%' OR contacttitle LIKE '%Admin%'

SELECT DISTINCT(contacttitle) FROM customers WHERE contacttitle LIKE '%Sales%' AND contacttitle LIKE '%Manager%'

SELECT DISTINCT(contacttitle) FROM customers WHERE contacttitle LIKE '%Sales%' OR contacttitle LIKE '%Admin%' AND contacttitle LIKE '%Manager%'

SELECT DISTINCT(contacttitle) FROM customers WHERE (contacttitle LIKE '%Sales%' OR contacttitle LIKE '%Admin%') AND contacttitle LIKE '%Manager%'
```

  

While you begin working with `WHERE` clause, reference this article [What are logical operators LIKE, IN and NOT in SQL?](https://www.educative.io/answers/what-are-logical-operators-like-in-and-not-in-sql) to read about logical operators `LIKE`, `IN` and `NOT` in SQL.

- First, learn about the following logical operators:
    
    - `LIKE`
    - `IN`
    - `NOT`
- Then, take the quiz integrated in the article to test your knowledge.
    

Let's conclude what we have learned from the referenced article

### Conclusion

The `SELECT` statement returns all rows from one or more columns in a table. To select rows that satisfy a specified condition, we use a `WHERE` clause.

**Logical operators** allow us to perform operations similar to using `WHERE` and `=` , but for specific cases:

- **LIKE**: is a logical operator in SQL that allows you to match similar values rather than exact ones. It is used for cases when we might not know exactly what we are looking for.
    
- **IN**: is a logical operator that allows you to specify a list of values that you'd like to include in the results. It is used for more than one condition.
    
- **NOT**: is a logical operator that you can put before any conditional statement to select rows for which that statement is false. It is used with the two operators above and helps us negate the query result easily.