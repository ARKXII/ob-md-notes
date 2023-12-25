- these are queries i had difficulties with

## self-join
> Retrieve a list with the managers last name, and the last name of the employees who report to him or her.

```sql
SELECT M.LastName AS Manager,
E.LastName AS Employee
FROM Employees E
INNER JOIN Employees M ON E.ReportsTo = M.EmployeeID
```
the above query demonstrates a self-join. it duplicates the Employees table into two, one for managers and one for employees.

it then uses those two tables to cross reference the ReportsTo column with the appropriate employee name.

---
## IS NULL
> Find the name and ID of the artists who do not have albums.

```sql
SELECT ar.name, ar.artistID, a.title
FROM artists ar
LEFT JOIN albums a ON a.artistID = ar.artistID
WHERE a.artistID IS NULL
```
this does the request just fine.

it's just confusing to me because we search for NULL artistIDs, but this is the reasoning I found closest to it.

*we left join artists to albums, which takes all the artist records even if they don't have albums. this creates a table that has both artists and albums. my guess is that WHERE is performed on the right table*

---
## double conditional
*question: Are there more reviews with the word "love" or with the word "hate" in them?*

```sql
SELECT CASE -- double conditional 
	WHEN LOWER(text) LIKE '%love%' THEN 'love' 
	WHEN LOWER(text) LIKE '%hate%' THEN 'hate'
	ELSE NULL END AS reviews, 
COUNT(*) AS count 
FROM review GROUP BY reviews;
```

- this is helpful to think of this as exactly the same as IF ELSE in traditional programming
- in this CASE, we are searching for two words in the same column
	- we establish the IF conditions
	- then we add the function that we want to do, which is count
	- to get results for each of our conditions, we group by CASE