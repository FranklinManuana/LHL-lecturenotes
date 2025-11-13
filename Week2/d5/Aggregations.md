### Simple Aggregations

SQL is excellent at aggregating data in a way that is similar to using pivot tables in Excel. Aggregations in SQL refer to the process of performing calculations on a set of values. Since you will use aggregate functions all the time, it's important to get comfortable with them. The functions themselves are the same ones you will find in Excel or any other analytics program. We'll cover them individually in the next few activities.

Here's a quick preview:

- `COUNT`: This function counts the number of rows in a specified column. It's often used to determine how many records are in a table, or how many times a certain value appears in a column.
    
- `SUM`: This function adds together all the values in a specified column. It's useful for calculating totals, such as the total sales for a company or the total number of hours worked by employees.
    
- `MIN` and `MAX`: These functions return the lowest and highest values in a specified column, respectively. They're often used to find the smallest or largest value in a dataset.
    
- `AVG`: This function calculates the average value of a group of selected values in a specified column. It's often used to calculate the average salary of employees or the average price of a product.
    

Note

The arithmetic operators only perform operations across rows. Aggregate functions are used to perform operations across entire columns (which could include millions of rows of data or more).

### Aggregations with the `GROUP BY` Clause

Aggregations functions like `COUNT`, `AVG`, and `SUM` have something in common: they all aggregate across the entire table. But what if you want to aggregate only part of a table? For example, you might want to count the number of entries for each year.

In situations like this, you'd need to use the `GROUP BY` clause. `GROUP BY` allows you to separate data into groups, which can be aggregated independently of each other.

Instruction

For more information on “Aggregation functions in SQL” you can read the following article: [https://learnsql.com/blog/beginners-guide-sql-aggregate-functions/](https://learnsql.com/blog/beginners-guide-sql-aggregate-functions/)

#### Conclusion

In SQL, aggregate functions are used to perform numerical calculations on data and return summarized information about a given column or result set. These functions can be used with the `GROUP BY` statement.