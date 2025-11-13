In this activity, we are going to learn how to work with databases directly from Python. Specifically, we will work with the SQLite database however we can connect to other databases in a similar way.

For SQLite, there is a special Python package called `sqlite3` that allows us to connect to (or create) any SQLite database on our local machine.

We will be using parts of the content from the article [Introduction to Python SQL Libraries](https://realpython.com/python-sql-libraries/) that was published on realpython.com. We will focus on SQLite for now and we will use our own Jupyter Notebooks to try out the code.

### Connecting to Database

Here's how we use sqlite3 to connect to an SQLite database in Python:

```python
import sqlite3
from sqlite3 import Error

def create_connection(path):
    connection = None
    try:
        connection = sqlite3.connect(path)
        print("Connection to SQLite DB successful")
    except Error as e:
        print(f"The error '{e}' occurred")

    return connection
```

Here’s how this code works:

- Lines 1 and 2 import sqlite3 and the module’s Error class.
- Line 4 defines a function .create_connection() that accepts the path to the SQLite database.
- Line 7 uses .connect() from the sqlite3 module and takes the SQLite database path as a parameter. If the database exists at the specified location, then a connection to the database is established. Otherwise, a new database is created at the specified location, and a connection is established.
- Line 8 prints the status of the successful database connection.
- Line 9 catches any exception that might be thrown if .connect() fails to establish a connection.
- Line 10 displays the error message in the console.

`sqlite3.connect(path)` returns a connection object, which is in turn returned by create_connection(). This connection object can be used to execute queries on an SQLite database. The following script creates a connection to the SQLite database:

```python
connection = create_connection("sm_app.sqlite")
```

Note

The database file will be created automatically if it doesn't exist. If it does the code above will connect Python to the existing database.

### Creating Tables

In the previous section, we saw how to connect to the database server using `sqlite3`. In this section, we'll see how to create tables inside the database.

We'll create four tables:

1. users
2. posts
3. comments
4. likes

To execute queries in SQLite, use `cursor.execute()`. In this section, we'll define a function `execute_query()` that uses this method. Our function will accept the connection object and a query string, which we'll pass to `cursor.execute()`.

`.execute()` can execute any query passed to it in the form of string. We'll use this method to create tables in this section. In the upcoming sections, We'll use this same method to execute update and delete queries as well.

Note

This script should be executed in the same file where we created the connection for the SQLite database.

Here's the function definition:

```python
def execute_query(connection, query):
    cursor = connection.cursor()
    try:
        cursor.execute(query)
        connection.commit()
        print("Query executed successfully")
    except Error as e:
        print(f"The error '{e}' occurred")
```

This code tries to execute the given query and prints an error message if necessary.

Next, let's write our query:

```python
create_users_table = """
CREATE TABLE IF NOT EXISTS users (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL,
  age INTEGER,
  gender TEXT,
  nationality TEXT
);
"""
```

This says to create a table **users** with the following five columns:

1. id
2. name
3. age
4. gender
5. nationality

Finally, we'll call execute_query() to create the table. We'll pass in the connection object that we created in the previous section, along with the `create_users_table` string that contains the create table query:

```python
execute_query(connection, create_users_table)  
```

The following query is used to create the **posts** table:

```python
create_posts_table = """
CREATE TABLE IF NOT EXISTS posts(
  id INTEGER PRIMARY KEY AUTOINCREMENT, 
  title TEXT NOT NULL, 
  description TEXT NOT NULL, 
  user_id INTEGER NOT NULL, 
  FOREIGN KEY (user_id) REFERENCES users (id)
);
"""
```

Since there’s a one-to-many relationship between **users** and **posts**, we can see a foreign key user_id in the **posts** table that references the id column in the **users** table. Execute the following script to create the **posts** table:

```python
execute_query(connection, create_posts_table)
```

Finally, we can create the **comments** and **likes** tables with the following script:

```python
create_comments_table = """
CREATE TABLE IF NOT EXISTS comments (
  id INTEGER PRIMARY KEY AUTOINCREMENT, 
  text TEXT NOT NULL, 
  user_id INTEGER NOT NULL, 
  post_id INTEGER NOT NULL, 
  FOREIGN KEY (user_id) REFERENCES users (id) FOREIGN KEY (post_id) REFERENCES posts (id)
);
"""

create_likes_table = """
CREATE TABLE IF NOT EXISTS likes (
  id INTEGER PRIMARY KEY AUTOINCREMENT, 
  user_id INTEGER NOT NULL, 
  post_id integer NOT NULL, 
  FOREIGN KEY (user_id) REFERENCES users (id) FOREIGN KEY (post_id) REFERENCES posts (id)
);
"""

execute_query(connection, create_comments_table)  
execute_query(connection, create_likes_table) 
```

We can see that creating tables in SQLite is very similar to using raw SQL. All we have to do is store the query in a string variable and then pass that variable to `cursor.execute()`.

### Inserting Records

In this section, we'll see how to insert records into our tables.

To insert records into our SQLite database, we can use the same `execute_query()` function that we used to create tables. Firstly, we have to store our **INSERT INTO** query in a string. Then, we can pass the connection object and query string to `execute_query()`. Let's insert five records into the **users** table:

```python
create_users = """
INSERT INTO
  users (name, age, gender, nationality)
VALUES
  ('James', 25, 'male', 'USA'),
  ('Leila', 32, 'female', 'France'),
  ('Brigitte', 35, 'female', 'England'),
  ('Mike', 40, 'male', 'Denmark'),
  ('Elizabeth', 21, 'female', 'Canada');
"""

execute_query(connection, create_users)   
```

Since we set the **id** column to auto-increment, we don't need to specify the value of the **id** column for these users. The **users** table will auto-populate these five records with id values from 1 to 5.

Now insert six records into the **posts** table:

```python
create_posts = """
INSERT INTO
  posts (title, description, user_id)
VALUES
  ("Happy", "I am feeling very happy today", 1),
  ("Hot Weather", "The weather is very hot today", 2),
  ("Help", "I need some help with my work", 2),
  ("Great News", "I am getting married", 1),
  ("Interesting Game", "It was a fantastic game of tennis", 5),
  ("Party", "Anyone up for a late-night party today?", 3);
"""

execute_query(connection, create_posts)  
```

It's important to mention that the **user_id** column of the **posts** table is a foreign key that references the id column of the **users** table. This means that the **user_id** column must contain a value that already exists in the id column of the **users** table. If it doesn’t exist then we'll get an error.

Similarly, the following script inserts records into the comments and likes tables:

```python
create_comments = """
INSERT INTO
  comments (text, user_id, post_id)
VALUES
  ('Count me in', 1, 6),
  ('What sort of help?', 5, 3),
  ('Congrats buddy', 2, 4),
  ('I was rooting for Nadal though', 4, 5),
  ('Help with your thesis?', 2, 3),
  ('Many congratulations', 5, 4);
"""

create_likes = """
INSERT INTO
  likes (user_id, post_id)
VALUES
  (1, 6),
  (2, 3),
  (1, 5),
  (5, 4),
  (2, 4),
  (4, 2),
  (3, 6);
"""

execute_query(connection, create_comments)
execute_query(connection, create_likes) 
```

In both cases, we store our INSERT INTO query as a string and execute it with `execute_query()`.

### Selecting Records

To select records using SQLite, we can again use `cursor.execute()`. However, after you’ve done this, we'll need to call `.fetchall()`. This method returns a list of tuples where each tuple is mapped to the corresponding row in the retrieved records.

To simplify the process, we can create a function `execute_read_query()`:

```python
def execute_read_query(connection, query):
    cursor = connection.cursor()
    result = None
    try:
        cursor.execute(query)
        result = cursor.fetchall()
        return result
    except Error as e:
        print(f"The error '{e}' occurred")
```

This function accepts the _connection_ object and the SELECT query and returns the selected records.

Let’s now select all the records from the **users** table:

```python
select_users = "SELECT * from users"
users = execute_read_query(connection, select_users)

for user in users:
    print(user)
```

In the above script, the SELECT query selects all the users from the **users** table. This is passed to the `execute_read_query()`, which returns all the records from the **users** table. The records are then traversed and printed to the console.

Note

It's not recommended to use SELECT * on large tables since it can result in a large number of `I/O` operations that increase the network traffic.

We did focus on more complex SQL queries already so we are not going to show it here. However, we can run _ANY_ select statement in the same way, including

- joins
- subqueries
- filtering
- aggregate functions
- ...

### Updating Table Records

Updating records in SQLite is pretty straightforward. We can again make use of `execute_query()`. As an example, we can update the description of the post with an id of 2. The following script updates the description:

```python
update_post_description = """
UPDATE
  posts
SET
  description = "The weather has become pleasant now"
WHERE
  id = 2
"""

execute_query(connection, update_post_description)
```

### Deleting Table Records

We can again use `execute_query()` to delete records from YOUR SQLite database. All we have to do is pass the connection object and the string query for the record you want to delete to `execute_query()`. Then, `execute_query()` will create a cursor object using the connection and pass the string query to `cursor.execute()`, which will delete the records.

As an example, let's try to delete the comment with an id of 5:

```python
delete_comment = "DELETE FROM comments WHERE id = 5"
execute_query(connection, delete_comment)
```

Now, when we select all the records from the comments table, we'll see that the fifth comment has been deleted.

## Conclusion

We have seen how to work with SQLite databases from the Python interface. `sqlite3` is a special package that connects to any SQLite database. Other database types have other packages with pre-build drivers therefore we can't use `sqlite3` to connect to those.

The important thing is we can follow a similar workflow to connect to any other database when we have the correct Python library.

- `mysql-connector-python` for MySQL
- `psycopg2` for Postgres
- `SQLAlchemy` - generic library which using JDBC to connect to different DBs.