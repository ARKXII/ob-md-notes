*we go beyond the SELECT FROM syntax*

#sql
[[advanced queries]]
[[sql cheatsheet]]
[[strings]]
[[joins_best practice]]

---
subqueries are used for more advanced querying 
- are queries inside queries`
example:
```sql
SELECT * FROM customers
WHERE age > (SELECT MIN(age) FROM customers);
```
*the subquery above is used to find the minimum age of all customers. the outer query then selects all customers whose age is greater than that value*

---
## inner joins
- joins that selects records that only have matching values in both tables

```sql
SELECT suppliers.CompanyName,
ProductName,
UnitPrice
FROM Suppliers INNER JOIN Products ON Suppliers.supplierid = Products.supplierid;
```
*the above query selects the COMPANY NAME from the suppliers table, PRODUCTNAME, and UNITPRICE from the products table. the inner join functions as a bridge between the suppliers table and the products table with the supplierID key.*

---
## left joins ![[Pasted image 20230528143242.png]]
- LEFT JOIN takes the all the records from the left table and matches it with the records with the right table.
- all empty records from the right table will be returned NULL
```sql
SELECT C.CustomerName, O.OrderID
FROM Customers C
> LEFT JOIN Orders O ON C.CustomerID = O.CustomerID
ORDER BY C.CustomerName;
```
*the above syntax selects the CUSTOMERNAME from the Customers table, and the ORDERID from the Orders table. this returns all records from the Customers table regardless if they had made an order or not*

## right join
- the same function as the left join but takes the records from the right table and matches it with the left
> **not supported by SQLite**

```sql
SELECT C.CustomerName, O.OrderID
FROM Customers C
> RIGHT JOIN Orders O ON C.CustomerID = O.CustomerID
ORDER BY C.CustomerName;
```
*this query returns all ORDERID from the Orders table and matches it with the CUSTOMERNAME from the Customers table regardless if they have a customer attached to them or not*

left join returns all records from the left table even if they don't have a match on the right.
```sql
CustomerName | OrderID 
----------+--------- 
John Doe | 123456 
Jane Doe | 789012 
(null) | (null) 
(null) | 345678
```

right join returns all records from the right table even if they don't have a match on the left, but since we're ordered by customer name

```sql
CustomerName | OrderID
------------|--------- 
John Smith | 10
Jane Doe | 20
NULL | 30
Peter Brown | 40
```

## full outer join
- this just returns all data in the left and right tables
```sql
SELECT C.CustomerName, O.OrderID
FROM Customers C
> RIGHT JOIN Orders O ON C.CustomerID = O.CustomerID
ORDER BY C.CustomerName;
```
*this query simply returns every record in both tables regardless if they have a value or not*

---
## unions
- stack two tables on top of one another
- rare function
- both tables must have the same structure (i.e. columns, size, column order)
```sql
SELECT City, Country FROM Customers
WHERE Country = 'Germany'
> UNION
SELECT City, Country FROM Suppliers
WHERE Country = 'Germany'
ORDER BY City;
```
*this query combines the Customers and Suppliers table. we use this to find which German cities have suppliers*

---
### reference
![[Pasted image 20230528173252.png]]
#sql #joins #diagram

---
## Required Reading
[[joins_best practice]] 