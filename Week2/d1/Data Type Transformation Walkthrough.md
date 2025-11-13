Let's go through some examples of data type transformation using the Chinook database in pgAdmin.

### Formatting Track File Size

> We can see in the `track` table that the file size is provided in the `bytes` column. Let's convert it to a string and give it formatting without any decimal digits and with commas where appropriate and give the resulting column the name `kb_format`. We can do this using `TO_CHAR` as follows:

```sql
SELECT TO_CHAR(bytes, '9G999G999') AS kb_format FROM track
```

### Converting Genre ID

> Also in the `track` table we have the column `genreid` which is made up of integer data. Let's convert that to floating point values.

```sql
SELECT CAST(genreid AS float) FROM track
```

### Formatting Employee Birthdays

> In the table `employee` we have birthdays given in the column `birthdate`. Let's format those as strings with the day number, then three-letter abbreviated month, and then the year (after a comma).

```sql
SELECT TO_CHAR(birthdate, 'DD Mon, YYYY') FROM employee
```

### Handling Null Values

> Notice that in the `invoice` table we have state, country, and postal code for billing purposes but that there are many null values. Let's replace null values in the `billingstate` column with the values in the `billingpostalcode` column.

```sql
SELECT COALESCE(billingstate, billingpostalcode) FROM invoice
```

> What if the postal code value is also null? Let's modify our query to then replace with the country if that is the case.

```sql
SELECT COALESCE(billingstate, billingpostalcode, billingcountry) FROM invoice
```

> What if the country is also null? Let's add a final option to replace with the string 'n/a' if that is the case.

```sql
SELECT COALESCE(billingstate, billingpostalcode, billingcountry, 'n/a') FROM invoice
```