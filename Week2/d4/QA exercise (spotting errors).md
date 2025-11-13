## Quality Assurance for Northwind Database using SQL

Instruction

Let's complete the following tasks by performing QA techniques to detect invalid information from a database. The solution for each task is provided at the end of the document. We encourage you to perform the tasks first and then check your queries with the provided solution.

**Task 1: Data Profiling**

- Use SQL queries to identify the schema of the Northwind database and its tables.
    
- Write SQL queries to determine the data types, null values, and unique values in each table.
    
- Analyze the results of your queries and document any potential data quality issues.
    

---

**Task 2: Data Validation**

- Write SQL queries to validate the data in the Northwind database, for example, by checking for missing or duplicate data, or data that falls outside expected ranges.
    
- Document any issues you find and propose solutions to resolve them.
    

---

**Task 3: Data Cleansing**

- Identify any data quality issues in the Northwind database, such as missing or inconsistent data, and write SQL queries to clean the data.
    
- Document your cleaning process and explain any decisions you made.
    

---

**Task 4: Testing**

- Develop a set of SQL test cases to ensure the quality of the Northwind database, for example, by testing for valid data values and ensuring that calculated fields are accurate.
    
- Write SQL queries to execute your test cases and document the results.
    
- Identify any issues that arise and propose solutions to resolve them.
    

---

**Task 5: Documentation**

- Create a document that summarizes your QA process for the Northwind database, including your data profiling, validation, cleansing, and testing procedures.
    
- Include any SQL queries or scripts you used in your process, as well as explanations of any decisions you made.
    

Note

Conclude with any recommendations for improving the quality of the Northwind database

### Solutions :

To identify the schema of the Northwind database, you can use the following SQL query:

**Task 1: Data Profiling**

```sql
SELECT *
FROM information_schema.tables
WHERE table_schema = 'public';
```

This query will return a list of all tables in the public schema of the Northwind database. (14 tables)

To determine the data types, null values, and unique values in each table, you can use queries like the following:

- Get column data types and nullability for the employees table

```sql
SELECT column_name, data_type, is_nullable
FROM information_schema.columns
WHERE table_name = 'employees';
```

- Count unique values for the country column in the customers table

```sql
SELECT COUNT(DISTINCT country)
FROM customers;
```

[Should get 21 for the second SQL]

By analyzing the results of these queries, you may notice data quality issues like missing or inconsistent data, or unexpected data types.

---

**Task 2: Data Validation**

To validate the data in the Northwind database, you can use queries like the following:

- Check for missing data in the order_details table

```sql
SELECT *
FROM order_details
WHERE quantity IS NULL;
```

- Check for duplicate data in the customers table

```sql
SELECT customerid, COUNT(*)
FROM customers
GROUP BY customerid
HAVING COUNT(*) > 1;
```

[No Missing data and no duplicate in customers table]

By analyzing the results of these queries, you can document any issues you find and propose solutions to resolve them. For example, if you find missing data, you may need to fill in the missing values with appropriate defaults or values from related tables. If you find duplicate data, you may need to merge the duplicate records or choose one record to keep and delete the others.

---

**Task 3: Data Cleansing**

To clean the data in the Northwind database, you can use queries like the following:

- Clean the phone numbers in the customers table by removing non-digit characters

```sql
UPDATE customers
SET phone = regexp_replace(phone, '[^0-9]', '', 'g')
WHERE phone LIKE '%(%-%) %-%';
```

- Standardize the country names in the customers table

```sql
UPDATE customers
SET country = CASE
    WHEN country IN ('USA', 'United States') THEN 'United States'
    WHEN country = 'UK' THEN 'United Kingdom'
    ELSE country
    END;
```

By documenting your cleaning process and explaining any decisions you made, you can help ensure that the Northwind database is more accurate and consistent.

---

**Task 4: Testing**

To develop a set of SQL test cases to ensure the quality of the Northwind database, you can use queries like the following:

- Test that the order dates in the orders table are valid

```sql
SELECT *
FROM orders
WHERE orderdate < '1900-01-01';
```

- Test that the discount amounts in the order_details table are accurate

```sql
SELECT orderid, SUM(unitprice * quantity * (1 - discount)) AS total_discount
FROM order_details
GROUP BY orderid
HAVING SUM(unitprice * quantity * (1 - discount)) < 0;
```

[No error in both testing queries]

By executing your test cases and documenting the results, you can identify any issues that arise and propose solutions to resolve them. For example, if you find invalid order dates, you may need to update the affected records with valid dates. If you find inaccurate discount amounts, you may need to recalculate the discounts or investigate the underlying data to identify the cause of the issue.