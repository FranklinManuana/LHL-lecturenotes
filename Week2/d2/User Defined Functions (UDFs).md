## User-Defined Functions

We've used a number of different functions for things like computing average of a set of data, converting from one type to another, and so on. But what if we want to make a custom function that doesn't otherwise exist? We can do that using what we call _user-defined functions_.

### What Is A Function?

You may have heard the word _function_ in a math course where it defines a specific equation that takes inputs and returns an output (along with some other properties and conditions). A function in the context of programming is very similar -- it is a process that takes a set of inputs and returns one or more outputs. Functions can be short and simple or long and complex. In fact, you can think of an entire program as one big function. We see built-in functions for SQL such as `AVG()` or `CONVERT()`, but in this activity we'll be talking about customized functions.

### Basic Structure And Syntax

A user-defined function in SQL can be created using a query which then adds it to your database and makes it available for future use (i.e., you only need to run a query to create a function once -- after that it will then be stored in the database and available for use). The overall structure of a user-defined function looks like this:

```sql
CREATE FUNCTION <name>(<input1> <type1>, <input2> <type2>, ...)
AS
$$
BEGIN
    <function code>
END
$$
LANGUAGE PLPGSQL
```

- We can see that we start with the commands `CREATE FUNCTION` and then we include the name for our function in place of `<name>` followed by parentheses in-which we have the list of input parameters and their types, each separate by commas.
    
- After that we use the command `AS` followed by the function code in-between commands `BEGIN` and `END`.
    
- Note that the function will actually be treated as a string and this is why we have the `$$` (_dollar quotes_) before the `BEGIN` and after the `END` commands.
    
- Finally, we include the command `LANGUAGE` followed by the specific SQL language keyword (we can use `PLPGSQL` by default).
    

> At some point within the function code we need to output the result, which is done with the command `RETURN`.

Instruction

For more information about dollar quotes `$$`, see this link: [https://www.postgresqltutorial.com/postgresql-plpgsql/dollar-quoted-string-constants/](https://www.postgresqltutorial.com/postgresql-plpgsql/dollar-quoted-string-constants/)

Note

Note that instead of simply using `CREATE FUNCTION` we can also use `CREATE OR REPLACE FUNCTION`, which will do exactly what the syntax suggests.

Here is an example of a simple function that adds two integers:

```sql
CREATE FUNCTION AddTwoIntegers(x int, y int)
AS
$$
BEGIN
    RETURN x + y
END
$$
LANGUAGE PLPGSQL
```

### Advanced Structure and Syntax

Building on the basic structure and syntax already described, we can generate more advanced functions by including some extra query code to provide better context and options. See the following:

```sql
CREATE FUNCTION <name>(<input1> <type1>, <input2> <type2>, ...)
RETURNS <return type>
AS
$$
DECLARE
    <variable1> <type1>;
    <variable2> <type2>;
BEGIN
    <function code>
END
$$
LANGUAGE PLPGSQL
```

We have now added a line that includes `RETURNS <return type>` to define the type of variable (e.g., `VARCHAR`, `INT`, `FLOAT`, etc.) being returned. We also included a block of code starting with the command `DECLARE` in-which we can define variables and their types that will be used within the function.

Note

It's also important to note that we may need semicolons wherever a query command line is explicitly ended and a new one begins. For example, a semicolon is always required after the list of variables in the `DECLARE` block before the `BEGIN` command to define the function code. The semicolon simply tells the query that there is a separation between parts of the code and not to try and use it as one big command (e.g., two `SELECT` statements need to be separated by a semicolon).

Here is the same example of adding two integers but using the more advanced structure and syntax:

```sql
CREATE FUNCTION AddTwoIntegersAdvanced(x int, y int)
RETURNS int
AS
$$
DECLARE
    z int;
BEGIN
    z = x + y;
    RETURN z
END
$$
LANGUAGE PLPGSQL
```

### Accessing Tables Within Functions

Functions exist as part of a database, and therefore they can recognize tables within that database. We simply need to specify the table along with its schema. For example, let's say we want to make a function that will compute the range (maximum minus minimum) of the values in a particular column of a particular table:

```sql
CREATE FUNCTION GetRangeOfValues()
RETURNS float
AS
$$
DECLARE
    max_value float;
    min_value float;
    range float;
BEGIN
    SELECT MAX(column) INTO max_value FROM public.table;
    SELECT MIN(column) INTO min_value FROM public.table;
    range = max_value - min_value;
    RETURN range;
END
$$
LANGUAGE PLPGSQL
```

Note

Note that we include the schema name when specifying the table (i.e., `public.table`). We also use the command `INTO` to store the `SELECT` statement result into the variable (i.e., `max_value` and `min_value`).

---

