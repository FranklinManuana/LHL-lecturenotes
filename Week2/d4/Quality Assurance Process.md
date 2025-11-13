### What to Look Out for When Validating Your Data

Data validation is the method for checking the accuracy and quality of data. It is often performed prior to adding, updating, or processing data. Similarly, when we want to merge data from disparate sources we often talk of ‘cleansing’ the data – in other words validating it. When validating data, we can check if the data is:

- **complete** (i.e. no blank or null values)
- **unique** (i.e. no duplicate values)
- **consistent** with what we expect (eg. a decimal between a certain range)

### An Example

In the [Putting it All Together activity](https://web.compass.lighthouselabs.ca/f1705b32-b91a-4474-95db-b060adc5a1cd), we used the `Chinook` database to practice executing several SQL queries to find the answers to a series of questions. In this activity, we will again use the tables contained in the `Chinook` database to go through some ways of validating our results.

Let’s say that you want to retrieve a list of `Album` rows with each `Track`. To achieve this, you would join on the `AlbumId` column that is in both tables (remember that joins are about combining columns based on matching data between tables).

The type of join to use depends on which table’s data is most relevant to you, and how you want the results to be returned. The query below will return all the albums and all the tracks inside each album:

```sql
SELECT a.AlbumId AS albumid, a.Title AS title, t.Name AS track_name
FROM Album a
INNER JOIN Track t
ON a.AlbumId = t.AlbumId
```

The query will give you a result set like this:

|albumid|title|track_name|
|---|---|---|
|1|For Those About To Rock We Salute You|For Those About To Rock (We Salute You)|
|2|Balls to the Wall|Balls to the Wall|
|3|Restless and Wild|Fast As a Shark|
|3|Restless and Wild|Restless and Wild|
|3|Restless and Wild|Princess of the Dawn|

Once the query returns a result set to you, you need to validate the accuracy of the result set.

How to go about doing this depends on the situation. The general rule is to review the outcome of the query to see if the result set makes sense.

#### STEP 1: Systematically validate the number of albums and number of tracks

First, we will validate the number of albums by comparing the results of two queries. Check that the result set has indeed returned the correct total number of albums by

##### Query 1: Get the number of albums from our original query.

```sql
SELECT COUNT(distinct albumid) FROM (
SELECT a.AlbumId AS albumid, a.Title AS title, t.Name AS track_name
FROM Album a
INNER JOIN Track t
ON a.AlbumId = t.AlbumId
    ) tmp
```

This will result in an output of **347.**

##### Query 2: Get the number of albums from the Album table.

```sql
SELECT COUNT(AlbumId) FROM Album
```

This will result in an output of **347.**

Since both outputs match, we know that our join worked correctly as far as the number of albums is concerned.

Next, we need to validate the number of tracks by comparing the results of two queries.

##### Query 1: Get the number of tracks from our original query.

```sql
SELECT COUNT(distinct track_name) FROM (
SELECT a.AlbumId AS albumid, a.Title AS title, t.Name AS track_name
FROM Album a
INNER JOIN Track t
ON a.AlbumId = t.AlbumId
    ) tmp
```

This will result in an output of **3256**.

##### Query 2: Get the number of tracks from the Tracks table.

```sql
SELECT COUNT(Name) FROM Track
```

This will result in an output of **3503**.

They don’t agree! But they should have.

What’s going on?

Our joined result set tells us that there are more tracks than there are distinct track names.

The next question you should ask yourself is: does this make sense? This only makes sense if we have at least one album that has more than one track that shares the same name. To validate this, you would write the following query:

```sql
SELECT title, track_name, COUNT(*) FROM (
SELECT a.AlbumId AS albumid, a.Title AS title, t.Name AS track_name
FROM Album a
INNER JOIN Track t
ON a.AlbumId = t.AlbumId
    ) tmp
    GROUP BY track_name, title
    HAVING COUNT(*) > 1
    ORDER BY track_name
```

The query above will give you a result set like this:

|"title"|"track_name"|"count"|
|---|---|---|
|"Da Lama Ao Caos"|"Banditismo Por Uma Questa"|2|
|"The Office, Season 3"|"Branch Closing"|2|
|"Heroes, Season 1"|"Company Man"|2|
|"Instant Karma: The Amnesty International Campaign to Save Darfur"|"Gimme Some Truth"|2|
|"Instant Karma: The Amnesty International Campaign to Save Darfur"|"Imagine"|2|
|"Lost, Season 3"|"Not In Portland"|2|

Furthermore, let’s spot check one of the albums, with the following query:

```sql
SELECT * FROM Track
WHERE AlbumId = 229
```

The query above will give a result set like this:

|"TrackId"|"Name"|"AlbumId"|"MediaTypeId"|"GenreId"|"Composer"|"Milliseconds"|"Bytes"|"UnitPrice"|
|---|---|---|---|---|---|---|---|---|
|2857|"A Tale of Two Cities"|229|3|19|NULL|2636970|513691652|1.99|
|2862|"The Glass Ballerina"|229|3|21|NULL|2637458|535729216|1.99|
|2863|"Further Instructions"|229|3|19|NULL|2563980|502041019|1.99|
|2866|"Every Man for Himself"|229|3|21|NULL|2637387|513803546|1.99|
|2870|"The Cost of Living"|229|3|19|NULL|2637500|505647192|1.99|
|2874|"I Do"|229|3|19|NULL|2627791|504676825|1.99|
|2875|"Not In Portland"|229|3|21|NULL|2637303|499061234|1.99|
|2876|"Not In Portland"|229|3|21|NULL|2637345|510546847|1.99|
|2881|"Flashes Before Your Eyes"|229|3|21|NULL|2636636|537760755|1.99|
|2882|"Lost Survival Guide"|229|3|21|NULL|2632590|486675063|1.99|
|2886|"Stranger In a Strange Land"|229|3|21|NULL|2636428|505056021|1.99|
|2890|"Tricia Tanaka Is Dead"|229|3|21|NULL|2635010|548197162|1.99|
|2891|"Enter 77"|229|3|21|NULL|2629796|517521422|1.99|
|2895|"Par Avion"|229|3|21|NULL|2629879|517079642|1.99|
|2899|"The Man from Tallahassee"|229|3|21|NULL|2637637|550893556|1.99|
|2900|"Expos�"|229|3|21|NULL|2593760|511338017|1.99|
|2903|"Left Behind"|229|3|21|NULL|2635343|538491964|1.99|
|2908|"One of Us"|229|3|21|NULL|2638096|502387276|1.99|
|2909|"Catch-22"|229|3|21|NULL|2561394|489773399|1.99|
|2912|"D.O.C."|229|3|21|NULL|2616032|518556641|1.99|
|3165|"The Brig"|229|3|21|NULL|2617325|488919543|1.99|
|3169|"The Man Behind the Curtain"|229|3|21|NULL|2615990|493951081|1.99|
|3170|"Greatest Hits"|229|3|21|NULL|2617117|522102916|1.99|
|3224|"Through a Looking Glass"|229|3|21|NULL|5088838|1059546140|1.99|
|3251|"Through the Looking Glass, Pt. 2"|229|3|21|NULL|2617117|550943353|1.99|
|3252|"Through the Looking Glass, Pt. 1"|229|3|21|NULL|2610860|493211809|1.99|

Now we see that indeed, albums with tracks of the same names do exist.

#### STEP 2: Manually spot check

Manually spot checking is a great addition to the systematic validation as it addresses boundary cases and also checks that the validation logic was correct.

Spot check a few of the albums from the result set and validate that each of the albums checked indeed has the correct number of tracks

The SQL query that would help you to do this is:

```sql
SELECT * FROM (
SELECT a.AlbumId AS albumid, a.Title AS title, t.Name AS track_name
FROM Album a
INNER JOIN Track t
ON a.AlbumId = t.AlbumId
WHERE a.AlbumId = 229
    ) tmp
    ORDER BY track_name
```

## Conclusion

What is data validation in SQL and why is it important? Data validation is a method for checking the accuracy and quality of data. Information in databases is constantly being updated, deleted, queried, or moved by multiple people or processes, so ensuring that data is valid at all times is essential. With practice, you will develop a series of checks and balances for validating your data and the results it gives you.