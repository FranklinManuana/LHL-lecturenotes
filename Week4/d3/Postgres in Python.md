In this activity, we will show how to connect Postgres to Python.

Instruction

Follow [**this article**](https://stackabuse.com/working-with-postgresql-in-python/) to learn the basics of how to connect Postgres to Python and go over some simple operations.

Note

There are two things we need to point out from the article:

1. There is no need to install the package using `pip3`. We can simply install it with `pip` or `conda` even when we use Python3.
    
2. And our connection details to Northwind database will look like this (we have previously setup this database locally):
    

- `database`: northwind
- `host`: 127.0.0.1
- `port`: 5432
- `user`: postgres
- `password`: <your password>

## Conclusion

Now that we have explored working with Postgres in Python, it is clear that there are huge similarities to SQLite.

The truth is, working with different databases in Python is very similar. The main difference is the package we are using to create the connection, and the context in which each database is most appropriately used.

SQLite is great for working on locally stored database files. Its lightweight and requires almost no setup. Remember pretty much all we had to do was select the `.db` file we wanted to query. However, its not very scalable, and doesn't support concurrent access, which is essential in industry applications.

PostgreSQL requires a bit more set-up, and takes up more space on your computer. However, it supports connection to remote databases, supports multiple concurrent users, and is much more scalable.

Overall, SQLite is great for personal projects, while PostgreSQL is more suited for industry application, but both can be easily used in VSCode and used alongside Python/ Pandas. It's important to note as well that SQLite and PostgreSQL are slightly different 'flavours' of SQL, with some minor syntax differences. Your queries may not always translate 1:1, but the vast majority of things will be the same.