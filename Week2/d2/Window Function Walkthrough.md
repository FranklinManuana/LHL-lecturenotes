In this activity, we will be using the connection to the `window_functions_test_db` database to practice using window functions.

Instruction

Connect the database to your IDE by following the steps below.

1. Open pgAdmin
2. Right-click on Servers --> Register --> Server
3. In the General tab, give this server a name (`AWS_postgres_DB`)
4. In the Connection tab, enter the following:

- Host name/address: lhl-data-bootcamp.crzjul5qln0e.ca-central-1.rds.amazonaws.com
    
- Port: 5432
    
- Username: lhl_student
    
- Password: lhl_student
    
- Leave everything else as default
    
- Click save
    

1. You should now see the server appear on the left-side under Servers.
2. Navigate to the window_functions_test_db database and open the query tool.

Instruction

Follow the [PostgreSQL Window Functions tutorial](https://www.postgresqltutorial.com/postgresql-window-function/). Start the tutorial at the heading **_Introduction to PostgreSQL window functions_** because the tables we need have already been created in the schema `training`.

Example query:

```sql
SELECT * FROM training.products;
```