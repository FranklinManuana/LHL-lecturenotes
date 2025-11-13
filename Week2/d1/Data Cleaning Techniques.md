### Constraints

Let's dig into different types of constraints you might encounter when cleaning data

**Data-type Constraints:** values in a particular column must be of a particular type. For example, the order date column in the Northwind database needs to be in a date format, not a numeric or boolean format.

**Range Constraints:** data should fall within a range. For example, the order date should not be in the future.

**Mandatory Constraints:** certain columns cannot be empty. For example, orderid, customerid should never be empty.

**Unique Constraints:** some fields must be unique. For customerid should always be unique.

### Other measures of quality

Here are some other ways you can measure the quality of your data; when cleaning data, look for

**Accuracy**: Your data vs their true values. For example, a street address in a customer contact may be inaccurate. This can be improved by using an external dataset to match up with the zip code.

**Completeness**: Any missing data. For example, does every productid have a categoryid assigned to it? Does every product have a unit price?

**Consistency**: The degree to which the data is consistent, within the same data set or across multiple data sets.

**Uniformity**: The degree to which a set of data measures are specified using the same units of measure in all systems. Are orders always measured in the same way with the same unit price by product or does the unit price change over time? Are all the order dates in the same format?

Instruction

Wanted to learn more on how to clean your data? watch this video [The Ultimate Guide to Data Cleaning in SQL](https://www.youtube.com/watch?v=iF6zHuReEZQ&t=223s) to learn data cleaning techniques that can be done in SQL.