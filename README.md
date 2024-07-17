# **SQL Basics to Advanced Guide**

## **1. Create Database**
This query is used for the creation of a database in which we create tables.

```sql
CREATE DATABASE DATABASE_NAME;
```

## **2. Use Database**
This query is used for selecting a database in which we want to perform some actions.

```sql
USE DATABASE_NAME;
```

## **3. Show Databases**
This query is used to view all the databases in the current MySQL Workbench.

```sql
SHOW DATABASES;
```

## **4. Data Types in MySQL**
**Definition**: An attribute that specifies the type of data in a column of our database table. The most widely used data types are:

- **Numeric**: `INT`,`BIGINT(to store value more than 8 length)`, `DOUBLE`, `FLOAT`, `DECIMAL`
- **String**: `VARCHAR`
- **Date:** `DATE(YYYY-MM-DD)`, `TIME(HH:MM:SS)`, `DATETIME(YYYY-MM-DD HH:MM:SS)`, `CURDATE()`, `CURTIME()`, `NOW()`, `DAYNAME('DATE')`, `DAYOFMONTH('DATE')`, `DAYOFWEEK('DATE')`, `MONTHNAME('DATE')`, `HOUR('TIME')`, `DATE_FORMAT('DATE', 'FORMAT')`, `DATE_ADD('DATE', INTERVAL VALUE DAY | MONTH | YEAR)`, `DATE_SUB('DATE', INTERVAL VALUE DAY | MONTH | YEAR)`, `TIMEDIFF('TIME1', 'TIME2')`

**Date Examples:**
```sql
SELECT DATE_FORMAT(now(), '%D %a at %T'); -- Result: 16th Tue at 12:50:23
SELECT DATE_FORMAT(now(), '%m/%d/%y'); -- Result: 07/16/24
SELECT DATE_FORMAT(now(), '%r'); -- Result: 12:49:32 PM
```

## **5. Create Table**
This query is used for the creation of a table inside a selected database.

**Definition**: A table is a collection of related data held in a table format within a database.

```sql
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1,
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn
);

-- Example:
CREATE TABLE users (
  id INT AUTO_INCREMENT,
  name VARCHAR(100),
  email VARCHAR(100)
);
```

## **6. Describe Table Schema**
This query is used to get to know the schema of tables.

```sql
DESC TABLE_NAME;

-- Example:
DESC employees;
```

| Field  | Type         | Null | Key | Default   | Extra          |
|--------|--------------|------|-----|-----------|----------------|
| emp_id | int          | NO   | PRI | NULL      | auto_increment |
| name   | varchar(100) | NO   |     | NULL      |                |
| design | varchar(50)  | YES  |     | Probation |                |
| dept   | varchar(50)  | YES  |     | NULL      |                |

## **7. Adding Data into Table**
This query is used to add data into a table.

```sql
INSERT INTO TABLE_NAME VALUES
  (VALUE1, VALUE2, ...);

-- Or:

INSERT INTO TABLE_NAME (COLUMN_NAME1, COLUMN_NAME2, ...) VALUES
  (DATA1, DATA2, ...);
```

## **8. Reading from Database**
This query is used to get data from a required table.

```sql
SELECT * FROM TABLE_NAME;  -- To get all columns data

-- Or:

SELECT COLUMN_NAME1, COLUMN_NAME2, ... FROM TABLE_NAME;
```

## **9. Update on Table**
This query is used to update or modify existing data (records) in a required table.

```sql
UPDATE TABLE_NAME SET COLUMN_NAME = "VALUE" WHERE COLUMN_NAME = "RECORD_VALUE";
```

## **10. Delete on Table**
This query is used to delete records from a required table.

```sql
DELETE FROM TABLE_NAME WHERE COLUMN_NAME = "RECORD_VALUE";
```

**Note**: If the `WHERE` clause is omitted, all records will be deleted.

## **11. Delete Table or Database**
This query is used to delete an entire table or database along with its schema.

```sql
DROP TABLE TABLE_NAME;
DROP DATABASE DATABASE_NAME;
```

## **12. Constraints**
### **a. NOT NULL**
This constraint ensures that the column cannot have `NULL` values.

```sql
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1 NOT NULL,
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn
);
```

### **b. UNIQUE**
This constraint ensures that all values in a column are unique.

