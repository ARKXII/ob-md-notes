#sql 
[[joins_best practice]]
[[advanced queries]]
[[sql cheatsheet]]

---
- always check the number of records
- always cross reference what you know about the table with the result
	- *does it seem logical?*
	- *does it look right?*
- check for duplicates
- check the number of records *AFTER* joining a table
- check one table first then the next
- **SLOWLY DO**
	- think about what you are trying to achieve
	- map out your table joins
	- think about how your query is going to perform
- **DON'T GRAB UNNECESSARY DATA**
- Always check your RDBMS syntax