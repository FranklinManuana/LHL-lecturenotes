

Sometimes, we may need or want to transform columns of data from one type to another. For example, it could be that we have integer values that we would prefer to list as floating point values, or numeric identification numbers we wish to list as text. To do this, we need to use a data type transformation method.

### Casting

The most general method of data type transformation is using `CAST`, which will attempt to take data of one type and convert it to a new desired type. We use the word _attempt_ because not all data types can be converted to any other type (e.g., a string such as 'Hello' cannot be converted to an integer).

The general syntax for using `CAST` is as follows:

```sql
CAST(expression AS type)
```

Where `expression` is a value or column of data and `type` is the desired data type to be converted to.

Here are some examples of using the `CAST` function:

```sql
CAST(price AS FLOAT)
```

```sql
CAST(id_number AS VARCHAR)
```

```sql
CAST(date_text AS TIMESTAMP)
```

### Formatting

Instead of simply casting various data types to text (i.e., casting as `VARCHAR` type), we can also be more specific about how we want to format the text during conversion. To do this, we can use the function `TO_CHAR` instead of `CAST`.

The general syntax for using `TO_CHAR` is as follows:

```sql
TO_CHAR(expression, format)
```

Where `expression` is a value or column of data and `format` is a string of text specifying the desired format.

#### Formatting Numeric Values

When converting numeric values (integers, floats, etc.) to strings, we specify format using a string that defines each digit or character in the output. We can use the following characters in the format specifier:

|Character|Usage|
|---|---|
|9|numeric digit, empty if not present|
|0|numeric digit, zero if not present (leading zeros)|
|D|decimal point|
|S|sign (negative or positive)|
|G|comma (i.e., thousands, millions, etc.)|

Consider the following example where we wish to convert a floating point value to formatted text:

```sql
SELECT TO_CHAR(1439.733, '9999')
```

> |output|
> |---|
> |1440|

```sql
SELECT TO_CHAR(1439.733, '09999')
```

> |output|
> |---|
> |01440|

```sql
SELECT TO_CHAR(1439.733, '9999D9')
```

> |output|
> |---|
> |1439.7|

```sql
SELECT TO_CHAR(1439.733, '9G999D9')
```

> |output|
> |---|
> |1,439.7|

```sql
SELECT TO_CHAR(1439.733, 'S9G999D9')
```

> |output|
> |---|
> |+1,439.7|

Note

Note that we can run the same type of transformation backwards (i.e., converting text to numeric) using `TO_NUMBER` and providing a string input as well as the format specifier.

```sql
SELECT TO_NUMBER('+1,439.73', 'S9G999D99')
```

> |output|
> |---|
> |1439.73|

#### Formatting Date and Time Data

When converting date and time data to a string, we use another series of specifier characters. Although there are many more options, the following table lists the most common ones we would use:

|Character|Usage|
|---|---|
|HH|hours|
|MI|minutes|
|SS|seconds|
|YYYY|year|
|MM|month number|
|Month|month (text)|
|DD|day number|
|Day|day of the week (text)|

Consider the following examples:

```sql
SELECT TO_CHAR(DATE('2008-08-30'),'Day, Month DD, YYYY')
```

> |output|
> |---|
> |Saturday, August 30, 2008|

```sql
SELECT TO_CHAR(NOW(),'HH:MI:SS AM')
```

> |output|
> |---|
> |03:26:13 PM|

We can also convert strings to dates or times using `TO_DATE` or `TO_TIMESTAMP`, again by providing the input string to be converted and the format specifier defining the list of characters.

```sql
SELECT TO_DATE('2008-08-30','YYYY-MM-DD')
```

> |output|
> |---|
> |2008-08-30|

```sql
SELECT TO_TIMESTAMP('03:26:13 PM 30/08/2008','HH:MI:SS AM DD/MM/YYYY')
```

> |output|
> |---|
> |2008-08-30 15:26:13-04|

### Handling NULL Values

It's possible to convert null values using the `COALESCE` function, which will return the first non-null value in the given list of inputs. Note that each of the inputs provided need to have the same data type (i.e., all integer, all text, etc.).

Consider an example where we want to replace any null values in the column `customer_id` with the string `'missing'`.

```sql
COALESCE(customer_id, 'missing')
```

We could also attempt to first replace any null values in the column `customer_id` with the values in column `company` and if both are null then replace with the value `'missing'`.

```sql
COALESCE(customer_id, company, 'missing')
```

Instruction

See the following resource for more details on specific formatting options: [https://www.postgresql.org/docs/8.1/functions-formatting.html](https://www.postgresql.org/docs/8.1/functions-formatting.html)

## Review Questions

Answer all of the questions below to review your understanding. Try to answer them in your own words.

Question