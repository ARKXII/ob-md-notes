#sql 
*one of the hardest strings to parse*

[[advanced queries]]
[[sql cheatsheet]]
[[strings]]

---
## STRFTIME
- at the moment, it isn't very clear to me how to parse this.
- so make sure that you understand how the date is formatted first before using this
```sql
SELECT Birthdate,
STRFTIME('%Y', Birthdate), AS Year
STRFTIME('%m', Birthdate), AS Month
STRFTIME('%d', Birthdate), AS Day
FROM Employees
```
*this query separates the formatted date YYYY-MM-DD into their respected columns*

## NOW
- denotes the current date

### use case for STRFTIME
- this computes the age
```sql
SELECT Birthdate,
STRFTIME('%Y', Birthdate) AS Year,
STRFTIME('%m', Birthdate) AS Month,
DATE(('now') - Birthdate) AS Age
```
*this takes substracts the current date to the birthdate to find the customer's age*