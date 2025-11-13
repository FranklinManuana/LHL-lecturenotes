The best way to learn SQL order of operations is through practice. By using examples, you will explore the execution order of the six most common operations in an SQL query: `SELECT`, `FROM`, `WHERE`, `GROUP BY`, `HAVING`, and `ORDER BY`.

Instruction

You will start with a simple query using the Northwind database to obtain the names of the employees who have the title Sales Representative:

```sql
SELECT firstname, lastname
FROM employees
WHERE title = 'Sales Representative'
```

  
  

**First**, SQL server will execute the `FROM employees`, which retrieves this data:

![Employee Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_table.PNG)

  
  

**Second**, SQL server will execute the `WHERE title = 'Sales Representative'`, which narrows it down to this:

![Sales Rep Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_salesrep_table.PNG)

  
  

**Finally**, SQL server will apply `SELECT firstname, lastname`, producing the final result of the query:

![Sales Rep Name Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_salesrep_name_table.PNG)

  
  

---

### Changes in the Order of Operations if you Add ORDER BY Clause

---

Consider the following scenario: suppose your boss receives a report based on the query in the previous example and asks you to sort the employee names in alphabetical order. You, therefore, need to add an `ORDER BY` clause to the previous query:

```sql
SELECT firstname, lastname
FROM employees
WHERE title = 'Sales Representative'
ORDER BY firstname
```

Note

The execution process of this query is almost the same as in the previous example. The only change is at the end when the `ORDER BY` clause is processed.

The final result of this query orders the entries by “firstname”, as shown below:

  
  

![employees salesrep name orderby table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_salesrep_name_orderby_table.PNG)

  
  

---

### Adding GROUP BY and HAVING Clauses to the Query

---

In this example, you will use a query with `GROUP BY` clause. Suppose you want to obtain how many employees for each position in the company have been hired in 1992 and you want the result in descending order by the number of people by position. The query could be:

```sql
SELECT title, COUNT(*)
FROM employees
WHERE EXTRACT(YEAR FROM hiredate) = 1992
GROUP BY title
ORDER BY COUNT(*) DESC
```

  
  

Again, SQL server will **first** execute `FROM employees`, which retrieves this data:

![Employee Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_table.PNG)

  
  

**Second**, SQL server will execute `WHERE EXTRACT(YEAR FROM hiredate) = 1992`, which narrows it down to this:

![Employee Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_hiredate_table.PNG)

  
  

**Third**, `GROUP BY` is applied, generating one record for each distinct value in the `GROUP BY` columns. In this example, SQL server will create one record for each distinct value in “title”:

![Employee Hire Date Group By Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_hiredate_groupby_table.PNG)

  
  

**Fourth**, SQL server will apply `SELECT` with `COUNT(*)`, producing this intermediate result:

![Employee Hire Date Group By Count Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_hiredate_groupby_count_table.PNG)

  
  

**Finally**, SQL server will apply the `ORDER BY` clause, producing the final result of the query:

![Employee Hire Date Group By Count OrderBy Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_hiredate_groupby_count_orderby_table.PNG)

  
  

In this next example, you will add the `HAVING` clause. Suppose you now want to obtain all titles for which employees were hired after 1992 and for which there is more than one employee with the title. The query for this situation is:

```sql
SELECT title
FROM employees
WHERE EXTRACT(YEAR FROM hiredate) > 1992
GROUP BY title
HAVING COUNT(*) > 1
```

Again, SQL server will **first** execute `FROM employees`, which retrieves this data:

![Employee Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_table.PNG)

  
  

**Second**, the `WHERE` clause, excluding employees hired after 1992, is processed:

![Employee Table Hired After 1992](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_hiredate1992_table.PNG)

  
  

**Third**, `GROUP BY` is applied, generating the following records:

![Employee Table Hired After 1992 Group By](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_hiredate1992_groupby_table.PNG)

  
  

**Fourth**, `HAVING COUNT(*) > 1` is applied to filter the group of records generated by `GROUP BY`:

![Employee Table Hired After 1992 Group By Having](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_hiredate1992_groupby_having_table.PNG)

  
  

**Finally**, the `SELECT` clause is applied, producing the final result of the query:

![Employee Table Hired After 1992 Group By Having Select](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_hiredate1992_groupby_having_select_table.PNG)

  
  

---

### Adding the JOIN Clause

---

The previous example dealt with one table. Add a second table using the `JOIN` clause. Suppose you want to obtain the last names and employee IDs of employees whose territory ID is 19713. The query for this situation could be:

```sql
SELECT employees.employeeid AS employeeid
,employees.lastname
FROM employees 
JOIN employeeterritories 
ON employees.employeeid = employeeterritories.employeeid
WHERE employeeterritories.territoryid = '19713'
```

Again, SQL server will **first** execute `FROM employees`, which retrieves this data:

![Employee Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_table.PNG)

  
  

**Second**, SQL server will apply the `JOIN` clause generating a new intermediate result combining both tables:

![Employee Territory Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_employeeterritory_table.PNG)

  
  

**Third**, `WHERE employeeterritories.territoryid = '19713'` is applied:

![Employee Territory Table](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_employeeterritory_where_table.PNG)

  
  

**Finally**, `SELECT employees.employeeid AS employeeid,employees.lastname` is executed, producing the final result of the query:

![Employee Territory Table after select](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/employees_employeeterritory_where_select_table.PNG)

Great job completing the Order of Execution - Walkthrough.