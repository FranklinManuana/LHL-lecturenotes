Working with the Northwind database, let's look at the `orders` table where we have order dates and shipping dates for each order. Let's say that we want a function that will take those two dates and compare the difference to a threshold number of days then return a string to tell us if the shipment was sent late. Since the `order_date` and `shipped_date` columns are `date` type, their difference will simply be an `integer` type specifying the number of days difference in the dates. We'll have our function output `late` or `on time` depending on if the difference in shipped date and order date is greater than some limit.

First, let's list out our desired inputs:

|Input|Type|
|---|---|
|order date|`date`|
|ship date|`date`|
|threshold|`int`|

> Where "threshold" refers to the number of days passed between order date and shipping date after which we say the shipment was sent late.
> 
> We know from previous experience that we can tackle the kind of logic we want by using a `CASE` statement inside a `SELECT` statement as follow:

```sql
SELECT
CASE
    WHEN shipped_date - order_date > 5 THEN 'late'
    ELSE 'on time'
END AS is_late
FROM orders
```

> Here we have the `CASE` statement by default return whatever value is after the `THEN` or `ELSE` commands, and we use the `AS` command to give the result the name `is_late`.
> 
> When we use a `CASE` statement inside a function, we need to use slightly different syntax as we can see below (just for the `CASE` statement):

```sql
CASE
    WHEN shipped_date - order_date > 5 THEN is_late = 'late';
    ELSE is_late = 'on time';
END CASE;
```

Note

Note here that we need to specify `is_late =` after the `THEN` and `ELSE` commands instead of just providing the result (and we no longer use the `AS` command afterwards). We also use `END CASE` instead of simply `END`. Also note the use of semicolons, without which we would have errors when trying to run the query and create the function.

Since we're using the variable `is_late` to store the result, we'll need to declare it within the function. Let's also define a variable `lead_time` to store the difference in dates instead of including the calculation directly inside the `CASE` statement.

```sql
DECLARE
    is_late varchar;
    lead_time int;
```

> Our function header needs a name and list of inputs as well as the return type defined. Since we're returning a string `late` or `on time` the return type is `varchar`.

```sql
CREATE OR REPLACE FUNCTION LateShipment(date_ordered date, date_shipped date, lead_time_limit int)
RETURNS varchar
```

> The function body will then include the calculation of `lead_time`, the `CASE` statement, and a `RETURN` command to return the value of `is_late`.

```sql
BEGIN
    lead_time = date_shipped - date_ordered;
    CASE
        WHEN lead_time > lead_time_limit THEN is_late = 'late';
        ELSE is_late = 'on time';
    END CASE;
    RETURN is_late;
END
```

> Finally, we put it all together with the necessary syntax between the blocks of code we've already defined.

```sql
CREATE OR REPLACE FUNCTION LateShipment(date_ordered date, date_shipped date, lead_time_limit int)
RETURNS varchar
AS
$$
DECLARE
    is_late varchar;
    lead_time int;
BEGIN
    lead_time = date_shipped - date_ordered;
    CASE
        WHEN lead_time > lead_time_limit THEN is_late = 'late';
        ELSE is_late = 'on time';
    END CASE;
    RETURN is_late;
END
$$
LANGUAGE PLPGSQL
```