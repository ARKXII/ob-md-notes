hopefully this helps with remembering.

#sql
[[sql cheatsheet]]
[[advanced queries]]
[[strings]]

---
# Table Manipulation
- **CREATE TABLE** - create table in database
```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);
```
*CREATE TABLE in this case creates a table named 'table name'*

> 	i. column1 refers to the column name for the table.
> 
> 	ii. datatype refers to what kind of data is going to be stored in that particular column. for example datatype INTEGER signifies that only integers are going to be accepted in that column, whereas STRING accepts alphanumeric data but will be stored in *string* form.
> 
> 	iii. constraints refer to modifications to the datatype. an example use case will be *TEXT UNIQUE* where in TEXT is the data type and UNIQUE is the constraint, meaning that the records in that column should be unique.

- **INSERT INTO** - inserts a row of data into a table
```sql
INSERT INTO customers (name, email, age) VALUES ('John Doe', 'john@example.com', 30);
```
*the syntax above inserts the values 'John Doe', his email, and age into the CUSTOMERS table. keep in mind that we initialize first what columns are the data going to be inserted into first with the table arguments ( "" )*

 - **DROP** - deletes a specified table.
```sql
DROP employee_data;
```

- **UPDATE** - updates a record. to be used in conjunction with searching queries.
``` sql
UPDATE customer_data
SET country = 'America'
WHERE name = 'John Moore' AND customer_id = 10093
```

---
# Querying Data

- **SELECT** - very important
- **FROM** - where you get the data from

- **WHERE** - used like "where in"
```sql
SELECT employee_name, employee_position, employee_type
FROM Organization
> WHERE employee_type = "full"
```
*WHERE in this case finds all records where employee_type is equal to 'full'*	

```sql
SELECT employee_name, employee_position, employee_type
FROM Organization
> WHERE employee_name LIKE "John%"
```
*Where in this case finds all records where employee name starts with 'John'. This uses the wild card '%'*

- **GROUP BY** - sorts the records by selected column name
- **HAVING** - this filters groups based on a specified condition
```sql
SELECT country, COUNT(*) as customer_count
FROM customers
GROUP BY country
> HAVING customer_count > 5;
```
*this query counts every customer in the country table and only returns countrys where the customer_count is > 5

- **AS** - alias function. 
- **IN** - used in a lot of this but this one stuck out to me
```sql
SELECT *
FROM Customers
WHERE state IN ('AB', 'BC', 'CD')
```
*the above WHERE statement returns all matches in the parentheses*