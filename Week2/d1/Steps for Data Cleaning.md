Data cleaning is the process of removing incorrect, duplicate, or otherwise erroneous data from a dataset. By performing data cleaning we improves the quality of our data, as well as, the quality of any business decisions that we draw based on the data.

Note

Data cleaning is often a tedious process, but it’s absolutely essential to get top results and powerful insights from your data. Here are some things to consider when you approach data cleaning:

- Does the data make sense?
- Identify missing values and extreme values – filling missing values if you can
- Choose the best tool to proceed
- Communicate your observations along the way

Let's follow a step by step process to see how to implement the above considerations when it comes to data cleaning. Use the **Northwind database** and follow the steps below to perform data cleaning!

**Step 1: Retrieve sample data**

Retrieve some of the data and try to understand it

```sql
SELECT * FROM employees
LIMIT 100
```

Instruction

View the value of `birthdate` and `hiredate`. Make sure that these datetime values make sense.

**Step 2: Explore unique values**

Explore some unique values from the sample data. Make sure there are no duplicates.

```sql
SELECT employeeid, firstname FROM employees
SELECT DISTINCT(employeeid), firstname FROM employees
```

Instruction

Observe, if the number of rows in the result are same for the both queries? There should only be one record by the employee. Having the same information duplicated on an employee would introduce a bias due to the fact that there would be too much emphasis on that employee (double count).

**Step 3: View the value of `orderdate` and `requireddate`.**

View the value of `orderdate` and `requireddate`, make sure that, for each order, `orderdate` is always smaller or equal to `requireddate`. We could assume that a customer must make an order first and then specify a required date.

```sql
SELECT * FROM orders
WHERE orderdate > requireddate
```

Note

You can also do that for `birthdate` and `hiredate` for each employee.

**Step 4: Identify missing and extreme values**

Identify some missing values and extreme values. Fill in missing values if you can.

```sql
SELECT city, region FROM employees
GROUP BY city, region
```

Question

Can you identify where the `city` is London and the `region` has missing values. Can we fill in the `region` value?

Note

Yes we can, but before that, we should find out more facts about these employees. After ensuring that they are indeed based in London, UK, then we can fill in the missing values as follows:

```sql
SELECT employeeid, lastname, firstname, title, birthdate, hiredate, city,
CASE when region is NOT NULL then region
WHEN city = 'London' THEN 'UK' end as region
FROM employees
```

We can identify missing values for `address` for each customer. Let's assume that there is a requirement that each customer needs to have an address to make an order.

```sql
SELECT *
FROM customers
WHERE address is NULL
```

**Step 5: Choose the best tool to proceed**

At this point, SQL is the tool we are using to clean the data so there is no choice of tool that needs to be made for this activity. However, as you grow your data skills, you will be exposed to other languages that can be used to clean data. One of those languages is Python.

It is important to mention that as the number of languages you are able to work with increases, at some point in the data-cleaning process, you will have to decide which is the best for the situation at hand. For example, you may need to consider if the data cleaning should be performed using SQL inside a database, or using a programming language on the retrieved data (outside the database).

Note

Using a programming language outside of the database means that you will need to update the table(s) in the database with the cleaned data. The best approach depends on your specific situation.

**Step 6: Communicate your data-cleaning approach**

Communicate your data-cleaning approaches along the way. In this case, we have filled the missing values of the region to be the UK where the city is London. We should be aware that this may not have been the appropriate decision as there is a city in Ontario named London as well. This is a good example where you need to communicate the assumptions you made in your data cleaning process.

### Conclusion

Data cleaning is an extremely crucial stage in the data analysis process and can be time-consuming. Using the general questions and steps outlined in this activity is a great starting point to orient your data-cleaning process.