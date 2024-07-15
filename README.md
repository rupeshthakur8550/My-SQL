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

- **Numeric**: `INT`, `DOUBLE`, `FLOAT`, `DECIMAL`
- **String**: `VARCHAR`
- **Date**

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
This constraint uniquely identifies each record in a table.

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
  PRIMARY KEY(COLUMN_NAME)
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

## **13. Clauses**
### **a. WHERE**
This clause is used to select specific records based on a condition from a table.

```sql
SELECT * FROM TABLE_NAME WHERE COLUMN_NAME = 'VALUE';
DELETE FROM TABLE_NAME WHERE COLUMN_NAME = 'VALUE';
UPDATE TABLE_NAME SET COLUMN_NAME = "VALUE" WHERE COLUMN_NAME = 'VALUE';
```

## **14. AUTO_INCREMENT**
This feature automatically generates a unique number when a new record is inserted into a table.

```sql
CREATE TABLE TABLE_NAME (
  COLUMN_NAME1 COLUMN_TYPE1 PRIMARY KEY AUTO_INCREMENT,
  COLUMN_NAME2 COLUMN_TYPE2,
  ...
  COLUMN_NAMEn COLUMN_TYPEn
);
```

## **15. ALIAS**
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

## **16. String Functions**
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
