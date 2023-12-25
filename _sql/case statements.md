#sql 

[[advanced queries]]
[[sql cheatsheet]]
[[strings]]

- filtering tool similar to C#
- this is mainly used to transform bulk data into another format

---
## syntax
```sql
CASE input_expression
	WHEN condition_statement THEN result
	ELSE else_condition
END
```

## sample use case
```sql
SELECT
employeeid,
firstname,
lastname,
city,
CASE City
	WHEN 'Calgary' THEN 'Calgary'
ELSE 'Other'
	END calgary	# function returns to column name 'calgary'
FROM Employees
ORDER BY LastName, FirstName;
```
