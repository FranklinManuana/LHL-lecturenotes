## Introduction to PostgreSQL

PostgreSQL is sometimes affectionately known as the developers’ database. It is a good choice for a database because it’s free, open-source, highly customizable, has regular releases, and has many useful features for developers. In addition, several companies offer cloud-hosted PostgreSQL databases that can be used for practice.

The first question that needs to be answered is, what is the difference between PostgreSQL and other databases?

Instruction

Read this [introduction on PostgreSQL by PostgreSQL Tutorial](https://www.postgresqltutorial.com/postgresql-getting-started/what-is-postgresql/).

### Some Key Characteristics of PostgreSQL

#### Free, Open-Sourced with Good Documentation

PostgreSQL is open-source. This means the source code is available online and can be changed by anyone. It follows a Git source control model, meaning there is a process to ensure it’s not corrupted or broken by anyone.

#### Runs on Many OSs

Many databases run on some, but not all, OSs. PostgreSQL runs on a wide range of OSs, including:

- BSD (FreeBSD, OpenBSD)
- Linux (Red Hat family, Debian, Ubuntu, SuSE, and others)
- macOS
- Solaris
- Windows

#### Comprehensive Functionality

PostgreSQL includes many data types for working with and storing data, and allows developers to define custom data types. This means that if you can’t store what you need using one of the built-in data types, you can create your own.

#### Great JSON Support

Many databases either focus on storing relational data in tables or document data as JSON. MongoDB, for example, is a document database, whereas MySQL is a relational database. PostgreSQL can do both.

#### Compliant to SQL Standards

Being compliant to SQL standards mean that PostgreSQL shares the standard SQL features. This makes it easy to migrate to and from PostgreSQL if needed.

#### Window Functions

Window functions in SQL are one of the most underrated and unknown features. They are supported in Oracle, and SQL Server has a partial implementation of them. PostgreSQL supports them too.

#### Common Table Expressions

Common Table Expressions is a feature that lets you simplify your queries. If you have a large query with subqueries inside it, you can define the subqueries with a name, and use that name in your main query. This can improve query readability, which helps you to debug. And it also helps with query performance.

#### Custom Languages and Functions Inside the Database

If the PostgreSQL built-in functions are not enough, you can create your own.

You can also use other languages in PostgreSQL such as Python, Ruby, and R. This is a great feature if you’re familiar with those languages and want to include them.

#### Regular Releases

Although the PostgreSQL is open-source, there are still releases which offer stable versions of the database.

A major release is targeted once per year. Several minor releases are made to the database to fix any bugs or security issues.

#### Cloud-Hosted PostgreSQL

Google Cloud, Amazon AWS, and Microsoft Azure all offer cloud-hosted PostgreSQL databases. This makes it easy to set up a database for your application, rather than deploying it on your own server.

## Conclusion

As you work on data projects, you may be given the freedom to choose your SQL flavour, or it might be predetermined for you. In either case, knowing the benefits and limitations of the flavour you are working with will allow you to maximize what you are able to accomplish.