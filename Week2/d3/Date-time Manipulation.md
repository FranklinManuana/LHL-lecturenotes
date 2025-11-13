

---

When manipulating data, we often need to work with dates or times. This is even more true for data analysts because we can find some kind of a timestamp in almost every table. In the following reading, you will understand different date-time manipulation techniques and when to apply each of them.

Let's start by examining the data types available for date and time, relevant operators and functions, and their proper use.

## Data Types

There are three main data types for specifying dates and times:

|Type|Description|Example|
|---|---|---|
|`date`|Date only with year, month, and day|2023-02-26|
|`time`|Time only with hours, minutes, and seconds|13:38:07|
|`timestamp`|Date and time|2023-02-26 13:38:07|

Note

It's important to note that time may be specified with or without a timezone indicator. For example: `2023-02-26 13:38:07-05`, where the `-05` corresponds to GMT-5 (EST).

In addition to `date`, `time`, and `timestamp`, there is also the data type `interval` that can be used to define a specified duration of time. We specify the amount of the duration with values and units, for example:

```sql
SELECT interval '5 year'
```

```sql
SELECT interval '-10 seconds'
```

## Operations

We can perform a number of different operations with dates, times, and timestamps as well as including intervals. Some notable examples include:

- Adding intervals to a date, time, timestamp, or another interval.
    
- Adding a time to a date.
    
- Subtraction instead of addition.
    
- Division or multiplication on intervals.
    

Let's explore each with SQL query examples:

### Adding or subtracting

We can simply use the expected mathematical symbols to perform addition and subtraction of dates, times, intervals, or any combination. For example:

```sql
SELECT date '2023-02-28' + time '09:12:53' -> timestamp '2023-02-28 09:12:53'
```

```sql
SELECT time '09:12:53' - time '09:10:41' -> interval '00:02:12'
```

```sql
SELECT date '2023-02-28' + interval '5 years' -> timestamp '2028-02-28 00:00:00'
```

### Division or multiplication on intervals

Intervals can be multiplied or divided, for example:

```sql
SELECT interval '2 hours' * 100 -> interval '200:00:00'
```

```sql
SELECT interval '5 years' / 4 -> interval '1 year 3 mos'
```

Instruction

For a complete list of operations, please refer to _Table 9.32. Date/Time Operators_ in the PostgreSQL documentation [here](https://www.postgresql.org/docs/current/functions-datetime.html). You are not required to remember all of the operations from this document, keep the reference document handy for future use.

## Functions

There are a number of available functions for analyzing date-time data. For example:

- Getting the current date and time.
    
- Extracting specific fields (e.g., number of hours) from a given date or time.
    
- Calculating age.
    
- Truncating date, time, timestamp, or interval.
    

Let's explore each with SQL query examples:

### Getting the current date and time

The current date and time can be found by using one of a number of available functions. For example:

```sql
SELECT current_time
```

```sql
SELECT current_date
```

```sql
SELECT current_timestamp
```

### Extracting fields

We can get specific fields such as the month, day, hour, etc. using the `extract` function. For example:

```sql
SELECT extract(day from date '2023-02-28') -> 28
```

```sql
SELECT extract(hour from time '09:12:43') -> 9
```

### Truncation and binning

We can truncate (i.e., round down) dates, times, timestamps, or intervals using the `date_trunc` function. For example:

```sql
SELECT date_trunc('hour', timestamp '2023-02-28 09:12:43') -> timestamp '2023-02-28 09:00:00'
```

```sql
SELECT date_trunc('minute',time '09:12:43') -> time '09:12:00'
```

We can also round down a timestamp to the nearest multiple of a particular interval starting from a given origin timestamp using the `date_bin` function. For example:

```sql
SELECT date_bin('5 minutes', timestamp '2023-02-28 09:12:43', timestamp '2023-02-28 00:00:00') -> timestamp '2023-02-28 09:10:00'
```

```sql
SELECT date_bin('5 minutes', timestamp '2023-02-28 09:12:43', timestamp '2023-02-28 00:04:00') -> timestamp '2023-02-28 09:09:00'
```

Note

Note how in the second example above the nearest multiple of 5 minutes starting from 00:04:00 for 09:12:43 is 09:09:00).

  
  

Instruction

For a complete list of operations, refer to _Table 9.33. Date/Time Functions_ in the PostgreSQL documentation [here](https://www.postgresql.org/docs/current/functions-datetime.html).

In the next activity, you will get an opportunity to practice the techniques learned by following some simple steps to manipulate date and time. Please click, 'Date-time Manipulation: Walkthrough' Next button to access the activity.