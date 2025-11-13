An SQL query is composed of multiple **clauses**. Some are mandatory while others are optional.

Instruction

Read this article [Introduction to SQL Query Structure](https://tprojects.schneider-electric.com/GeoSCADAHelp/ClearSCADA%202017%20R2/Content/SQLGuide/IntroductiontoSQLQueryStructure.htm) to familiarize yourself with the anatomy of an SQL query.

Please make sure to read through the four additional sections on the four clauses: `SELECT`, `FROM`, `WHERE`, and `ORDER BY` at the end of the document.

[SELECT Clause](https://tprojects.schneider-electric.com/GeoSCADAHelp/ClearSCADA%202017%20R2/Content/SQLGuide/SELECTClause.htm)

[FROM Clause](https://tprojects.schneider-electric.com/GeoSCADAHelp/ClearSCADA%202017%20R2/Content/SQLGuide/FROMClause.htm)

[WHERE Clause](https://tprojects.schneider-electric.com/GeoSCADAHelp/ClearSCADA%202017%20R2/Content/SQLGuide/WHEREClause.htm)

[ORDER BY Clause](https://tprojects.schneider-electric.com/GeoSCADAHelp/ClearSCADA%202017%20R2/Content/SQLGuide/ORDERBYClause.htm)

You will come back to the **GROUP BY** and **HAVING** later.

## Conclusion

The fundamental structure of SQL queries includes three clauses: SELECT, FROM, and WHERE. SQL statements follow a logical order of operations, similar to how a math equation follows a logical order:

`SELECT`: what columns you want to see/get back in response.

- What you want in the final result is specified in the SELECT clause. In the SELECT clause, you have to specify the attributes that you want to see in the result relation.

`FROM`: where your data is located.

- Which relations you need to access to get the result is specified in the FROM clause. In the FROM clause, you have to specify the list of relations that has to be accessed for evaluating the query.

`WHERE`: how you want to filter your data.

- How the relation must be operated to get the result is specified in the WHERE clause. In the WHERE clause, you filter the attributes of the relations that you have listed in the FROM clause.

![Anatomy of a SQL query](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/2.+SQL+Fundamentals/query_anatomy.PNG)

Anatomy of an SQL query