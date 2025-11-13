In this walkthrough, you will use the **Northwind** database that you restored in PostgreSQL.

#### Northwind Database

_Northwind_ Database is the sample database that originally comes with Microsoft Access application. Nowadays, it's popular for learning basic `SQL` logic and queries by different database providers.

In the picture below, you can see the data model of the Northwind database:

![](https://i.imgur.com/rvJyZco.png)

Note

For more information about the database, please read this introduction by the access buddy, [Northwind Database Explained](https://theaccessbuddy.wordpress.com/2011/07/03/northwind-database-explained/).

In the last topic, Anatomy of a Query, you have learned that **the SQL query is a request to databases to fetch (or retrieve) information** and it has multiple clauses, such as `SELECT`, `FROM`, `WHERE`, `GROUP BY`, `HAVING`, and `ORDER BY`.

Practice each clause in the following exercise; do not forget to execute queries while practicing.

---

### SELECT

---

##### What can you do with the `SELECT` clause:

**1. You can select at least one field**

**Example**: Get the contact names of Northwind customers.

```sql
SELECT contactname
FROM customers
```

**2. You can select multiple fields**

**Example**: Get the contact names and the company names of Northwind customers.

```sql
SELECT contactname, companyname
FROM customers
```

**3. You can select all fields**

**Example**: Get all the information on Northwind customers.

```sql
SELECT *
FROM customers
```

**4. You can select unique values using `DISTINCT`(field)**

**Example**: Identify the different employee titles at Northwind.

```sql
SELECT DISTINCT(title)
FROM employees
```

**5. You can rename a field**

**Example**: Rename the field contactname for customername in the customers table of Northwind.

```sql
SELECT contactname as customername
FROM customers
```

**6. You can apply an aggregate function to a field using `MIN`, `MAX`, `SUM`, `AVG`, `COUNT` (to be covered later)**

**Example**: Get the average unit price for all the products sold by Northwind.

```sql
SELECT AVG(unitprice)
FROM order_details
```

  

---

### FROM

---

##### What you can do with the `FROM` clause:

**1. Reference the table involved in the query**

**Example**: Get the information on Northwind orders.

```sql
SELECT *
FROM orders
```

**2. Reference multiple tables involved using `JOINS`(to be covered later)**

**Example**: Get the information on Northwind suppliers and the products each supplier sells to Northwind.

```sql
SELECT suppliers.companyname, products.productname
FROM products
INNER JOIN suppliers ON products.supplierid = suppliers.supplierid
```

  

---

### WHERE

---

##### What you can do with the `WHERE` clause:

**1. Filter data**

**Example**: Get the information on Northwind employees who are sales representatives.

```sql
SELECT *
FROM employees
WHERE title = 'Sales Representative'
```

Warning

SQL is case sensitive on the values of records. Make sure to use the appropriate case sensitivity.

Note

The `WHERE` clause is evaluated for each record resulting from the `FROM`. Only when it gives TRUE result the record is kept. The record is not kept in case of FALSE or unknown result.

Below are some references to use when applying filters on the data.

##### Comparison Operators

Comparison operators test whether two expressions are the same. Look at the following operators and their meanings, and practice the provided examples.

|Operator|Meaning|Example|
|---|---|---|
|=|Equal to||
|>|Greater than||
|<|Less than||
|>=|Greater than or equal to||
|<=|Less than or equal to||
|<>|Not equal to||
|!=|Not equal to||

##### Logical Operators

Logical operators test for the truth of some condition. Logical operators, like comparison operators, return a **Boolean** data type with a value TRUE, FALSE, or UNKNOWN.

|Operator|Meaning|Example|
|---|---|---|
|AND|TRUE if both Boolean expressions are TRUE||
|BETWEEN|TRUE if the operand is within a range||
|EXISTS|TRUE if a subquery contains any rows||
|IN|TRUE if the operand is equal to one of a list of expressions||
|LIKE|TRUE if the operand matches a pattern: <br><br>  <br><br>→ Finds any values that _start_ with "a"  <br><br>→ Finds any values that _end_ with "a"  <br><br>→ Finds any values that have "or" in any position||
|NOT|Reverses the value of any other Boolean operator||
|OR|TRUE if either Boolean expression is TRUE||

  

---

### GROUP BY

---

##### What you can do with the GROUP BY clause:

**1. Group data by field**

**Example**: Get the list of country of Northwind customers.

```sql
SELECT country
FROM customers
GROUP BY country
```

Note

When one field is selected and the data is grouped by, the GROUP BY clause is equivalent to the DISTINCT in the SELECT clause.

**2. Group data according to one, two, three, …, x fields**

**Example**: Get the list of country and city of Northwind customers.

```sql
SELECT country, city
FROM customers
GROUP BY country, city
```

Warning

When one field is used in the GROUP BY clause but there are multiple fields in the SELECT clause, then all fields must be defined in the GROUP BY clause.

**3. Group data by aggregate functions**

**Example**: Get the number of customers by country.

```sql
SELECT country, COUNT(customerid)
FROM customers
GROUP BY country
```

  

---

### HAVING

---

##### What you can do with the HAVING clause:

**1. Filter a grouping**

**Example**: Get the countries with more than five customers.

```sql
SELECT country, COUNT(customerid)
FROM customers
GROUP BY country
HAVING COUNT(customerid) > 5
```

**No HAVING without GROUP BY**

  

---

### ORDER BY

---

##### What you can do with the ORDER BY clause:

**1. Sort results by ascending (default option) or descending order**

**Example**: Get the countries with more than five customers and sort the result by country in alphabetical order.

```sql
SELECT country, COUNT(customerid)
FROM customers
GROUP BY country
HAVING COUNT(customerid) > 5
ORDER BY country
```

**2. Sort results by one, two, three, …, x fields**

**Example**: Get the title of each Northwind employee with their first and last name and sort the result by title and first name.

```sql
SELECT title, firstname, lastname
FROM employees
ORDER BY title, firstname
```

---

[

](https://web.compass.lighthouselabs.ca/p/ds-5/days/w01d2/activities/2340)