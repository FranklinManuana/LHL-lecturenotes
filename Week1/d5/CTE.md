## CTE

Similar to subqueries, for analytical purposes, you sometimes need to define a temporary result and query this result. To tackle this, you can use CTEs. A CTE is the result set of a query which exists temporarily and for use only within the context of a larger query.

### CTE Structure

A CTE starts with the **WITH clause**, which allows you to define a temporary result from which you will work. This temporary result represents a set on which you will perform a main query.

Note

A good practice is to start with the temporary query and then integrate this query into a complete CTE. Otherwise, the full query can be quite complex to debug.

A CTE can sometimes replace a complex query or make it more readable.

Instruction

Read more on the topic in this article [PostgreSQL CTE](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-cte/).

## Conclusion

A CTE is a temporary result set which you can reference within another SQL statement, including `SELECT`, `INSERT`, `UPDATE`, or `DELETE`. They are used to simplify complex queries and are temporary in the sense that they only exist during the execution of the query.