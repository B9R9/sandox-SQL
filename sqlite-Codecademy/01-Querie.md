# Introduction
+ [Select](#select)                           
+ [Distinct](#distinct)                      
+ [Where](#where) 
+ [Like](#like)
+ [IsNULL](#is-null)
+ [Between](#between)
+ [And](#and)
+ [Or](#or)
+ [Orderby](#order-by)
+ [Limit](#limit)
+ [Case](#case)

***
# SELECT
`SELECT` is used every time you want to query data from a database. And `*` means all columns.  
If you are interested in two of the columns. You can use:
```
SELECT column 1, column2
FROM <TABLE_NAME>
``` 
`AS` is a keyword in SQL that allows you to rename a column or table using an alias. The new name can be anything you want as long as you put it inside of single quotes. 
```
SELECT column_name AS 'whatever'
FROM <TABLE_NAME>
```
[top](#introduction)
***
# Distinct
`DISTINCT` is used to return unique values in the output. It filters out all duplicate values in the specified column(s).
```
SELECT fruits
FROM inventory;
```
OUTPUT
```
banana
water melon
apple
apple
apple
```
If you add `DISTINCT` before the column name
```
SELECT DISTINCT fruits
FROM inventory;
```
OUTPUT
```
banana
water melon
apple
```
[top](#introduction)
***
# Where
We can restrict our query results using the `WHERE` clause in order to obtain only the information we want.
```
SELECT *
FROM movies
WHERE rating > 8;
```
The `WHERE` clause filters the result set to only include rows where the following condition is true.
`rating > 8` is the condition. Only rows with a value greater than 8 in the rating column will be returned.
Comparison operators used with the `WHERE` clause are:
 + `=` equal to
 + `!=` not equal to
 + `>` greater than
 + `<` less than
 + `>=` greater than or equal to
 + `<=` less than or equal to
   
[top](#introduction)
***
# Like
LIKE can be a useful operator when you want to compare similar values.
```
SELECT * 
FROM movies
WHERE name LIKE 'Se_en';
```
`LIKE` is a special operator used with the `WHERE` clause to search for a specific pattern in a column. 
`_` represents a wildcard character.
The `_` means you can substitute any individual character here without breaking the pattern. The names Seven and Se7en both match this pattern.  

  
`%` is another wildcard character that can be used with `LIKE`  
`A%` matches all movies with names that begin with the letter ‘A’  
`%a` matches all movies that end with ‘a’  
`%man%`matches all movies that contain the word 'man'  
`LIKE` is not case-sensitive. ‘Batman’ and ‘Man of Steel’ will both appear in the result of the query above.  

  [top](#introduction)
***
# Is Null
Unknown values are indicated by `NULL`.  
It is not possible to test for NULL values with comparison operators, such as `=` and `!=`.  
Instead, we will have to use these operators:
```
IS NULL
IS NOT NULL
```
```
SELECT name
FROM movies 
WHERE rating IS NOT NULL;
```

  [top](#introduction)

***
# Between
The `BETWEEN` operator is used in a `WHERE` clause to filter the result set within a certain range. It accepts two values that are either numbers, text or dates.  
```
SELECT *
FROM movies
WHERE year BETWEEN 1990 AND 1999;
```
 When the values are text, BETWEEN filters the result set within the alphabetical range.  
In this statement, BETWEEN filters the result set to only include movies with names that begin with the letter ‘A’ up to, but not including ones that start with ‘J’.
```
SELECT *
FROM movies
WHERE name BETWEEN 'A' AND 'J';
```
If a movie has a name of simply ‘J’, it would actually match. This is because `BETWEEN` goes up to the second value — up to ‘J’. So the movie named ‘J’ would be included in the result set but not ‘Jaws’.  

 [top](#introduction)
***
# And
When you want to combine multiple conditions in a `WHERE` clause to make the result set more specific and useful.
We use the `AND` operator.
```
SELECT * 
FROM movies
WHERE year BETWEEN 1990 AND 1999
   AND genre = 'romance';
```
Both conditions must be true for the row to be included in the result.  
[top](#introduction)  

***
# Or
The `OR` operator can be used to combine multiple conditions in `WHERE`, but there is a fundamental difference:  
`AND` operator displays a row if all the conditions are true.  
`OR` operator displays a row if any condition is true.  
```
SELECT *
FROM movies
WHERE year > 2014 -- 1st condition
   OR genre = 'action'; -- 2nd condition
``` 
With OR, if any of the conditions are true, then the row is added to the result.  
[top](#introduction)

***
# Order By
We can sort the results using `ORDER BY`. `ORDER BY` is a clause that indicates you want to sort the result set by a particular column.
For example, if we want to sort everything by the movie’s title from A through Z:
```
SELECT *
FROM movies
ORDER BY name;
```
`DESC` is a keyword used in ORDER BY to sort the results in descending order (high to low or Z-A).
```
SELECT *
FROM movies
WHERE rating > 8
ORDER BY year DESC;
```
`ASC` is a keyword used in ORDER BY to sort the results in ascending order (low to high or A-Z).  
`ORDER BY` always goes after `WHERE` (if `WHERE` is present).  
The column that we `ORDER BY` doesn’t have to be one of the columns that we’re displaying.  
[top](#introduction)  

***
# Limit
`LIMIT` is a clause that lets you specify the maximum number of rows the result set will have. This saves space on our screen and makes our queries run faster.
```
SELECT *
FROM movies
LIMIT 10;
```
`LIMIT` always goes at the very end of the query. Also, it is not supported in all SQL databases.  
[top](#introduction)
***
# Case
`CASE` statement allows us to create different outputs (usually in the SELECT statement). It is SQL’s way of handling if-then logic.
```
SELECT name,
 CASE
  WHEN rating > 8 THEN 'Fantastic'
  WHEN rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END
FROM movies;
```
 We can rename the column to ‘Review’ using `AS`:
```
SELECT name,
 CASE
  WHEN rating > 8 THEN 'Fantastic'
  WHEN rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END AS 'Review'
FROM movies;
```

  [top](#introduction)
 
