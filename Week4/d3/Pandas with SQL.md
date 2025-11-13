In this hands-on activity, we'll practice working with databases with Pandas. We will also review how to connect to `SQLite` with the `sqlite3` module and try the same process with `SQLAlchemy.` Let's dive straight into it!

First, let's import the necessary libraries:

```python
import sqlite3 as sqlite

import pandas as pd

from sqlalchemy import create_engine
```

Note

If you haven't installed `SQLAlchemy` before, please install it with the well-known approach with pip or conda.

For demonstration purposes, we'll create a database, `population.db`, and insert one table with the name, `Population`, which represents the population in different countries.

```python
with sqlite.connect('population.db') as con:
    cur = con.cursor()    
    cur.execute("CREATE TABLE IF NOT EXISTS Population(id INTEGER PRIMARY KEY, country TEXT, population INT)")
    cur.execute("INSERT INTO Population VALUES(NULL,'Germany',81197537)")
    cur.execute("INSERT INTO Population VALUES(NULL,'France', 66415161)")
    cur.execute("INSERT INTO Population VALUES(NULL,'Spain', 46439864)")
    cur.execute("INSERT INTO Population VALUES(NULL,'Italy', 60795612)")
    cur.execute("INSERT INTO Population VALUES(NULL,'Spain', 46439864)")

```

### Creating Connection with SQLAlchemy

We have already learned how to make a connection to the `SQLite` database with the `sqlite3` module. Another option is, to connect to the `SQLite` (or any other supported databases) database using `SQLAlchemy`. This type of connection is also recommended by Pandas.

Let's create a connection with `SQLAlchemy`.

```python
connection = create_engine('sqlite:///population.db')
```

The syntax is as simple as that. The only required parameter in the `create_engine` function is a connection string. This connection string consists of the name of the database driver and the name of the database we want to connect.

Warning

For this connection string to work, `population.db` needs to be in the same directory as our notebook. If we choose a different directory, we then need to adjust the string accordingly.

### Reading SQL data with Pandas

Pandas allows us to query `SQL` tables with three methods:

- `read_sql_query()`
- `read_sql_table()`
- `read_sql()`

For each of these methods, we'll need our database connection, which we defined as a variable above `connection = create_engine('sqlite:///population.db')`

We'll now explain each of these three methods:

#### 1) `read_sql_query()`

This method requires two parameters as input. The first parameter is a string with a SQL query and the second one is a connection to the database. Let's try to read all the rows from our `Population` table.

```python
# create SQL query
sql = 'SELECT * FROM Population'

df = pd.read_sql_query(sql, connection)
df
```

As we can see from code above, we loaded data from the database into the data-frame with only a few lines of code.

#### 2) `read_sql_table()`

Another way to load data from the database and into the data-frame is the `read_sql_table()` method. Compared to the `read_sql_query()` method, the first argument is the table name instead of the SQL query. The second argument stays the same.

```python
# table name
table = 'Population'

df = pd.read_sql_table(table, connection)
df
```

#### 3) `read_sql()`

This function is a combination of the two mentioned above. Depending on the type of the first argument (SQL query or table name), this function internally calls `read_sql_query()` instead of `read_sql_table()`.

So we can use it both ways:

- with SQL query:

```python
# create SQL query
sql = 'SELECT * FROM Population'

df = pd.read_sql(sql, connection)
df
```

- with table name:

```python
# table name
table = 'Population'

df = pd.read_sql(table, connection)
df
```

#### Closing the Connection

When you're done working with your database connection, be sure to close it:

```python
connection.close()
```

This releases any computational resources allocated to the connection and prevents resource leaks. This is especially important when working with a shared database as leaving connections open can cause limited resources to be available for others' queries, slowing down processing speeds.

It is best practice to always close your connections when you are done with them. You can easily re-open with the same connection creation syntax we used above.