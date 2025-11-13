The **WHERE** clause is a filtering mechanism that we can use to limit the data retrieved so that it meets our specific query conditions.

Note

In this walkthrough, we will use the **pgAdmin4 app** to access the data in the **Northwind database**. We will then add a condition to our query using the **WHERE** clause.

Follow along the step by step process:

**Step 1**: In the pgAdmin4 app, click on Servers, and connect to the Northwind database.

**Step 2**: Inside the Northwind database, navigate to Schemas → Public → Tables → employees. Right-click on the `employees` table, and open the query tool, as in the image below:

> ![query tool](https://i.imgur.com/NJZ6gb9.png)
> 
> Type in the following query to retrieve all the rows in the `EMPLOYEES` table.
> 
> ```sql
> SELECT * FROM EMPLOYEES
> ```
> 
> See the following image
> 
> ![Select query](https://i.imgur.com/Zn7mZhR.png)
> 
> However, we would like to restrict the rows to the employees who were hired after 1992. As with anything in coding, there is more than one way to achieve this. One of the ways is to write the following query:
> 
> ```sql
> SELECT * FROM EMPLOYEES 
> WHERE hiredate > '1992-12-31'
> ```
> 
> The following query uses the `date_part` function and extracts the `year` part from the date, and achieved the same thing:
> 
> ```sql
> SELECT * FROM EMPLOYEES 
> WHERE date_part('year', hiredate) > 1992
> ```
> 
> You should see the following result set:
> 
> ![where employees hiredate](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/where_employees_hiredate.PNG)

**Step 3:** After we identified the employees hired after 1992, we might want to find the sales representative.

> Type in the following query:
> 
> ```sql
> SELECT * FROM EMPLOYEES 
> WHERE date_part('year', hiredate) > 1992 AND title = 'Sales Representative'
> ```
> 
> See this image
> 
> ![where employees hiredate with title](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/where_employees_hiredate_title.PNG)

**Step 4:** Among the employees identified in the previous step, we are now asked to identify the employees living in London.

> Type in the following query. Make sure to identify first the capitalization by exploring the data:
> 
> ```sql
> SELECT * FROM EMPLOYEES 
> WHERE date_part('year', hiredate) > 1992 
>  AND title = 'Sales Representative'
>  AND city = 'London'
> ```
> 
> See this image:
> 
> ![where employees hiredate with title](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/where_employees_hiredate_title_city.PNG)

**Step 5:** Now we will retrieve all the rows in the `CUSTOMERS` table. Right-click on the `customers` table, and open the query tool. We would like to identify customers who are located in Canada or in the United States.

> One of the ways is to execute the following query:
> 
> ```sql
> SELECT * FROM customers 
> WHERE country IN ('Canada', 'USA') 
> ```
> 
> See this image:
> 
> ![where customer country](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/where_customers_country.PNG)
> 
> There are 16 rows in total. You can see it at the bottom of your data output.
> 
> An alternative query would be the following: `sql SELECT * FROM customers WHERE country ='Canada' OR country = 'USA'`

**Step 6:** Among the customers that we identified in the previous step, we would like to be more specific on the city and filter out these two cities: Vancouver and Seattle.

> Type in the following query:
> 
> ```sql
> SELECT * FROM customers 
> WHERE country IN ('Canada', 'USA') 
>   AND city NOT IN ('Vancouver', 'Seattle')
> ```
> 
> See this image:
> 
> ![where customer country with city](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/where_customers_country_city.PNG)
> 
> There are 14 rows in total.
> 
> An alternative query would be the following:
> 
> ```sql
> SELECT * FROM customers 
> WHERE (country ='Canada' OR country = 'USA')
>   AND NOT city = 'Vancouver' 
>   AND NOT city = 'Seattle'
> ```

  

**Step 7:** The last step would be to filter on the customer address to include only the addresses with ‘Blvd’ in it.

> Type in the following query:
> 
> ```sql
> SELECT * FROM customers 
> WHERE country IN ('Canada', 'USA') 
>   AND city NOT IN ('Vancouver', 'Seattle')
>   AND address LIKE '%Blvd%'
> ```
> 
> See this image:
> 
> ![where customer country with address](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/where_employees_hiredate_title_city_address.PNG)

---

