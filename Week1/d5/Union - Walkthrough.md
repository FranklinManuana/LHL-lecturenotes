## Unions

As learned in the last reading, the `UNION` operator is used to combine the result set of two or more `SELECT` statements when the following are true:

- Every `SELECT` statement within `UNION` must have the same number of columns.
- The columns must also have similar data types.
- The columns in every `SELECT` statement must also be in the same order.

Follow this step-by-step walkthrough to use `UNION` in SQL.

Instruction

Use the Northwind database and follow the steps below to practice using UNION.

**Step 1: examine the data from the `shippers` and `suppliers` table and try to understand it.**

You should examine the schema of each table by expanding the columns of each table, like this:

![schema](https://i.imgur.com/6pUKWzZ.png)

You can also use the following query to get an idea of the result sets:

```sql
SELECT * FROM shippers LIMIT 10
SELECT * FROM suppliers LIMIT 10
```

**Step 2: create a new table using a `UNION` statement.**

Suppose that you want to set up a table where each row of the new table is either a supplier or shipper. This is where you can use the `UNION` statement.

Note

Note that the `suppliers` and `shippers` tables don’t have exactly the same columns, but recall that in order for `UNION` to work, you need:

- Every `SELECT` statement within `UNION` to have the same number of columns
    
- The columns to have similar data types
    
- The columns in every `SELECT` statement to be in the same order
    

Furthermore, suppose that in the new table you want the following columns: `id`, `name`, and `type` (to identify whether a partner is a supplier or a shipper). The following query will accomplish this:

```sql
SELECT shipperid AS id, companyname AS name, 'shipper' AS type FROM shippers
UNION
SELECT supplierid AS id, companyname AS name, 'supplier' FROM suppliers
```

Note

In a business context, this new table you created may be referred to as a partner table since shipper and suppliers are "partners" in the interaction.

### More Practice

**Task 1:** write a query that returns **unique** customers and suppliers names. To distinguish customers from suppliers, create an additional column named ‘Type’.

```sql
SELECT 'Customer' AS Type, contactname
FROM customers
UNION
SELECT 'Supplier' As Type, contactname
FROM suppliers
```

An alias was used in the temporary column and defined a value for each row, either ‘Customer’ or ‘Supplier’ depending on which table the contact name comes from. This can be useful to classify the information in the output for analysis purposes.

Note

The alias can be defined only one time and the query will give the same output, as follows:

```sql
SELECT 'Customer' AS Type, contactname
FROM customers
UNION
SELECT 'Supplier', contactname
FROM suppliers
```

**Task 2:** write a query that returns **all** customers and suppliers names:

- To distinguish customers from suppliers, create an additional column named ‘Type’. You can see that the result is the same as above (120 rows). If there would have been more rows, it would have told you that a customer can be a supplier as well.
    
- Since the UNION clause removes duplicates, it takes the first value that it sees. In your case, the information is first seen in the `customers` table.
    

```sql
SELECT 'Customer' AS Type, contactname
FROM customers
UNION ALL
SELECT 'Supplier' As Type, contactname
FROM suppliers
```