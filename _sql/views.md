#sql 

[[sql cheatsheet]]
- creates a temporary table

---
## syntax
```
CREATE [TEMP] VIEW [IF NOT EXISTS] view_name (column_name_list)
AS
select-statement;
```

### sample use case
```
CREATE VIEW my_view
AS
SELECT
r.regiondescription
,t.territorydescription
,e.lastname
,e.firstname
,e.reportsto
FROM Region r
INNER JOIN Territories t on r.regionid = t.regionid
INNER JOIN Employeeterritories et on t.territoryid = et.territoryid
INNER JOIN Employees e on et.employeeid = e.employeeid

```
*this creates an temporary table and uses the alias AS as a way to manipulate the data. we then INNER JOIN the tables we need to build the temp table*

to view the data, we run
```
SELECT *
FROM my_view
```

to destroy the temp table
```
DROP VIEW my_view
```