```sql
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1,
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn,
  UNIQUE(COLUMN_NAME1, COLUMN_NAME2, ...)
);
```

**Note**: Multiple columns can be assigned as unique.

### **c. DEFAULT**
This constraint assigns a default value to a column if no value is specified.

```sql
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1 DEFAULT 'VALUE',
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn
);
```

### **d. PRIMARY KEY**
This constraint is used for the below requirements:
1. The PRIMARY KEY constraint uniquely identifies each record in a table.
2. Primary keys must contain UNIQUE values, and cannot contain NULL values.
3. A table can have only ONE primary key.

```sql
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1 PRIMARY KEY,
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn
);

-- Or:

CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1,
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn,
  PRIMARY KEY (COLUMN_NAME)
);
```

### **e. FOREIGN KEY**

```sql
-- Define a foreign key
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1,
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn,
  FOREIGN KEY (COLUMN_NAME) REFERENCES OTHER_TABLE_NAME(OTHER_COLUMN_NAME)
);
```

### **f. CHECK**

```sql
-- Define a check constraint
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1 CHECK (COLUMN_NAME1 CONDITION),
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn
);
```

### **g. AUTO_INCREMENT**
This feature is used when you want to assign auto-indexing to record values of that column of Tables.

```sql
-- Define a auto_increment constraint
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1 PRIMARY KEY AUTO_INCREMENT,
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn
);
```

## 13. Clauses
### a. WHERE
This clause is used to select the particular record based on condition from Table.
**Example:**
```sql
SELECT * FROM users WHERE email = 'john.doe@example.com';
DELETE FROM users WHERE email = 'john.doe@example.com';
UPDATE users SET name = 'Johnathan Doe' WHERE email = 'john.doe@example.com';
```

**Operators with WHERE clause:**
- **Arithmetic Operators:** `+`, `-`, `*`, `/`, `%`
- **Comparison Operators:** `=`, `!=`, `>`, `>=`, `<`, `<=`
- **Logical Operators:** `AND`, `OR`, `IN`,`NOT IN`, `BETWEEN`, `ALL`, `IS NULL`, `LIKE`, `NOT LIKE`, `ANY`
- **Bitwise Operators:** `&`, `|`

### b. ORDER BY
This clause is used to arrange the result in ascending or descending order which is generated by select query.
**Example:**
```sql
SELECT * FROM users ORDER BY name;
SELECT * FROM users ORDER BY name DESC;
```

### c. LIMIT
This clause is used to add limitations to records fetch for select query.
**Example:**
```sql
SELECT * FROM employees LIMIT 5;
```

### d. OFFSET
This clause is used to specify from which row we want the data to be retrieved.
**Example:**
```sql
SELECT * FROM employees LIMIT 5 OFFSET 10;

-- OR

SELECT * FROM employees LIMIT 10, 5;
```

### e. GROUP BY
This clause is used to grouping the result generated by select query which is also distinct by default.

**Example:**
```sql
SELECT dept, COUNT(*) FROM employees GROUP BY dept;
```
Note - COLUMN_NAME must be same on both side and also if you are using more than one COLUMN_NAME then add all of them into group by side as well otherwise it throws error

## **14. ALIAS**
This is used to give a temporary name to a column or table in a query.

```sql
SELECT employees.design AS designation FROM employees;
```

| designation |
|-------------|
| Manager     |
| Manager     |
| Associate   |
| Accountant  |
| HR          |

## **15. String Functions**
### **i. CONCAT**
Concatenates two or more strings.

```sql
SELECT CONCAT('Hello', ' World');
SELECT CONCAT(COLUMN_NAME1, COLUMN_NAME2) AS TEMP_NAME FROM TABLE_NAME;
```

### **ii. CONCAT_WS**
Concatenates strings with a separator.

```sql
SELECT CONCAT_WS(',', 'Hello', 'World');
SELECT CONCAT_WS(',', COLUMN_NAME1, COLUMN_NAME2) AS TEMP_NAME FROM TABLE_NAME;
```

### **iii. LENGTH OR CHAR_LENGTH**
Returns the length of a string.

```sql
SELECT LENGTH('Hello World');
SELECT CHAR_LENGTH('Hello World');
```

### **iv. SUBSTRING**
Extracts a substring from a string.

