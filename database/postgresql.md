# PostgreSQL

## Installation

* GUI Interface: [PSequel](http://www.psequel.com/)
* Homebrew:
  * Before running, remember to check Brew is up-to-date: `brew update; brew upgrade; brew cleanup; brew doctor`
  * Installation: `brew install postgresql`
  * Start and stop the database server: `brew services [start|stop] postgresql`
  * Create Database: `createdb 'YOUR_DATABASE_NAME'`
  * REPL Test: `psql 'YOUR_DATABASE_NAME'`

## **Commands**

```sql
-- Table Creation
CREATE TABLE table_name(column_1 type_1, column_2 type_2, ...);
​
-- Data Insertion
INSERT INTO table_name(column_1, column_2, ...) VALUES (value_1, value_2, ...);
​
-- Data Selection
SELECT column_1, column_2, ... FROM table_name;
​
-- Data Selection with all columns specified
SELECT * FROM table_name;
​
-- Data Update
UPDATE table_name
SET column_name = value
WHERE column_name = value [AND | OR column_name = value ...];
​
-- Data Deletion
DELETE FROM table_name WHERE column_name = value;
​
-- Table Deletion
DROP TABLE table_name;
​
-- Table Alteration
ALTER TABLE table_name ADD column_name type;
​
-- Conditional Queries
SELECT * FROM table_name WHERE column_name LIKE 'A%';       -- matchs 'A' + anything
SELECT * FROM table_name ORDER BY column_name [DESC | ASC]; -- sorting
​
-- SQL Functions
SELECT AVG(column_name) FROM table_name;   -- get the average value of a column
SELECT SUM(column_name) FROM table_name;   -- get the sum of a column
SELECT COUNT(value) FROM table_name;       -- count the data
​
-- Joining Table
SELECT * FROM table_name JOIN another_table ON table_name.intersected_column = another_table.intersected_column;
```

Available data types: [https://www.postgresql.org/docs/12/datatype.html](https://www.postgresql.org/docs/12/datatype.html)

