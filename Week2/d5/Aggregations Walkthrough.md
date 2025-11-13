Use the Northwind database and follow the steps below to practice using the Aggregation functions in SQL.

**Step 1:** Examine the data from the customers table and try to understand it

```sql
SELECT * FROM customers
```

**Step 2:** To get started with aggregation functions, begin by using the COUNT function. The COUNT function is used to count the number of rows in a particular column. For example, to count the number of customers in the Customers table, you can use the following query:

```sql
SELECT COUNT(CustomerID) AS TotalCustomers FROM Customers;
```

**Step 3:** Next, try using the SUM function to calculate the total sales for each customer. To do this, you will need to join the Customers, Orders, and Order_Details tables together. The Customers table contains information about each customer, while the Orders table contains information about each order, and the Order_Details table contains information about each product in each order. You can use the following query to calculate the total sales for each customer:

```sql
SELECT Customers.CustomerID, SUM(Order_Details.UnitPrice * Order_Details.Quantity) AS TotalSales
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID
INNER JOIN Order_Details ON Orders.OrderID = Order_Details.OrderID
GROUP BY Customers.CustomerID;
```

**Step 4:** Another useful aggregation function is AVG, which is used to calculate the average value of a group of selected values. To calculate the average order value for each customer, you can use the following query:

```sql
SELECT Customers.CustomerID, AVG(Order_Details.UnitPrice * Order_Details.Quantity) AS AverageOrderValue
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID
INNER JOIN Order_Details ON Orders.OrderID = Order_Details.OrderID
GROUP BY Customers.CustomerID;
```

**Step 5:** Next, try using the MAX and MIN functions to find the highest and lowest values in a particular column. For example, to find the highest unit price for each product in the Products table, you can use the following query:

```sql
SELECT ProductName, MAX(UnitPrice) AS HighestUnitPrice
FROM Products
GROUP BY ProductName;
```

**Step 6:** Finally, suppose you want to find the total sales and average sales per order for each year in the Orders table. To do this, you can use the SUM function to calculate the total sales for each order and the AVG function to calculate the average sales per order. You can then group the results by year using the EXTRACT function to extract the year from the OrderDate column. Here's an example query:

```sql
SELECT EXTRACT(year FROM OrderDate) AS OrderYear, 
       SUM(UnitPrice * Quantity) AS TotalSales, 
       AVG(UnitPrice * Quantity) AS AverageSalesPerOrder
FROM Orders
INNER JOIN Order_Details ON Orders.OrderID = Order_Details.OrderID
GROUP BY EXTRACT(year FROM OrderDate)
ORDER BY OrderYear;
```

### More Practice

Instruction

Continue to practice by completing the following tasks:

> **Task 1**: Write a query to get the most expensive and the least expensive product (name and unit price) (2 separate queries)

Solution :

```sql
SELECT ProductName, UnitPrice
FROM Products
WHERE UnitPrice = (SELECT MAX(UnitPrice) FROM Products);

SELECT ProductName, UnitPrice
FROM Products
WHERE UnitPrice = (SELECT MIN(UnitPrice) FROM Products);
```

---

> **Task 2**: Write a query to count the number of current and discontinued products.

Solution :

```sql
SELECT Discontinued, COUNT(*) AS ProductCount
FROM Products
GROUP BY Discontinued;

```

---

> **Task 3**: Write a query to find the total quantity of orders sold

Solution :

```sql
SELECT SUM(Quantity) AS TotalQuantity
FROM Order_Details;

```

---

> **Task 4**: Write a query to get the total quantity of orders sold for each order (830 rows)

Solution :

```sql
SELECT OrderID, SUM(Quantity) AS TotalQuantity
FROM Order_Details
GROUP BY OrderID;

```

---

> **Task 5**: Write a query to get the number of employees who have been working more than 5 years in the company

Solution :

```sql
SELECT COUNT(*) AS NumEmployees
FROM Employees
WHERE EXTRACT(YEAR FROM CURRENT_DATE) - EXTRACT(YEAR FROM HireDate) > 5
   OR (EXTRACT(YEAR FROM CURRENT_DATE) - EXTRACT(YEAR FROM HireDate) = 5 AND EXTRACT(MONTH FROM CURRENT_DATE) >= EXTRACT(MONTH FROM HireDate) AND EXTRACT(DAY FROM CURRENT_DATE) >= EXTRACT(DAY FROM HireDate));

```

Great Job!