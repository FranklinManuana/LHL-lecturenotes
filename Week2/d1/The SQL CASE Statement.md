
The `CASE` statement is SQL's way of handling if/then logic. The `CASE` statement is followed by at least one pair of `WHEN` and `THEN` statements — SQL's equivalent of IF/THEN in Excel. Because of this pairing, you might be tempted to call this SQL `CASE WHEN`, but `CASE` is the accepted term.

Every `CASE` statement must end with an `END` statement. The `ELSE` statement is optional and provides a way to capture values not specified in the `WHEN`/`THEN` statements.

The `CASE` statement goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the `ELSE` clause.

If there is no `ELSE` part and no conditions are true, it returns NULL.

### CASE Syntax

```sql
SELECT column_1, column_2,
CASE
WHEN condition1 THEN result1
WHEN condition2 THEN result2
WHEN conditionN THEN resultN
ELSE result
END AS column_3
FROM table
```

### An Example

`CASE` is easiest to understand in the context of an example. Let’s use the Northwind database again.

Instruction

Use the Northwind database and follow the steps below to practice writing `CASE` statements.

#### Step 1: Retrieve some of the data and try to understand it

```sql
SELECT * FROM employees
LIMIT 100
```

View the value of `birthdate` and `hiredate`. Make sure that these datetime values make sense.

#### Step 2: Identify missing values and extreme values.

```sql
SELECT city, region FROM employees
GROUP BY city, region
```

We see where the `city` is London, the `region` has missing values.

Can we fill in the `region` value of London?

#### Step 3: Use CASE statements to fill in missing values of `region`

We should find out more facts about these employees. If we are sure that they are indeed based in London, UK, then we can fill in the missing values as follows:

```sql
SELECT employeeid, lastname, firstname, title, birthdate, hiredate, city,
CASE WHEN region IS NOT NULL THEN region
WHEN city = 'London' THEN 'UK' END AS region
FROM employees
```

In plain English, here's what's happening:

1. The `CASE` statement checks each row to see if the conditional statement — `region is not null` is true.
2. For any given row, if that conditional statement is true, then the original value of `region` gets printed in the column that we have named `region`.
3. In any row for which the conditional statement is false (which means that `region` is null), then we will fill the null value in the `region` column.

Note

**Adding multiple conditions to a CASE statement**

You can also define a number of outcomes in a `CASE` statement by including as many `WHEN`/`THEN` statements as you'd like.