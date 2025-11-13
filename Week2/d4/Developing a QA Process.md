We are returning to the Chinook database for this activity. Recall that in the [Putting it All Together](https://data.compass.staging.lighthouselabs.ca/days/w2d3/activities/2244) activity you answered a series of questions by using SQL to query the database.

Instruction

Your task in this activity is to use questions #1, #4, and #6 and develop your own data validation process for your queries. A solution for these tasks is as follows.

#### Solution :

**1. Data validation for TASK 1:**

- Check that the email addresses provided for each customer are in a valid email format.
    
- Ensure that the FirstPurchaseDate is not later than the current date.
    
- Verify that the TotalSpent column contains valid decimal or integer values.
    
- Check that the NumDistinctArtists column contains integer values and is not negative.
    

```sql
SELECT c.FirstName, c.LastName, 
       CASE 
         WHEN c.Email NOT LIKE '%_@__%.__%' THEN NULL 
         ELSE c.Email 
       END AS Email,
       MIN(i.InvoiceDate) AS FirstPurchaseDate, 
       SUM(CASE WHEN i.Total NOT BETWEEN 0 AND 999999 THEN NULL ELSE i.Total END) AS TotalSpent, 
       COUNT(DISTINCT CASE WHEN al.ArtistId NOT BETWEEN 1 AND 999 THEN NULL ELSE al.ArtistId END) AS NumDistinctArtists
FROM Customer c
JOIN Invoice i ON c.CustomerId = i.CustomerId
JOIN InvoiceLine il ON i.InvoiceId = il.InvoiceId
JOIN Track t ON il.TrackId = t.TrackId
JOIN Album al ON t.AlbumId = al.AlbumId
GROUP BY c.CustomerId
HAVING SUM(i.Total) > 0
ORDER BY TotalSpent DESC, c.LastName;
```

**Explanation**:

- Email validation check: the CASE statement ensures that the Email field only contains valid email addresses by using a regular expression pattern.
    
- TotalSpent validation check: the CASE statement ensures that the TotalSpent column contains valid decimal or integer values and filters out any values outside the valid range (0-999,999).
    
- NumDistinctArtists validation check: the CASE statement ensures that the ArtistId column contains integer values and filters out any values outside the valid range (1-999).
    

---

**2. Data validation for TASK 4:**

- Ensure that the InvoiceDate column is in a valid date format.
    
- Verify that the TotalSpent column contains valid decimal or integer values.
    
- Check that the FirstName and LastName columns contain only alphabetic characters and have a length within a specified range.
    

```sql
SELECT c.FirstName, c.LastName, i.InvoiceDate,
       CASE 
         WHEN c.Email NOT LIKE '%_@__%.__%' THEN NULL 
         ELSE c.Email 
       END AS Email,
       SUM(CASE WHEN i.Total NOT BETWEEN 0 AND 999999 THEN NULL ELSE i.Total END) AS TotalSpent
FROM Customer c
JOIN Invoice i ON c.CustomerId = i.CustomerId
WHERE i.InvoiceDate BETWEEN '2013-01-01' AND '2013-01-31'
      AND EXTRACT('month' FROM i.InvoiceDate) = '01'
      AND LENGTH(c.FirstName) BETWEEN 1 AND 50
      AND LENGTH(c.LastName) BETWEEN 1 AND 50
      AND c.FirstName SIMILAR TO '[A-Za-z]{1,50}'
      AND c.LastName SIMILAR TO '[A-Za-z]{1,50}'
GROUP BY c.CustomerId, i.InvoiceDate
HAVING SUM(i.Total) > 0
ORDER BY TotalSpent DESC;

```

**Explanation** :

- InvoiceDate validation check: the WHERE clause filters the results to only include rows where the InvoiceDate is between January 1, 2013 and January 31, 2013, and uses the EXTRACT function to extract the month portion of the InvoiceDate column for comparison with January 1, 2013.
    
- TotalSpent validation check: the CASE statement ensures that the TotalSpent column contains valid decimal or integer values and filters out any values outside the valid range (0-999,999).
    
- FirstName and LastName validation checks: the SIMILAR TO operator with a regular expression ensures that the FirstName and LastName columns contain only alphabetic characters and have a length within the specified range (1-50).
    

---

**3. Data validation for TASK 6:**

- Ensure that the Genre table has a GenreId column that is a valid integer.
    
- Verify that the Customer, Invoice, InvoiceLine, Track, and Genre tables are properly joined on their respective keys.
    
- Confirm that the COUNT function with the DISTINCT keyword is accurately calculating the number of distinct genres each customer has purchased music from.
    
- Check that the results only include customers who have purchased music from more than one genre.
    
- Verify that the results are ordered by the number of distinct genres in descending order.
    

```sql

-- Validate the join between the tables
SELECT COUNT(*)
FROM Customer c
JOIN Invoice i ON c.CustomerId = i.CustomerId
JOIN InvoiceLine il ON i.InvoiceId = il.InvoiceId
JOIN Track t ON il.TrackId = t.TrackId
JOIN Genre g ON t.GenreId = g.GenreId;

-- Validate the COUNT function with DISTINCT
SELECT COUNT(DISTINCT g.GenreId) FROM Customer c JOIN Invoice i ON c.CustomerId = i.CustomerId JOIN InvoiceLine il ON i.InvoiceId = il.InvoiceId JOIN Track t ON il.TrackId = t.TrackId JOIN Genre g ON t.GenreId = g.GenreId;

-- Validate that the query only returns customers who have purchased music from more than one genre
SELECT COUNT(*)
FROM (
  SELECT c.CustomerId, COUNT(DISTINCT g.GenreId) AS NumDistinctGenres
  FROM Customer c
  JOIN Invoice i ON c.CustomerId = i.CustomerId
  JOIN InvoiceLine il ON i.InvoiceId = il.InvoiceId
  JOIN Track t ON il.TrackId = t.TrackId
  JOIN Genre g ON t.GenreId = g.GenreId
  GROUP BY c.CustomerId
  HAVING COUNT(DISTINCT g.GenreId) > 1
) AS subquery;

-- Validate the order by clause
SELECT c.FirstName, c.LastName, COUNT(DISTINCT g.GenreId) AS NumDistinctGenres
FROM Customer c
JOIN Invoice i ON c.CustomerId = i.CustomerId
JOIN InvoiceLine il ON i.InvoiceId = il.InvoiceId
JOIN Track t ON il.TrackId = t.TrackId
JOIN Genre g ON t.GenreId = g.GenreId
GROUP BY c.CustomerId
HAVING COUNT(DISTINCT g.GenreId) > 1
ORDER BY NumDistinctGenres DESC;
```

**Explanation** :

- The first validation check verifies that the GenreId column in the Genre table contains only valid integer values greater than 0.
    
- The second validation check ensures that the tables are properly joined on their respective keys and that all necessary columns exist.
    
- The third validation check confirms that the COUNT function with DISTINCT keyword is accurately calculating the number of distinct genres each customer has purchased music from.
    
- The fourth validation check ensures that the query only returns customers who have purchased music from more than one genre.
    
- The fifth validation check verifies that the results are properly ordered by the number of distinct genres in descending order.