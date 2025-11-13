## Introduction to Relational Databases

This activity is a quick primer to relational databases and the various things you have to know when working with them, including structured query language (SQL).

Instruction

Read the article [Relational Databases for Dummies](http://code.tutsplus.com/tutorials/relational-databases-for-dummies--net-30244) to get a good introduction to RDBMSs.

Note

The article mentions that MySQL is used at just about every company. Even though, for example, Facebook uses MySQL, it's a bit of an overstatement. More importantly though, MySQL is a vendor of RDBMSs. All SQL database systems support the same fundamental SQL syntax, which is the more important thing to learn here. Each vendor, indeed, has their own nuances and custom features but these are not going to be your focus for now, as they are not necessary for being a generalist data scientist.

### Summary of Key Takeaways

- A database stores data in an organized way so that it can be searched and retrieved later.
- A table is much like a spreadsheet, in that it's made up of rows and columns. All rows have the same columns, and each column contains the data itself.
- A relational database is a type of database that organizes data into tables, and links them, based on defined relationships. These relationships enable you to retrieve and combine data from one or more tables with a single query.
- Before data can be sent to the database, it should be cleaned and normalized so that it is suited for the database.
- Normalization is needed so that when you connect your tables you don’t have duplicates. Duplicates are problematic because it makes CRUD (create, read, update, delete) operations more challenging. For example, it would take longer to retrieve data because time would be wasted going through duplicate rows.
- Repetitive data is a problem. You can fix this problem by splitting a table into separate tables. This step of removing repetitive data across columns is referred to as the first normal form (1NF).
- The step of removing repetitive data across rows is referred to as the second normal form (2NF).
- Once repetitive data has been removed, the data you need may be found in different tables. In order to have useful data, you need to draw meaningful links between the tables.
- The way to draw links between tables is to first give each row in a table a unique identifier, known as a primary key, and then reference that primary key in the other table to which you want to link.

## Conclusion

In a relational database, you can define complex relationships between tables, and you can access the relations directly. In contrast, a hierarchical or network database is often designed for a specific application. These two database types are considered legacy solutions. Relational databases have become the most common data storage mechanism, and SQL is the most common way to communicate with them. SQL (commonly pronounced 'S-Q-L' or 'sequel') is a powerful programming language that can add, delete, extract, or operate on information within a relational database. You can even use SQL to perform complicated analytical functions and change the structure of the database itself–adding or deleting tables, for instance. You will explore the power of SQL throughout this course.