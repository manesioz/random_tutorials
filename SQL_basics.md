# SQL Basics

Relational databases are collections of tables, where each table has columns (or fields) and rows (or instances).
The relational behaviour arises from the fact that each row has a Primary Key that uniquely identifies it,
and you can use other table's primary key's in another table (now considered a foreign key) to describes relationships between the tables.


CREATE TABLE table_name ( //creates a table
          column_1 data_type,
          column_2 data_type,
          column_3 data_type
);
//creating a table with specified columns and data types

INSERT Statements are used to insert a new row into a table.
INSERT INTO table_name (column_1, column_2, column_3) VALUES (val_1, val_2, val_3);
//insert a new row into table_name, where each value corresponds to the correct data type

SELECT statements are used to fetch data from a table.
SELECT column_1 FROM table_name; //returns the value(s) in column_1
SELECT column_1 FROM table_name WHERE condition; //returns the value(s) in column_1 where the condition is met

Various key-words for Querying:
AS keyword: //used for renaming column_1
SELECT column_1 AS "Column 1 Name" FROM table_name;

DISTINCT keyword: //used for only showing unique items
SELECT DISTINCT column_1 from table_name;

LIKE (_) keyword: //allows you to query similar items
SELECT * FROM movies WHERE name LIKE "Se_en" //this would return both Seven and Se7en
LIKE (%) keyword: //a more flexible keyword for querying
SELECT * FROM movies WHERE name LIKE 'A%'; //this would return every movie that begins with "A"

IS NULL or IS NOT NULL keywords; //self-explanatory
SELECT name FROM movies WHERE year IS NOT NULL;

BETWEEN keyword;
SELECT name FROM movies WHERE name BETWEEN "A" AND "F"; //Important point to note: BETWEEN is NOT inclusive with letters but IS inclusive with numbers;

AND, OR operators also work as you would expect them to, often used after the WHERE clause for conditionals.

ORDER BY ASC/DESC/column_name; //this orders the queried results depending on the specified order
SELECT name, year, imdb_rating FROM movies ORDER BY imdb_rating DESC; //example that orders the query by descending rating

LIMIT keyword; // limits the result
SELECT * FROM movies LIMIT 100; //limits queried results to 100
SELECT * FROM movies ORDER BY imdb_rating DESC LIMIT 3; //this query returns the top 3 movies

CASE statements allow for "If-then" statement functionality, usually used in SELECT statements.
SELECT name,
 CASE
  WHEN genre = 'romance' THEN 'Chill'
  WHEN  genre = 'comedy' THEN 'Chill'
  ELSE 'Intense'
 END AS "Mood"
FROM movies;
//This query results in a new column named Mood, where each entry is either Chill or
Intense depending on the corresponding genre of that row.



ALTER statements are used to add a new column to a table
ALTER TABLE table_name ADD COLUMN column_4 data_type;

UPDATE statements edit a row in a table.
UPDATE table_name SET column_4 = some_val WHERE id = num;

DELETE statements delete one or more rows from a table.
DELETE FROM table_name WHERE some_condition;

Constraints add information regarding how a column can be used or changed. Common constraints:

CREATE TABLE celebs (
   id INTEGER PRIMARY KEY, //set id as PK, so no row can share the same id now
   name TEXT UNIQUE, //columns have a different value in every row. like PK, but tables can have many different unique columns
   date_of_birth TEXT NOT NULL, //cannot be NULL (must contain some data)
   date_of_death TEXT DEFAULT 'Not Applicable' //if not given data, the table will go with the default value
);





