In this activity, we will connect to a Postgres database that is running in the cloud. We will use it to practice connections from IDE and Python.

### Postgres Database

Our database is running in the cloud and we can connect to it from any IDE (we will use VSCode again in this activity) with the following credentials:

- host: `lhl-data-bootcamp.crzjul5qln0e.ca-central-1.rds.amazonaws.com`
- user: `lhl_student`
- pwd: `lhl_student`
- port: `5432`
- database: `northwind`

### Using VSCode to Connect to Postgres Database

In the picture below, we have the first two steps we need to start with:

![](https://i.postimg.cc/MGqJHg4N/Screenshot-2021-02-17-at-11-21-11.png) 1. Click on the **Extensions** icon in the left panel.  
2. Search for a correct Postgres extension and install it. We will work with **PostgreSQL Management Tool** from Chris Kolkman. Once installed you will see the Postgres icon in the left panel.  
![](https://i.postimg.cc/ZYpkPbS2/Screenshot-2021-02-26-at-12-46-01.png) 3. Click on the plus sign and add a new connection to the database. Follow the steps in the command prompt and fill in the required info about your Postgres database.  

Note

You will be prompted to select a standard or secured connection. In this case, select standard. Secure connections encrypt communications between the database server and the querying computer, and are appropriate for sensitive data or code. The server needs to be configured to be able to handle this kind of connection, and database documentation/ administrators will generally provide guidance on required connection type when working in industry.

1. When the connection is created, create a new plain text file and perform the following steps:

- In the lower right hand corner, click on the language mode (currently `Plain Text`), scroll through the menu to find `Postgres`
- On the lower left, click `Select Postgres Server`, which will then display a menu of your configured connections. Select the one you just created.
- You will then be prompted to select a specific database on this server. Select `northwind`.  
    Once configured, you should see something like this: ![](https://learningimages.lighthouselabs.ca/Data%20BC/Statistical%20Modelling%20in%20Python/PostgresInVSCODE.png)  
    

Warning

When running Postgres queries in VScode, the file extension of your query file should be `.psql` not `.sql`. We did this by selecting language mode `Postgres` above, but when selecting language mode `SQL` (`.sql` file), your computer may default to `SQLite` (which will prompt you to select a local `.db` file as we saw before), or it may provide two different `Run Query` options for `SQLite` and `Postgres`. To be safe, use a `.psql` file when intending to use PostgreSQL on VSCode.

Instruction

Test your connection by querying `orders`. Write the following code in your `.psql` file, right-click on it, and select `Run Query`.

```sql
SELECT * FROM orders LIMIT 10;
```

Note

In VSCode, the code is executed by right-clicking the query and choosing `Run Query`. However, this can get tedious, and it is often preferrable to set up a keybinding (like how you may have been using `Shift+Enter` to run Jupyter Notebook cells). This is optional, but you can set up different keyboard shortcuts for each database type by following [this guide](https://code.visualstudio.com/docs/getstarted/keybindings). For example:

- run SQLite query by `cmd+r` (`ctrl` on windows)
- run Postgres query by `cmd+e` (`ctrl` on windows).

## Conclusion

Now that we have connected to the Postgres database in the cloud, we can use it for additional `SQL` practice.