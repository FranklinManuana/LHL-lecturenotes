In this activity, we are going to look at how **window functions** in SQL work and how they differ from classic _aggregate_ functions.

Window functions in SQL are a set of advanced analytical functions that allow you to perform calculations on a set of rows within a result set, called a "window". These functions are different from regular aggregate functions, which calculate values based on the entire result set.

Note

Window functions are commonly used for tasks such as calculating moving averages, ranking results, and comparing the current row to other rows in the result set.

The syntax for window functions in SQL includes the `OVER` clause, which defines the window of rows to operate on. The `OVER` clause can include a partitioning clause to group rows into separate partitions, and an `ORDER BY` clause to define the order of the rows within each partition.

Instruction

Read [this article from mode.com](https://mode.com/sql-tutorial/sql-window-functions/) to learn about the basics of window functions. These functions can be used in a similar way across different database types.

### Key Takeaways

A _window function_ performs a calculation across a set of table rows that are somehow related to the current row. This is comparable to the type of calculation that can be done with an aggregate function. However, unlike regular aggregate functions, the use of a window function does not cause rows to become grouped into a single output row — the rows retain their separate identities.