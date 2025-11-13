Developing a quality assurance process takes practice and experience. While there are no universal solutions to conducting QA on your data, there are guidelines you can follow. Identifying your risk areas (i.e. how the SQL queries could go wrong) will help guide you in developing your own QA process.

Instruction

Read the following article to dive into how to develop quality assurance processes when interacting with data.

- [SQL Quality Assurance Queries](https://drive.google.com/file/d/16xMdqgr7OnjKYpi3KCclc9sIVXoj4kpm/view?usp=drive_link) by Zach Quinn

Next, read the following guide on using assertion statements to perform data QA

### Assertions for Data QA

A data assertion is a type of query that looks to identify problems in a dataset. It is not a query designed to retrieve specific information, but instead to find entries where information may be missing or incorrect. The intention is that an assertion will return ZERO ROWS if the data is clean, or return one or more 'failing' rows if it is not.

For example, in the Northwind database, we might be concerned with how many orders come from each region (`orders.shipregion`), and for our analysis we want to make sure that every order is associated with a region.

We could easily check this with the following query:

```sql
SELECT *
FROM orders
WHERE shipregion IS NULL;
```

This query looks for rows where `shipregion` is missing (`NULL`) and returns them. There are 507, so this assertion 'fails'.

Alternatively, if we wanted to ensure that every order has an associated address we could run:

```sql
SELECT *
FROM orders
WHERE shipaddress IS NULL;
```

This query returns no rows, so this assertion passes.

Assertions are a great way to quickly inspect data - allowing us to easily diagnose and fix problems in our other queries.

### More Assertions

Remember there are more ways data can be dirty than just unwanted `NULL`s! Data could have:

- Improper characters (i.e. special chars in names)
- Incorrect formatting (i.e. phone number `xxx-xxx-xxxx` vs `xxxxxxxxxx`)
- Non null missing values (i.e. `"enter name here"`)
- Impossible/ Outlier values (i.e. `age` < 0, `age` > 120, etc.)
- Misaligned values (i.e. listed `age` and `birthdate` don't match)
- Duplicated rows (i.e. two people with same `first name`/ `last name` - possible in real life but might be an issue for some queries)
- And many, many more!

In all of these cases, we could write assertion statements to check our data before we proceed with our other analyses.

For example, in the `employees` table, we might want to check to ensure that all home phone numbers follow the expected format - say "(xxx) xxx-xxxx":

```sql
SELECT * 
FROM employees 
WHERE homephone !~ '\(\d{3}\) \d{3}-\d{4}';
```

The regex pattern `\(\d{3}\) \d{3}-\d{4}` indicates a `(`, 3 digits, `)`, a space, 3 digits, a `-`, then 4 digits, which is the desired format. Using `!~` will return values where this pattern is NOT matched. Running this, we see that some numbers do not follow this pattern - they have a two digit area code.

We might also want to check if any phone numbers are duplicated. To do this we could run the following:

```sql
SELECT homephone, COUNT(*)
FROM employees
GROUP BY homephone
HAVING COUNT(*) > 1;
```

In this case, we are grouping by the value of `homephone`, and filtering for `COUNT(*) > 1`. For unique phone numbers, the count will be 1, so this will only return phone numbers that exist in more than one row. There are no duplicated numbers, so this assertion passes.

We can also use set operators to run multiple assertions at once. If we wanted to perform multiple checks on the `homephone` column at once, we could use `UNION ALL`, and slightly adjust the columns we are returning in `SELECT`:

```sql
SELECT homephone, 'Incorrect Format' AS reason
FROM employees 
WHERE homephone !~ '\(\d{3}\) \d{3}-\d{4}'

UNION ALL

SELECT homephone, 'Duplicated' AS reason 
FROM employees
GROUP BY homephone
HAVING COUNT(*) > 1; 
```

This would return two columns, the `homephone` value, and the `reason` it fails. Running this, we see incorrectly formatted phone numbers with `Incorrect Format` in the `reason` column, and no numbers with `Duplicated` in the `reason` column, because they're all unique.

### Creating Clean Data

Our assert statements provide guidance to our data cleaning efforts by helping us identify the issues to tackle. For example, lets return to our previous example looking at whether `shipregion` is `NULL` in the `orders` table.

Filling in missing data can be a complicated process, and often requires an understanding of how the data was generated, which is part of why domain knowledge and experience with a particular database can be so valuable. For example, if a value of `shipregion` is `NULL`, is that because it belongs to a region that already exists in our table, but the label is missing? Or because it belongs to some new region we don't have a label for yet? We don't know for sure, and in a real-life context, you might need to do some digging.

However, we can make our best guess:

```sql
SELECT shipregion, COUNT(*) 
FROM orders 
GROUP BY shipregion 
ORDER BY COUNT(*) DESC;
```

Running this query, we can see that the vast majority of orders are missing `shipregion`, and we have 19 existing values for `shipregion`. 19 is not a lot, especially since these seem to cover regions across many countries (i.e. American States, British Counties, Brazilian Cities, Canadian Provinces, etc.). These regions might be special for business/shipping purposes, and so received a value in `shipregion`. It therefore might be reasonable to replace all of the `NULL` values with `'Other'` - indicating a region other than the 19 we already have.

If we want use a version of this column with the `NULL` values replaced we can use `COALESCE`. For each row in `shipregion`, this will retain the value of any non `NULL`, but replace `NULL`s with a value of our choice, in this case, `'OTHER'`.

```sql
SELECT COALESCE(shipregion, 'OTHER') AS shipregion 
FROM orders
```

Or, if you want to make a permanent change to your database, you can update the table:

```sql
UPDATE orders
SET shipregion = COALESCE(shipregion, 'OTHER');
```

But be sure this is the right call for ALL database users before you do this, as this will affect the database for everyone!

Warning

Running this in pgAdmin will permanently affect the version of Northwind stored on your computer, which _may_ affect your future queries and lead to unexpected results. If you want to reverse this change you can run: `sql UPDATE orders SET shipregion = NULL WHERE shipregion = 'OTHER';`

### Assertions, Pipelines and Continuous Testing

Assertions aren't just important to help us understand data during querying and exploration. They are also an essential tool used by Data Engineers to ensure new data is correctly ingested into the database. They act as warning signals on automated data intake pipelines - whenever an assertion fails and an invalid row is returned, future steps in the pipeline should be set up to halt, and a notification sent to the maintainer. They can be set up to be run every time a new batch of data is ingested, or periodically at regular intervals.

These assertions are an essential step to ensure the integrity of the database, making downstream data operations by analysts and data scientists much smoother.