As you may recall, ETL, which stands for extract, transform and load, is a data integration process that combines data from multiple data sources into a single, consistent data store that is loaded into a database. ![Diagram showing the different source files that data can be extracted formed, then transformed and then loaded into a data warehouse](https://i.imgur.com/crUuOns.png)

So far, we have focused on the **E** and the **T** of the process.

### Extract

During data extraction, raw data is copied or exported from source locations to a staging area. Data management teams can extract data from a variety of data sources, which can be structured or unstructured.

Now would be a good time to review some of the activities that were focused on extracting data:

- [Sources of Data](https://web.compass.lighthouselabs.ca/af746c1c-c1a8-498d-ae1f-cf49acd8f459)
- [Visualizing Databases](https://web.compass.lighthouselabs.ca/0983ec23-30a2-4277-80d2-d1c434942a1e)
- [Filtering Data: WHERE clause](https://web.compass.lighthouselabs.ca/3ad2536e-bd92-4e9f-a9f6-c9eba478d535)
- [Using SQL to Access Data](https://web.compass.lighthouselabs.ca/3a4b96af-9c75-4583-bc77-a8bc8651b323)

### Transform

In the staging area, the raw data undergoes data processing. Here, the data is transformed and consolidated for its intended analytical use case. This phase can involve the following tasks:

Now would be a good time to review some of the activities that were focused on transforming data:

- [What is Data Transformation?](https://web.compass.lighthouselabs.ca/55c9c146-93c6-42b0-8c2f-86996f31634d)
- [Importance of Data Cleaning](https://web.compass.lighthouselabs.ca/1b28cb81-19f5-416c-9487-fb961e772045)
- [Steps of Data Cleaning](https://web.compass.lighthouselabs.ca/4f4abaee-e080-4174-92c6-5c06d6b95e6a)
- [Using SQL to Clean Data](https://web.compass.lighthouselabs.ca/582c9cdb-7c5f-4fc4-8268-06fcaacb890a)
- [Aggregations](https://web.compass.lighthouselabs.ca/7e77f0a9-a879-4d46-896a-62d85f0ecd11)
- [Joins](https://web.compass.lighthouselabs.ca/3a2f9b84-988a-40f3-96cc-374afe28ae44)
- [Unions](https://web.compass.lighthouselabs.ca/adeba29f-620a-4a34-99ba-923819df0f59)
- [Case Statements](https://web.compass.lighthouselabs.ca/4c98f324-4a1f-4777-8ad5-c568f92728b8)
- [Window Functions](https://web.compass.lighthouselabs.ca/94eaca00-7d92-49cb-9c87-33c981f05179)

### Load

Loading the cleaned and transformed data into the database is the last stage of the ETL process. Loading data could look like:

1. Inserting new data into an existing table in the database, or
2. Inserting existing data back into the database once it has been cleaned and transformed.

Note

Regardless of the case above, `INSERT INTO` is the sql query used to load data into a database.

### The SQL INSERT INTO Statement

The `INSERT INTO` statement is used to insert new records into a table. New can mean net new data OR data that is “new” because it has been cleaned or transformed.

#### INSERT INTO Syntax

It is possible to write the `INSERT INTO` statement in two ways:

1. Specify both the column names and the values to be inserted: `sql INSERT INTO table_name (column1, column2, column3, ...) VALUES (value1, value2, value3, ...);`
2. If you are adding values for all the columns in the table, you do not need to specify the column names in the SQL query. However, be sure that the order of the values you are inserting matches the order of the columns in the table. Here, the `INSERT INTO` syntax would be as follows:

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

## Conclusion

Be sure to make note of the INSERT INTO query as you will continue to use it throughout the course and in your own database dependent projects! You can also read more about the ETL process in [this documentation by Microsoft](https://docs.microsoft.com/en-us/azure/architecture/data-guide/relational-data/etl).