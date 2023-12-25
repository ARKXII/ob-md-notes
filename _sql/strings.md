*working with strings*
#sql

[[sql cheatsheet]]

---
## concatenations
- means linking words together
- symbol = *||*
```sql
SELECT
CompanyName,
ContactName,
CompanyName || ' ('|| ContactName||')'
FROM customers
```
*this query combines the CompanyName, and ContactName in the last column*

---
## trimming
- trims the leading or trailing spaces from a string
```sql
SELECT TRIM ("          hello world       ") AS TrimmedString;
```
*this removes the spaces from the string, leaving just "hello world"*
- **LTRIM** or **RTRIM** trims from either the left side or right side of the string.

---
## substring
- returns just the specified number of characters from a string
```sql
SUBSTR (string name, char position, number of characters)
```
*syntax for substring. char position is the starting point of the command*
```sql
SELECT first_name, SUBSTR (first_name,2,3)
FROM employees

> returns

first_name | substr(first_name,2,3)
---------- | ----------------------
John | ohn
MrBeast | rBe
Schlatt | chl
```

---
## upper and lower
- converts strings to upper or lowercase
```sql
UPPER(column_name)
LOWER(column_name)
```