```sql
SELECT SUBSTRING('Hello World', 1, 5);
```

### **v. UPPER**
Converts a string to uppercase.

```sql
SELECT UPPER('Hello World');
```

### **vi. LOWER**
Converts a string to lowercase.

```sql
SELECT LOWER('Hello World');
```

### **vii. REPLACE**
Replaces all occurrences of a substring within a string.

```sql
SELECT REPLACE('Hello World', 'World', 'Everyone');
```

### **viii. REVERSE**
Reverses the string.

```sql
SELECT REVERSE('Everyone');
```

### **ix. INSERT**
Inserts a string into another string at a specified position.

```sql
SELECT INSERT('Hello Wassup', 6, 0, 'Raju');
```

### **x. LEFT**
Returns the leftmost characters from a string.

```sql
SELECT LEFT('Abcdefghij', 3);
```

### **xi. RIGHT**
Returns the rightmost characters from a string.

```sql
SELECT RIGHT('Abcdefghij', 4);
```

### **xii. REPEAT**
Repeats a string a specified number of times.

```sql
SELECT REPEAT('o', 5);
```

### **xiii. TRIM**
Removes spaces from the beginning and end of a string.

```sql
SELECT TRIM('  Alright!  ');
```

## **16. DISTINCT Keyword**
This keyword is used to get the distinct records of a column from a table.

```sql
SELECT DISTINCT COLUMN_NAME FROM TABLE_NAME;
```

## **17. LIKE Operator**
This operator is used to check letters with the column records to match and return the result that only matches.

```sql
SELECT * FROM TABLE_NAME WHERE COLUMN_NAME LIKE 'A-Z% | a-z% | A_a'; 
```
- `%` -> column record should start with `A-Z` or `a-z` and can have infinite length or different words after the starting letter.
- `_` is used when you only want one letter to be filled with `a-z` or `A-Z` to match the string.

**Example:**
```sql
SELECT * FROM employees WHERE name LIKE 'P_u%';
```

| emp_id | name | design    | dept |
|--------|------|-----------|------|
|    103 | Paul | Associate | IT   |

## **18. Change Table Schema**

### a. Add Column
Adds a new column to a table.

```sql
ALTER TABLE table_name ADD column_name column_type [constraint];
```
**Example:**
```sql
ALTER TABLE users ADD age INT NOT NULL;
```

### b. Drop Column
Deletes a column from a table.

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```
**Example:**
```sql
ALTER TABLE users DROP COLUMN age;
```

### c. Modify Column
Changes the data type of a column.

```sql
ALTER TABLE table_name MODIFY COLUMN column_name new_column_type [constraint];
```
**Example:**
```sql
ALTER TABLE users MODIFY COLUMN name VARCHAR(150);
```

### d. Rename Column
Renames a column in a table.

```sql
ALTER TABLE table_name CHANGE COLUMN old_column_name new_column_name column_type;
```
**Example:**
```sql
ALTER TABLE users CHANGE COLUMN old_name new_name VARCHAR(100);
```

### e. Rename Table
Renames a table.

```sql
ALTER TABLE old_table_name RENAME TO new_table_name;
```
**Example:**
```sql
ALTER TABLE employees RENAME TO staff;
```

## **19. Aggregate Functions**

```sql
SELECT SUM(column_name) FROM table_name;
SELECT MIN(column_name) FROM table_name;
SELECT MAX(column_name) FROM table_name;
SELECT COUNT(column_name) FROM table_name;
SELECT AVG(column_name) FROM table_name;
```

## **20. CASE in MY SQL**

```sql
SELECT COLUMN_NAMES, 
		CASE
			WHEN COLUMN_NAME CONDITION THEN VALUE
			ELSE VALUE
		END AS NEW_COLUMN_NAME	
		FROM TABLE_NAME;
```

Example - LeetCode (1661)

``` sql
SELECT machine_id,ROUND(
		AVG(
        	CASE 
            		WHEN activity_type = 'start' THEN -timestamp
            		ELSE timestamp
        	END
    		) * 2,
   		 3 
	) AS processing_time FROM Activity GROUP BY machine_id;
```
Note for question - 2 is the partition as which start and end makes 1 partition here we have 2 partition for each

Note - You can add multiple WHEN as per requirements and skip ELSE.


