
# Introduction

+ [Statement](#statement-&-definition)
+ [Create Table](#create-table)
+ [Insertt](#insert)
+ [Select](#select)
+ [Alter Table](#alter-table)
+ [Update](#update)

***
# Statement & Definition  
The code below is a SQL statement. A statement is a text that the database recognizes as a valid command. Statements always end in a semicolon `;`.
```
CREATE TABLE table_name (
   column_1 data_type, 
   column_2 data_type, 
   column_3 data_type
);
```
The structure of SQL statements varies. The number of lines used does not matter. A statement can be written all on one line, or split up across multiple lines if it makes it easier to read. In this course, you will become familiar with the structure of common statements.  

CLAUSES: perform specific tasks in SQL. By convention, clauses are written in capital letters. Clauses can also be referred to as commands. 
PARAMETER: A parameter is a list of columns, data types, or values that are passed to a clause as an argument.  
DATA TYPE: An attribute that specifies the type of data that the object can hold: integer data, character data, monetary data, date and time data, binary strings, and so on.  

[top](#introduction)
***
# Create Table   
```
CREATE TABLE table_name (
   column_1 data_type, 
   column_2 data_type, 
   column_3 data_type
);
```
`CREATE TABLE` is a clause.  
`table_name` refers to the name of the table that the command is applied to.  
`(column_1 data_type, column_2 data_type, column_3 data_type)` is a list of parameters associated with their data type.
`CREATE` statements allow us to create a new table in the database. You can use the `CREATE` statement anytime you want to create a new table from scratch.  

[top](#introduction)  
***  
# INSERT
The `INSERT` statement inserts a new row into a table.
```
INSERT INTO class (id, name, age ) 
VALUES (1, 'Bob Dylan', 22);
```
`INSERT INTO` is a clause that adds the specified row or rows. "class" is the table the row is added to.  
`(id, name, age)` is a parameter identifying the columns that data will be inserted into.  
`VALUES` is a clause that indicates the data being inserted.  
"(1, 'Bob Dylan', 22)" is a parameter identifying the values being inserted.
   + 1:             an integer that will be added to id column
   + "Bob Dylan":   text that will be added to name column
   + 22:            an integer that will be added to age column

[top](#introduction)
***
# Select
`SELECT` statements are used to fetch data from a database. In the statement below, `SELECT` returns all data in the name column of the class table.  
```
SELECT name FROM class;
```
You can also query data from all columns in a table with SELECT.  
```
SELECT * FROM celebs;
``` 
`*` is a special wildcard character. It allows you to select every column in a table without having to name each one individually.  
`SELECT` statements always return a new table called the result set.  

[top](#introduction)
***
# Alter Table
`ALTER TABLE` statement adds a new column to a table. You can use this command when you want to add columns to a table.  
```
ALTER TABLE class 
ADD COLUMN teacher TEXT;
```
`TEXT` is the data type for the new column.  
`NULL` is a special value in SQL that represents missing or unknown data. The rows that existed before the column was added have `NULL` `∅` values for teacher.

[top](#introduction)  
***
# Update
`UPDATE` statement edits a row in a table. You can use the `UPDATE` statement when you want to change existing records.  
```
UPDATE class 
SET age = 24 
WHERE id = 4; 
```
`SET` is a clause that indicates the column to edit.  
`WHERE` is a clause that indicates which row(s) to update with the new column value.  

[top](#introduction)  
***
# Delete
The DELETE FROM statement deletes one or more rows from a table. You can use the statement when you want to delete existing records. The statement below deletes all records in the celebs table with no twitter_handle:

DELETE FROM celebs 
WHERE twitter_handle IS NULL;
 
DELETE FROM is a clause that lets you delete rows from a table.
celebs is the name of the table we want to delete rows from.
WHERE is a clause that lets you select which rows you want to delete. Here we want to delete all of the rows where the twitter_handle column IS NULL.
IS NULL is a condition in SQL that returns true when the value is NULL and false otherwise.

Constraints
Constraints that add information about how a column can be used are invoked after specifying the data type for a column. They can be used to tell the database to reject inserted data that does not adhere to a certain restriction. The statement below sets constraints on the celebs table.

CREATE TABLE celebs (
   id INTEGER PRIMARY KEY, 
   name TEXT UNIQUE,
   date_of_birth TEXT NOT NULL,
   date_of_death TEXT DEFAULT 'Not Applicable'
);
 
1. PRIMARY KEY columns can be used to uniquely identify the row. Attempts to insert a row with an identical value to a row already in the table will result in a constraint violation which will not allow you to insert the new row.

2. UNIQUE columns have a different value for every row. This is similar to PRIMARY KEY except a table can have many different UNIQUE columns.

3. NOT NULL columns must have a value. Attempts to insert a row without a value for a NOT NULL column will result in a constraint violation and the new row will not be inserted.

4. DEFAULT columns take an additional argument that will be the assumed value for an inserted row if the new row does not specify a value for that column.



----------------------------------------------------

Create a Table
In this project, you will create your own friends table and add/delete data from it!

CREATE TABLE friends (
  id INTEGER,
  name TEXT,
  birthday Date
);

INSERT INTO friends(id, name, birthday)
VALUES (1,'Ororo Munroe', '1940-05-30');
INSERT INTO friends(id, name, birthday)
VALUES (2,'Joe Dassin', '1950-07-23');
INSERT INTO friends(id, name, birthday)
VALUES (3,'Bernard Tapis', '1998-12-25');

UPDATE friends
SET name = 'Storm' 
WHERE id = 1; 

ALTER TABLE friends 
ADD COLUMN 'email' TEXT;

UPDATE friends
set email = 'storm@codecademy.com'
WHERE id = 1;
UPDATE friends
set email = 'Joe@codecademy.com'
WHERE id = 2;
UPDATE friends
set email = 'Bernard@codecademy.com'
WHERE id = 3;

DELETE FROM friends
WHERE id = 1;

SELECT * FROM friends;
