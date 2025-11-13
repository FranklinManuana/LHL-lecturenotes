So far we have worked with SQLite3 and psycopg2 and these are Python libraries for specific databases.

However, there are also well-known Python packages that can connect to most types of databases using ODBC or JDBC drivers, such as:

- SQLAlchemy
- pyodbc
- Turbodbc

Let’s take a quick look at them.

### SQLAlchemy

`SQLAlchemy` is a popular SQL toolkit and Object Relational Mapper. It's written in Python and it gives the full power and flexibility of SQL to an application developer. It is open-source and cross-platform software released under an MIT license. SQLAlchemy is famous for its object-relational mapper (ORM). Its classes can be mapped to the database, thereby allowing the object model and database schema to develop in a cleanly decoupled way right from the beginning.

Note

When you decide to use `SQLAlchemy` with ORM [this](https://www.tutorialspoint.com/sqlalchemy/index.htm) tutorial could be handy for you.

### Pyodbc

Pyodbc is an open-source Python module that makes accessing ODBC databases simple. It implements the DB API 2.0 specification but is packed with even more Pythonic convenience.

The easiest way to install it is to use conda or pip:

```python
conda install pyodbc
```

Note

When you decide to use pyodbc to access your database, read [this](https://github.com/mkleehammer/pyodbc/wiki) documentation first.

### Turbodbc

Turbodbc is a Python module to access relational databases via the Open Database Connectivity (ODBC) interface. Its primary target audience is data scientists that pull and insert huge amounts of data from and into the database.

For maximum compatibility, `turbodbc` complies with the Python Database API Specification 2.0 (PEP 249). For maximum performance, `turbodbc` offers built-in NumPy and Apache Arrow support and internally relies on batched data transfer instead of single-record communication as other popular ODBC modules do.

Turbodbc is free to use (MIT license), open-source (GitHub), works with Python 2.7 and Python 3.5+ and is available for Linux, OSX, and Windows.

Turbodbc is routinely tested with MySQL, PostgreSQL, EXASOL, and MSSQL, but also works with other databases

Note

When you decide to use turbodbc to access your database, read [these](https://turbodbc.readthedocs.io/en/latest/pages/getting_started.html) instructions first.

#### Which one to choose?

If it's possible in your application and your database supports it, we should try `turbodbc`. Manipulating and transfering big data with `turbodbc` is much faster.