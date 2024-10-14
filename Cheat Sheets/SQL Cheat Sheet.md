# Setting up Database and table
- To create a new user
```sql
CREATE USER <username> WITH PASSWORD "xxxxx";
```
- To create a database  
```sql
CREATE DATABASE database_name;
```
- To create a table 
```sql
CREATE TABLE table_name;
```
- To connect to database on the Command line use `\c database_name` command 
- To list databases present on a server use `\l` command 
## Table Manipulation
- To turn an existing column to a Foreign Key 
```sql
ALTER TABLE <table_name> ADD FOREIGN KEY(<column_name>) REFERENCES <reference_table>(<reference_column>); 
```
## To Find pattern in a table
To find a pattern in a table we use `LIKE` keyword. For example
```sql 
SELECT * FROM <table_name> WHERE <column_name> LIKE <pattern>
```
### Pattern matching Character
There some pattern matching characters. Some are:
- `_` which will return rows that have any character in that spot
- `%` which returns row that have values after the character 
The `NOT LIKE` keyword is the opposite of the `LIKE` keyword


There is a `COUNT` keyword which is used to know the number of entries of a row in a table. For example 
```sql
SELECT COUNT(<column_name>) FROM <table_name>;
```
`RIGHT JOIN` command joins two tables together in which the second table is joined to the right of the first table in which it returns all the row of the second table but return the rows of the first table linked to the first table. 
For example
```sql
SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id;
```
In this case the `majors` table is the right table in which all the rows of the table will be given and the row for `students` table  that is linked to the `majors` table will be given.
**Note**: `LEFT JOIN` command is the opposite of the `RIGHT JOIN` command 

`INNER JOIN` command join the two table together in which it returns rows that are linked to the column of each table 