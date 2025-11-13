## Cumulative Data Cleaning Assignment Solution

In this activity, you will be able to compare the queries you used to answer the questions in the previous Cumulative Data Cleaning assignment with sample queries. Be sure to complete that activity first before reviewing the answers provided below.

**1- Write a query to find out if there are order ids missing.**

```sql
SELECT *
FROM orders
WHERE orderid IS NULL
```

---

**2- Write a query to get the orders with 5% discounts or higher. The output should be a list of unique order id.**

```sql
SELECT DISTINCT(orderid) AS orderid
FROM order_details
WHERE discount >= 0.05
```

---

**3- Write a query to get detailed information on customers that made orders. Your output must include the company name, the contact title and the id of each customer.**

```sql
SELECT customerid, companyname, contacttitle
FROM customers
WHERE EXISTS 
    (SELECT customerid
     FROM orders
     WHERE customers.customerid = orders.customerid)
```

---

**4- Write a query to get suppliers’ companies names that are located in Germany within the cities of Berlin or Frankfurt. Make sure there are no duplicates in the output.**

```sql
SELECT DISTINCT(companyname) AS companyname
FROM suppliers
WHERE country = 'Germany'
    AND city IN ('Berlin', 'Frankfurt')
```

Alternative:

```sql
SELECT DISTINCT(companyname) AS companyname
FROM suppliers
WHERE country = 'Germany'
    AND city IN ('Berlin', 'Frankfurt')
```

---

**5- Write a query to get the orders that were made in 1997 and were required in 1998.**

```sql
SELECT *
FROM orders
WHERE DATE_PART('YEAR', orderdate) = 1997 AND DATE_PART('YEAR',requireddate) = 1998
```

Alternative:

```sql
SELECT *
FROM orders
WHERE orderdate BETWEEN '1997-01-01' AND '1997-12-31' 
    AND requireddate BETWEEN '1998-01-01' AND '1998-12-31'
```

---

**6- Write a query to get the information on products with a quantity per unit defined in “pieces”. Make sure to include all capitalization.**

```sql
SELECT *
FROM products
WHERE UPPER(quantityperunit) LIKE '%PIECES%'
```

Alternative using LOWER:

```sql
SELECT *
FROM products
WHERE LOWER(quantityperunit) LIKE '%pieces%'
```

Alternative: Data exploration to see the different spellings for “pieces” as a first step.

```sql
SELECT DISTINCT(quantityperunit)
FROM products
```

```sql
SELECT *
FROM products
WHERE UPPER(quantityperunit) LIKE '%PIECES%'
```

---

**7- Write a query to get the details on orders with the following characteristics:**

**Note** that the alternatives are commented out.

```sql
SELECT *
FROM order_details
WHERE productid IN (50, 55, 57)
    --(productid = 50 OR productid = 55 OR productid = 57) 
    AND NOT DISCOUNT = 0 
    --AND DISCOUNT > 0 
    --AND DISCOUNT <> 0
    --AND DISCOUNT != 0
    AND (quantity = 120 OR quantity = 60)
    --AND quantity IN (60, 120)
```

---

### Reflection Opportunity

While doing this assignment, you probably reviewed readings and walkthroughs and also googled how to solve each task. This is in fact normal. You are not expected to know and remember every aspect of a SQL query.

Depending on your needs, you will use different operators and clauses. For that, you can always refer to external resources. You will eventually remember things with time and practice!

Question

Here are some reflective questions to support conducting a comparative analysis of your solution from the provided solution to see how similar or different both were:

- While doing this assignment, what was your thought process to solve it and the techniques used to identify the appropriate operators?
- What was your thought process to write your queries?
- What were the steps taken to review code?
- What were the steps taken to clean data? Would there be other things to consider when cleaning data?
- What did you miss out on?

  

Note

In the end, we would encourage you to create a personal benchmark of best practices from this exercise to follow when you perform data filtering and cleaning next time!