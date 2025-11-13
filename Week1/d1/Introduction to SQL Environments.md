## SQL Environments

### What is an Environment?

A software development environment (SDE) is the collection of hardware and software tools a system developer uses to build software systems.

When you are developing software, you probably don’t want your users to see every messy part of your application creation process. In order to make sure you control what people see and when they have access to it, development teams use environments to create “stages” of the app which they consider good for releasing.

Just like developing software requires an environment, so does working with databases. This particular environment can be referred to as an SQL environment. A few things to make note of when it comes to SQL environments:

- Each SQL environment has its own unique purpose.
- There are different standards of environments which are used in the industry.
- Different organizations all have their own purposes and policies which dictate when and how each environment is used.

In a learning environment, you could work with SQL in a web browser. These environments are pre-prepared for you and for your learning purposes. However, you can also work with SQL directly from your machine.

The exact SQL environment you will use in your daily professional life will depend on the flavour of SQL you choose, and the flavour of SQL is often driven by the company as well as the project’s needs.

As for programming, there are different development environments for SQL databases. SQL is the query language used for managing data in relational databases. But it is important to know that there are several different flavours of SQL, often linked to the specific database system being used. A few examples are:

- MySQL Workbench for MySQL databases
- [PGAdmin](https://www.pgadmin.org/) for Postgres databases
- SQLite Studio for SQLite database

### Different Flavours of SQL

The nuances of the database you are working with will determine how you communicate with it (i.e., what flavour of SQL you will have to use).

Some of the most popular databases are listed below. The name of each database is also the name of the flavour of SQL used to communicate with it.

#### Oracle

Oracle database is robust and durable, and it is commonly used in time-critical businesses which require the strongest ACIDity and the guarantees that come with that.

Some of the unique features of Oracle databases are:

- Extremely strong ACID compliance, high reliability, high durability, and resiliency. If you are interested in what it means to be ACID compliant, take a read through [this article on the ACID database model by Lifewire](https://www.lifewire.com/the-acid-model-1019731).
- Great support for hierarchical queries with CONNECT BY ... LEVEL.
- Full support of analytical and window functions for the longest time.

Oracle is the definition of closed-source. The licensing cost could kill a small company. Every business cannot afford proprietary databases like Oracle and SQL Server, which is one reason why free open-source options like MySQL and PostgreSQL have become more popular over the years.

#### SQL Server

SQL Server (from Microsoft) has similar features and levels of ACID support, etc., just like Oracle. But similar to Oracle, it is also costly for many companies.

Some of the unique features of SQL Server are:

- Support for T-SQL (Microsoft’s own procedural)
- Advanced query statistics using Query Store for optimizing database and query performance
- Full support for analytic and window functions

#### MySQL

For a long time, MySQL did not support analytic and window functions, and only has support for basic aggregations using ‘GROUP BY.’ Now, however, MySQL is more capable, but still has limitations when performing SQL joins.

Some of the features unique to MySQL are:

- Support for native complex replication topologies
- Session and global variables to emulate analytic functions and PL/SQL functionality
- Storage engines (not many databases support these many storage engines)

#### PostgreSQL

PostgreSQL is commonly known as the programmer’s database, and it has established itself as a real competitor to MySQL in the open-source space with native support for advanced abstract data structures like arrays.

Some of the features that make PostgreSQL unique are:

- It is extensible–you can add extensions to the database to enhance its functionality. A very popular extension to PostgreSQL is PostGIS, which is a library for doing geospatial SQL queries.
- Extensive support for abstract data types, especially helpful to match usual data types in an application programming language.
- Unlike MySQL, PostgreSQL does extend itself to include a procedural language PL/pgSQL, similar to Oracle’s PL/SQL.

These are the four main SQL flavours and relational databases. In this course, you will use PostgreSQL.

## Conclusion

As you have discovered, there are a variety of SQL databases available to work with, and each database will dictate the flavour of SQL you will need to use. Sometimes you will have the ability to choose your environment setup, and sometimes it will be predetermined. Being aware of the nuances of each SQL flavour will allow you to adapt on a project-by-project basis, adding more tools to your data toolbelt.

---