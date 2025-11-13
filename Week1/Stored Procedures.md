A stored procedure is a defined SQL query that can be saved and stored in a database, so the code can be reused over and over again. To execute a stored procedure, you need to 'call it'. You can also pass parameters to a stored procedure, so that the stored procedure can act based on the parameter value(s) that is passed.

Instruction

Read this article [Getting Started with Stored Procedures in PostgreSQL](https://retool.com/blog/getting-started-with-stored-procedures-in-postgresql/) to learn about stored procedures.

### Examples

"Stored procedures are a good fit for tasks that do something, as opposed to transforming input data or some kind of smaller function you’d want to include nested inside a normal SQL statement." [Getting Started with Stored Procedures in PostgreSQL]

Let's look at the following examples to understand the logic to implement the stored procedures:

**1. Imagine a sales system in which we have a table of products, a table for orders made at the store, and a table for orders made on the Internet. In these these tables, we have 3 important attributes:**

- The price
    
- The taxes
    
- The price with taxes
    

We would like to have a way to **calculate the value of taxes** and **the price with taxes** for all these attributes without worrying too much if the tax rate changes. This could be done with a **stored procedure** which would update all prices if the tax rate changes.

**Logic to implement:**

- Take an input parameter (the price and the taxes)
    
- Create an archive table, if it doesn’t exist yet
    
- Insert data into the archive table
    

**2. Imagine that every year, we need to archive the sales of the year in an archiving table. We would create a script and save it on our hard drive. That said, we could instead wrap these commands in a stored procedure that resides in a database.**

**Logic to implement:**

- Take an input parameter (the year)
    
- Create an archive table, if it doesn’t exist yet
    
- Insert data into the archive table
    

## Conclusion

A stored procedure in SQL is a named set of SQL statements that have been previously defined and stored in a database, which can be called repeatedly with different parameters.

There are several advantages of using SQL stored procedures, including:

- **Reusability:** Stored procedures can be called from multiple places in an application, allowing for modular and reusable code.
    
- **Better performance:** Because stored procedures are precompiled and cached, they can often execute faster than ad hoc SQL queries.
    
- **Improved security:** Stored procedures can be used to restrict access to sensitive data, as they can be granted permissions to specific users or roles, rather than giving direct access to tables.
    
- **Simplified maintenance:** Stored procedures can be updated and maintained independently of application code, allowing for easier database maintenance and upgrades.
    
- **Encapsulation of business logic:** Stored procedures allow for the encapsulation of business logic within the database, making it easier to manage and maintain.