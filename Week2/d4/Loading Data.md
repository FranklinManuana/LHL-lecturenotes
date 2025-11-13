For this activity, we will continue using the Northwind database. In previous activities, you built several SQL queries for extracting and transforming the data. Now, we will focus on the queries that will load the data back into a new PostgreSQL table.

Go to the pgadmin app, open the Northwind database, and follow the steps below:

#### Step 1: Create a general template for creating a table

```sql
CREATE TABLE public.temp
(
    categoryid smallint NOT NULL,
    categoryname character varying NOT NULL,
    description character varying NOT NULL,
    picture bytea,
    PRIMARY KEY (categoryid)
);

ALTER TABLE IF EXISTS public.temp
    OWNER to postgres;
```

#### Step 2: Use this to insert data into the created table

```sql
INSERT INTO temp
SELECT * FROM categories;

```

#### Step 3: Validate data in the new table

```sql
SELECT * FROM temp
```

Note

This action of creating the temp table might seem redundant, however, in your ongoing interactions with SQL databases, this is the process you will follow to push your data back into the database, and it will save you a lot of headaches! Get into the habit now, and your future self will thank you. In practice, the scenario may be more complex, but once you are satisfied with your data transformations, this is the syntax you will use to push that newly transformed data back into the database.