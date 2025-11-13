## Debugging an SQL Query

---

Writing SQL queries implies experiencing bugs and errors. What should you do when your query returns an error message? Here are some guidelines to follow when you encounter an error.

**First**, go to the line that is failing in your SQL query:

Instruction

Based on that error message, you should go to line 1 and validate that “customersid” exists. You should fix this by making sure that the variable you are requesting for really exists, or by validating its syntax.

**Second**, check the SQL syntax on the line that is failing in your SQL query. By exploring the data in the customers table, you see that the correct syntax for that variable is in fact “customerid”. The error message may also include a hint to help you fix the bug of your query:

**Third**, check your query logic if the query uses joins, subqueries, or common table expressions (CTEs). These concepts will be covered later but the objective behind that step is to make sure the anatomy of the query is appropriate.

**Finally**, if you get an error message that isn’t specific to your SQL query, go to Troubleshooting error messages.

---

### How Does SQL Debugging Work?

---

SQL error messages are displayed for each line in your query that fails to run.

Instruction

You will need to follow the steps above for each line that fails.

If you make any changes to a line, run your query to check if the problem is fixed before moving on to the next step.

Note

Note that SQL queries are not run from top to bottom, as you saw in the order of execution section, so you won’t be debugging your query lines in the order that they are written. Follow the error messages to help you find the lines that need attention.

---

### Debugging SQL Syntax

---

**First**, review the spelling on the line that is failing in your SQL query:

**HINT**: Perhaps you meant to reference the column "customers.companyname".

Note

Nevertheless, the variable name is spelled correctly in the `SELECT` clause but not in the `WHERE` clause which still gives an error message.

Instruction

Again, you need to investigate the correct syntax by exploring the data, including selecting all the data in the customers table, as follows:

It may seem simple, but it may save you a lot of time for heavy and big queries.

**Second**, you can review for missing brackets or commas on the line that is failing in your SQL query:

---

---

**Third**, review removed commented lines (lines that begin with -- or /* ):

An example would be where you **do not** receive an error message but the query won’t return any result:

Note

The reason you don’t get any results even if you know that these two values exist, is that a customer cannot live in two countries at the same time. So it’s not possible that two values are affected by one customer. Therefore, you need to fix the query by **commenting on one** of the two values.

**Finally**, review common syntax errors that are specific to your SQL dialect:

- Correct spelling
    
- Punctuation
    
- Comments are not meant to be read or executed
    

---

### Common Syntax Errors

---

Take a look at some common syntax errors and see what an error message might say. For example:

**1. Column or table name is “not found” or “not recognized”**.

Follow the step-by-step process below to review this error.

Instruction

Review the **structure** section of the reference guide for your SQL dialect, in our case, PostgreSQL:

**a. Are you using the correct quotation marks? For example:**

i) `SELECT customerid FROM customers WHERE country = 'Mexico' AND country = 'UK'`

ii) `SELECT customerid FROM customers WHERE country = "Mexico" AND country = "UK"`

iii) ``SELECT customerid FROM customers WHERE country = `Mexico` AND country = `UK```

**b. Are you using the correct path to columns and tables? For example:**

i) `FROM table_name`

ii) `FROM schema_name.table_name`

iii) `FROM database.schema_name.table_name`

**c. Is your column name a reserved word? For example:**

In PostgreSQL, ‘users’ is a reserved word.

i) `SELECT users` will throw an error

ii) `SELECT "users"` will run correctly

**2. SQL function does not exist.**

Briefly, a function is an SQL statement that performs an action on a field in a database table and returns a result. It goes from date functions to extract information from a date field, such as the month of a date, or mathematical functions to get information from numerical data, such as the average monthly sales.

Although functions will be covered later, it is important to mention that the use of functions in queries can lead to errors.

**Example using the SUM function:**

**Returns the following error message:**

**HINT**: No function matches the given name and argument types. You might need to add explicit type casts.

Instruction

Follow the step-by-step process below to review this error.

**First**, review the **data type** of the column that you want your function to apply to.

For example, if you want to get the sum of monthly sales, you should make sure that the data type of the field defined in your SELECT clause (the input to your function) is numerical. In the above example, the data type of orderdate is

**a. How to check/find column types of a table?**

The output verifies that the information schema retrieves the column names and respective data types of the orders table.

**b. How to check/find the type of a particular column?**

To check the data type of only a specific column, you must specify the name of that particular column in the WHERE clause. The above query will retrieve the data type of the column named “orderdate”.

From here, you figure out that the function was not working because it is a date function.

**Secondly**, review the **function** section for your SQL dialect:

a. Confirm that the function exists for your SQL dialect. The best way is to google it.

b. Review the data type(s) that are accepted by your function.

**Lastly**, if the field type of your column does not match the expected data type of your function:

Cast your column to the correct data type in your SQL query. CAST function is essentially used to convert a data type from one to another. It will be covered later although you can notice that the _hint_ of the above error advises to cast the date field. However, not all the hints are relevant. It wouldn’t make sense, in this case, to convert a date to a numeric value. It therefore needs to make sense to make a conversion.

For example, it would make sense to extract the time of a date to make calculations such as the average time.

Note

SQL functions are designed to work on specific data types in a database. For example, the DATE_TRUNC function in PostgreSQL works on columns with **date**, **timestamp**, and **time**. If you try to use DATE_TRUNC function on a column with a **string** data type, it won’t work.

  
  

---

### How to Find the Failing Line in an SQL Query

---

Read your SQL error message. Does your error message:

- Tell you the line or character position?
    
- Include a table or column name?
    
- Mention an SQL clause?
    
- Identify a syntax error with an operator?
    
- Tell you the function does not exist?
    

Warning

A query might return a result that is inaccurate. You should therefore have **expectations** on the result to be returned and **always** review the logic of your query.

### Reflection Opportunity

Based on this walkthrough and what you have experienced with SQL so far, what is or would be your process to avoid getting errors?

- Do some data exploration.
    
- Review the logic and structure of your query before executing it.
    

---

