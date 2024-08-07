# **SQL Basics to Advanced Guide**

## **1. Create Database**
This query is used for the creation of a database in which we create tables.

```sql
CREATE DATABASE DATABASE_NAME;
```

Example - 
```sql
CREATE DATABASE Practice;
```

## **2. Use Database**
This query is used for selecting a database in which we want to perform some actions.

```sql
USE DATABASE_NAME;
```

Example - 
```sql
USE Practice;
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

1. **DATE(YYYY-MM-DD)**: Extracts the date part of a date or datetime expression.
    ```sql
    SELECT DATE('2024-07-16 12:30:45'); -- Result: 2024-07-16
    ```

2. **TIME(HH:MM:SS)**: Extracts the time part of a time or datetime expression.
    ```sql
    SELECT TIME('2024-07-16 12:30:45'); -- Result: 12:30:45
    ```

3. **DATETIME(YYYY-MM-DD HH:MM:SS)**: Represents a datetime value.
    ```sql
    SELECT '2024-07-16 12:30:45' AS datetime_value; -- Result: 2024-07-16 12:30:45
    ```

4. **CURDATE()**: Returns the current date.
    ```sql
    SELECT CURDATE(); -- Result: 2024-07-16
    ```

5. **CURTIME()**: Returns the current time.
    ```sql
    SELECT CURTIME(); -- Result: 12:30:45
    ```

6. **NOW()**: Returns the current date and time.
    ```sql
    SELECT NOW(); -- Result: 2024-07-16 12:30:45
    ```

7. **DAYNAME('DATE')**: Returns the name of the weekday for the given date.
    ```sql
    SELECT DAYNAME('2024-07-16'); -- Result: Tuesday
    ```

8. **DAYOFMONTH('DATE')**: Returns the day of the month for the given date.
    ```sql
    SELECT DAYOFMONTH('2024-07-16'); -- Result: 16
    ```

9. **DAYOFWEEK('DATE')**: Returns the day of the week for the given date (1 = Sunday, 7 = Saturday).
    ```sql
    SELECT DAYOFWEEK('2024-07-16'); -- Result: 3 (Tuesday)
    ```

10. **MONTHNAME('DATE')**: Returns the name of the month for the given date.
    ```sql
    SELECT MONTHNAME('2024-07-16'); -- Result: July
    ```

11. **HOUR('TIME')**: Returns the hour part of the given time.
    ```sql
    SELECT HOUR('12:30:45'); -- Result: 12
    ```

12. **DATE_FORMAT('DATE', 'FORMAT')**: Formats the date according to the specified format.
    ```sql
    SELECT DATE_FORMAT(now(), '%D %a at %T'); -- Result: 16th Tue at 12:50:23
    SELECT DATE_FORMAT(now(), '%m/%d/%y'); -- Result: 07/16/24
    SELECT DATE_FORMAT(now(), '%r'); -- Result: 12:49:32 PM
    ```

13. **DATE_ADD('DATE', INTERVAL VALUE DAY | MONTH | YEAR)**: Adds a time interval to a date.
    ```sql
    SELECT DATE_ADD('2024-07-16', INTERVAL 10 DAY); -- Result: 2024-07-26
    SELECT DATE_ADD('2024-07-16', INTERVAL 1 MONTH); -- Result: 2024-08-16
    SELECT DATE_ADD('2024-07-16', INTERVAL 1 YEAR); -- Result: 2025-07-16
    ```

14. **DATE_SUB('DATE', INTERVAL VALUE DAY | MONTH | YEAR)**: Subtracts a time interval from a date.
    ```sql
    SELECT DATE_SUB('2024-07-16', INTERVAL 10 DAY); -- Result: 2024-07-06
    SELECT DATE_SUB('2024-07-16', INTERVAL 1 MONTH); -- Result: 2024-06-16
    SELECT DATE_SUB('2024-07-16', INTERVAL 1 YEAR); -- Result: 2023-07-16
    ```

15. **TIMEDIFF('TIME1', 'TIME2')**: Returns the difference between two times.
    ```sql
    SELECT TIMEDIFF('12:30:45', '11:30:45'); -- Result: 01:00:00
    ```

16. **YEAR('DATE')**: Returns the year part of a date.
    ```sql
    SELECT YEAR('2024-07-16'); -- Result: 2024
    ```

17. **MONTH('DATE')**: Returns the month part of a date.
    ```sql
    SELECT MONTH('2024-07-16'); -- Result: 7
    ```

18. **DAY('DATE')**: Returns the day part of a date.
    ```sql
    SELECT DAY('2024-07-16'); -- Result: 16
    ```

19. **MINUTE('TIME')**: Returns the minute part of a time.
    ```sql
    SELECT MINUTE('12:30:45'); -- Result: 30
    ```

20. **SECOND('TIME')**: Returns the second part of a time.
    ```sql
    SELECT SECOND('12:30:45'); -- Result: 45
    ```

21. **WEEK('DATE')**: Returns the week number of a date (1-53).
    ```sql
    SELECT WEEK('2024-07-16'); -- Result: 29
    ```

22. **QUARTER('DATE')**: Returns the quarter of the year for a date (1-4).
    ```sql
    SELECT QUARTER('2024-07-16'); -- Result: 3
    ```

23. **DATEDIFF('DATE1', 'DATE2')**: Returns the difference in days between two dates.
    ```sql
    SELECT DATEDIFF('2024-07-16', '2024-07-01'); -- Result: 15
    ```

24. **LAST_DAY('DATE')**: Returns the last day of the month for the given date.
    ```sql
    SELECT LAST_DAY('2024-07-16'); -- Result: 2024-07-31
    ```

25. **EXTRACT(unit FROM 'DATE')**: Extracts part of a date.
    ```sql
    SELECT EXTRACT(YEAR FROM '2024-07-16'); -- Result: 2024
    SELECT EXTRACT(MONTH FROM '2024-07-16'); -- Result: 7
    SELECT EXTRACT(DAY FROM '2024-07-16'); -- Result: 16
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
```

### **Constraints : -**
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
This constraint is used for the below requirements:
1. The FOREIGN KEY constraint is used to link two tables together.
2. A FOREIGN KEY in one table points to a PRIMARY KEY in another table, ensuring referential integrity.
3. FOREIGN KEYs can have duplicate values and can contain NULL values.

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

Example -
``` sql
CREATE TABLE employees (
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    mobile_no BIGINT,
    employee_id INT,
    manager_id INT,
    salary INT NOT NULL,
    department VARCHAR(20) NOT NULL DEFAULT 'Management',
    PRIMARY KEY (id),
    CONSTRAINT chk_mobile_no CHECK (LENGTH(CAST(mobile_no AS CHAR)) >= 10),
    CONSTRAINT chk_employee_id CHECK (employee_id >= 12)
    FOREIGN KEY (department) REFERENCES departments(dept_id)
);
```

## **6. Describe Table Schema**
This query is used to get to know the schema of tables.

```sql
DESC TABLE_NAME;
```

Example -
``` sql
DESC employees;
```
Result - 
```
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| id          | int          | NO   | PRI | NULL    | auto_increment |
| name        | varchar(100) | NO   |     | NULL    |                |
| email       | varchar(100) | YES  | UNI | NULL    |                |
| mobile_no   | bigint       | YES  |     | NULL    |                |
| employee_id | int          | YES  |     | NULL    |                |
| manager_id  | int          | YES  |     | NULL    |                |
| salary      | int          | NO   |     | NULL    |                |
| department  | varchar(20)  | NO   |     | NULL    |                |
+-------------+--------------+------+-----+---------+----------------+
```

## **7. Adding Data into Table**
This query is used to add data into a Table.

```sql
INSERT INTO TABLE_NAME VALUES
  (VALUE1, VALUE2, ...);

-- Or:

INSERT INTO TABLE_NAME (COLUMN_NAME1, COLUMN_NAME2, ...) VALUES
  (DATA1, DATA2, ...);
```
Ezample -

``` sql
INSERT INTO employees (name, email, mobile_no, employee_id, manager_id, salary, department) VALUES
('John Doe', 'john.doe@example.com', 1234567890, 12, 1, 50000, 'HR'),
('Jane Smith', 'jane.smith@example.com', 2345678901, 13, 1, 60000, 'IT'),
('Alice Johnson', 'alice.johnson@example.com', 3456789012, 14, 2, 55000, 'Finance'),
('Bob Brown', 'bob.brown@example.com', 4567890123, 15, 2, 52000, 'Marketing'),
('Charlie Davis', 'charlie.davis@example.com', 5678901234, 16, 3, 48000, 'HR'),
('Dana White', 'dana.white@example.com', 6789012345, 17, 3, 63000, 'IT'),
('Evan Green', 'evan.green@example.com', 7890123456, 18, 4, 49000, 'Finance'),
('Fiona Black', 'fiona.black@example.com', 8901234567, 19, 4, 57000, 'Marketing'),
('George Harris', 'george.harris@example.com', 9012345678, 20, 5, 52000, 'HR'),
('Holly Evans', 'holly.evans@example.com', 9123456789, 21, 5, 61000, 'IT'),
('Ivy Collins', 'ivy.collins@example.com', 1234567899, 22, 6, 48000, 'Finance'),
('Jack Lewis', 'jack.lewis@example.com', 2345678909, 23, 6, 54000, 'Marketing');
```

## **8. Reading from Database**
This query is used to get data from a required table.

```sql
SELECT * FROM TABLE_NAME;  -- To get all columns data

-- Or:

SELECT COLUMN_NAME1, COLUMN_NAME2, ... FROM TABLE_NAME;
```

``` sql
SELECT * FROM employees;
```
Result -
```
+----+---------------+---------------------------+------------+-------------+------------+--------+------------+
| id | name          | email                     | mobile_no  | employee_id | manager_id | salary | department |
+----+---------------+---------------------------+------------+-------------+------------+--------+------------+
| 13 | John Doe      | john.doe@example.com      | 1234567890 |          12 |          1 |  50000 | HR         |
| 14 | Jane Smith    | jane.smith@example.com    | 2345678901 |          13 |          1 |  60000 | IT         |
| 15 | Alice Johnson | alice.johnson@example.com | 3456789012 |          14 |          2 |  55000 | Finance    |
| 16 | Bob Brown     | bob.brown@example.com     | 4567890123 |          15 |          2 |  52000 | Marketing  |
| 17 | Charlie Davis | charlie.davis@example.com | 5678901234 |          16 |          3 |  48000 | HR         |
| 18 | Dana White    | dana.white@example.com    | 6789012345 |          17 |          3 |  63000 | IT         |
| 19 | Evan Green    | evan.green@example.com    | 7890123456 |          18 |          4 |  49000 | Finance    |
| 20 | Fiona Black   | fiona.black@example.com   | 8901234567 |          19 |          4 |  57000 | Marketing  |
| 21 | George Harris | george.harris@example.com | 9012345678 |          20 |          5 |  52000 | HR         |
| 22 | Holly Evans   | holly.evans@example.com   | 9123456789 |          21 |          5 |  61000 | IT         |
| 23 | Ivy Collins   | ivy.collins@example.com   | 1234567899 |          22 |          6 |  48000 | Finance    |
| 24 | Jack Lewis    | jack.lewis@example.com    | 2345678909 |          23 |          6 |  54000 | Marketing  |
+----+---------------+---------------------------+------------+-------------+------------+--------+------------+
```

## **9. Update on Table**
This query is used to update or modify existing data (records) in a required table.

```sql
UPDATE TABLE_NAME SET COLUMN_NAME = "VALUE" WHERE COLUMN_NAME = "RECORD_VALUE";
```

Example -
```sql
UPDATE employees SET mobile_no = 9284438702 WHERE name = 'John Doe';
```

## **10. Delete on Table**
This query is used to delete records from a required table.

```sql
DELETE FROM TABLE_NAME WHERE COLUMN_NAME = "RECORD_VALUE";
```

Example -
```sql
DELETE FROM employees WHERE email = "jack.lewis@example.com";
```

**Note**: If the `WHERE` clause is omitted, all records will be deleted.

## **11. Delete Table or Database**
This query is used to delete an entire table or database along with its schema.

```sql
DROP TABLE TABLE_NAME;
DROP DATABASE DATABASE_NAME;
```

Example -
```sql
DROP TABLE employees;
DROP DATABASE Practice;
```

## 12. Clauses
### a. WHERE
This clause is used to select the particular record based on condition from Table.
**Example:**
```sql
SELECT * FROM employees WHERE email = 'john.doe@example.com';
DELETE FROM employees WHERE email = 'john.doe@example.com';
UPDATE employees SET name = 'Johnathan Doe' WHERE email = 'john.doe@example.com';
```

**Operators with WHERE clause:**
- **Arithmetic Operators:** `+`, `-`, `*`, `/`, `%`
- **Comparison Operators:** `=`, `!= or <>`, `>`, `>=`, `<`, `<=`
- **Logical Operators:** `AND`, `OR`, `IN`,`NOT IN`, `BETWEEN`, `ALL`, `IS NULL`, `LIKE`, `NOT LIKE`, `ANY`
- **Bitwise Operators:** `&`, `|`

Examples for Operators- 
### Arithmetic Operators

1. **Addition (`+`)**: Calculate the total salary of two employees.
   ```sql
   SELECT name, salary + 5000 AS increased_salary
   FROM employees
   WHERE name = 'John Doe';
   ```

2. **Subtraction (`-`)**: Calculate the difference between the highest and lowest salaries.
   ```sql
   SELECT MAX(salary) - MIN(salary) AS salary_difference
   FROM employees;
   ```

3. **Multiplication (`*`)**: Calculate the annual salary of an employee.
   ```sql
   SELECT name, salary * 12 AS annual_salary
   FROM employees
   WHERE name = 'Jane Smith';
   ```

4. **Division (`/`)**: Calculate the average monthly salary of an employee.
   ```sql
   SELECT name, salary / 12 AS average_monthly_salary
   FROM employees
   WHERE name = 'Alice Johnson';
   ```

5. **Modulus (`%`)**: Find employees whose employee_id is an odd number.
   ```sql
   SELECT name
   FROM employees
   WHERE employee_id % 2 != 0;
   ```

### Comparison Operators

1. **Equal (`=`)**: Find the employee with a specific employee_id.
   ```sql
   SELECT *
   FROM employees
   WHERE employee_id = 12;
   ```

2. **Not Equal (`!= or <>`)**: Find employees not in the IT department.
   ```sql
   SELECT *
   FROM employees
   WHERE department != 'IT';
   ```

3. **Greater Than (`>`)**: Find employees with a salary greater than 50000.
   ```sql
   SELECT *
   FROM employees
   WHERE salary > 50000;
   ```

4. **Greater Than or Equal (`>=`)**: Find employees with a salary greater than or equal to 60000.
   ```sql
   SELECT *
   FROM employees
   WHERE salary >= 60000;
   ```

5. **Less Than (`<`)**: Find employees with a salary less than 50000.
   ```sql
   SELECT *
   FROM employees
   WHERE salary < 50000;
   ```

6. **Less Than or Equal (`<=`)**: Find employees with a salary less than or equal to 55000.
   ```sql
   SELECT *
   FROM employees
   WHERE salary <= 55000;
   ```

### Logical Operators

1. **AND**: Find employees in the IT department with a salary greater than 60000.
   ```sql
   SELECT *
   FROM employees
   WHERE department = 'IT' AND salary > 60000;
   ```

2. **OR**: Find employees in either the HR or Finance departments.
   ```sql
   SELECT *
   FROM employees
   WHERE department = 'HR' OR department = 'Finance';
   ```

3. **IN**: Find employees in specified departments.
   ```sql
   SELECT *
   FROM employees
   WHERE department IN ('HR', 'IT', 'Finance');
   ```

4. **NOT IN**: Find employees not in specified departments.
   ```sql
   SELECT *
   FROM employees
   WHERE department NOT IN ('HR', 'IT', 'Finance');
   ```

5. **BETWEEN**: Find employees with a salary between 50000 and 60000.
   ```sql
   SELECT *
   FROM employees
   WHERE salary BETWEEN 50000 AND 60000;
   ```

6. **ALL**: Find employees with a salary greater than all salaries in the HR department.
   ```sql
   SELECT *
   FROM employees
   WHERE salary > ALL (SELECT salary FROM employees WHERE department = 'HR');
   ```

7. **IS NULL**: Find employees with no assigned manager.
   ```sql
   SELECT *
   FROM employees
   WHERE manager_id IS NULL;
   ```

8. **LIKE**: Find employees whose email ends with 'example.com'.
   ```sql
   SELECT *
   FROM employees
   WHERE email LIKE '%@example.com';
   ```

9. **NOT LIKE**: Find employees whose email does not end with 'example.com'.
   ```sql
   SELECT *
   FROM employees
   WHERE email NOT LIKE '%@example.com';
   ```

10. **ANY**: Find employees with a salary greater than any employee in the HR department.
    ```sql
    SELECT *
    FROM employees
    WHERE salary > ANY (SELECT salary FROM employees WHERE department = 'HR');
    ```

### Bitwise Operators

1. **Bitwise AND (`&`)**: Find employees with a specific bit pattern in their employee_id.
   ```sql
   SELECT *
   FROM employees
   WHERE employee_id & 1 = 1; -- Check if the least significant bit is set (odd employee_id)
   ```

2. **Bitwise OR (`|`)**: Use bitwise OR to set a specific bit in an employee_id.
   ```sql
   SELECT name, employee_id | 2 AS modified_employee_id
   FROM employees;
   ```
   
### b. ORDER BY
This clause is used to arrange the result in ascending or descending order which is generated by select query.
```sql
SELECT * FROM TBALE_NAME ORDER BY COLUMN_NAME;
SELECT * FROM TABLE_NAME ORDER BY COLUMN_NAME DESC;
```

Example -
```sql
SELECT * FROM employees ORDER BY name;
SELECT * FROM employees ORDER BY salary DESC;
```

### c. LIMIT
This clause is used to add limitations to records fetch for select query.
```sql
SELECT * FROM TABLE_NAME LIMIT VALUE;
```

Example - 
```sql
SELECT * FROM employees LIMIT 5;
Result returns top 5 records
```

### d. OFFSET
This clause is used to specify from which row we want the data to be retrieved.
```sql
SELECT * FROM TABLE_NAME LIMIT VALUE OFFSET VALUE;

-- OR

SELECT * FROM TABLE_NAME LIMIT OFFSET_VALUE, VALUE;
```

Example -
``` sql
SELECT * FROM employees ORDER BY salary LIMIT 1 OFFSET 4;

-- OR

SELECT * FROM employees ORDER BY salary LIMIT 4, 1;
Formula Nth record - LIMIT N-1, 1; OR LIMIT 1 OFFSET N-1;
```

### e. GROUP BY
This clause is used to grouping the result generated by select query which is also distinct by default.
```sql
SELECT COLUMN_NAME, COUNT(*) FROM TABLE_NAME GROUP BY COLUMN_NAME;
```

Example -
```sql
SELECT department, COUNT(*) FROM employees GROUP BY department;
```

Note - 
1. COLUMN_NAME must be same on both side and also if you are using more than one COLUMN_NAME then add all of them into group by side as well otherwise it throws error.
2. It return distinct record by default.

### f. HAVING 

The `HAVING` clause is used to filter groups based on a condition, typically after the groups are created with the `GROUP BY` clause. It is similar to the `WHERE` clause, but `HAVING` is used for filtering groups, whereas `WHERE` is used for filtering individual rows.

```sql
SELECT COLUMN_NAME, COUNT(*)
FROM TABLE_NAME
GROUP BY COLUMN_NAME
HAVING condition;
```

Example -

```sql
SELECT department, COUNT(*) as dept_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 2;
```

## **13. ALIAS**
This is used to give a temporary name to a column in a query.
```sql
SELECT COLUMN_NAME AS REFERENCE_COLUMN_NAME FROM TABLE_NAME;
```

Example -
``` sql
SELECT department, COUNT(*) AS employee_count FROM employees GROUP BY department;
```
Result -
```
+------------+----------------+
| department | employee_count |
+------------+----------------+
| HR         |              3 |
| IT         |              3 |
| Finance    |              3 |
| Marketing  |              3 |
+------------+----------------+
```

## **14. String Functions**
### **i. CONCAT**
Concatenates two or more strings.

```sql
SELECT CONCAT('Hello',' World'); -- Result: Hello World
```

### **ii. CONCAT_WS**
Concatenates strings with a separator.

```sql
SELECT CONCAT_WS(',', 'Hello', ' World'); -- Result: Hello, World
```

### **iii. LENGTH OR CHAR_LENGTH**
Returns the length of a string.

```sql
SELECT LENGTH('Hello World'); -- Result: 11
SELECT CHAR_LENGTH('Hello World'); -- Result: 11
```

### **iv. SUBSTRING**
Extracts a substring from a string.

```sql
SELECT SUBSTRING('Hello World', 1, 5); -- Result:  Hello
```

### **v. UPPER**
Converts a string to uppercase.

```sql
SELECT UPPER('Hello World'); -- Result: HELLO WORLD
```

### **vi. LOWER**
Converts a string to lowercase. 

```sql
SELECT LOWER('Hello World'); -- Result: hello world
```

### **vii. REPLACE**
Replaces all occurrences of a substring within a string.

```sql
SELECT REPLACE('Hello World', 'World', 'Everyone'); -- Result:  Hello Everyone
```

### **viii. REVERSE**
Reverses the string.

```sql
SELECT REVERSE('Everyone'); -- Result:  enoyrevE
```

### **ix. INSERT**
Inserts a string into another string at a specified position.

```sql
SELECT INSERT('Hello Wassup', 6, 0, ' Prakash'); -- Result:  Hello Prakash Wassup 
```

### **x. LEFT**
Returns the leftmost characters from a string.

```sql
SELECT LEFT('Abcdefghij', 3); -- Result: Abc 
```

### **xi. RIGHT**
Returns the rightmost characters from a string.

```sql
SELECT RIGHT('Abcdefghij', 4); -- ghij
```

### **xii. REPEAT**
Repeats a string a specified number of times.

```sql
SELECT REPEAT('o', 5); -- Result: ooooo
```

### **xiii. TRIM**
Removes spaces from the beginning and end of a string.

```sql
SELECT TRIM('  Alright!  '); -- Result: Alright 
```

## **15. DISTINCT Keyword**
This keyword is used to get the distinct records of a column from a table.

```sql
SELECT DISTINCT COLUMN_NAME FROM TABLE_NAME;
```

Example -
```sql
SELECT DISTINCT department FROM employees;
```

## **16. LIKE Operator**
This operator is used to check letters with the column records to match and return the result that only matches.

```sql
SELECT * FROM TABLE_NAME WHERE COLUMN_NAME LIKE 'A-Z% | a-z% | A_a'; 
```
- `%` -> column record should start with `A-Z` or `a-z` and can have infinite length or different words after the starting letter.
- `_` is used when you only want one letter to be filled with `a-z` or `A-Z` to match the string.

**Example:**
```sql
 SELECT * FROM employees WHERE name LIKE '_a%';
```
Resukt -
```
+----+------------+------------------------+------------+-------------+------------+--------+------------+
| id | name       | email                  | mobile_no  | employee_id | manager_id | salary | department |
+----+------------+------------------------+------------+-------------+------------+--------+------------+
| 14 | Jane Smith | jane.smith@example.com | 2345678901 |          13 |          1 |  60000 | IT         |
| 18 | Dana White | dana.white@example.com | 6789012345 |          17 |          3 |  63000 | IT         |
| 24 | Jack Lewis | jack.lewis@example.com | 2345678909 |          23 |          6 |  54000 | Marketing  |
+----+------------+------------------------+------------+-------------+------------+--------+------------+
```

## **17. Change Table Schema**

### a. Add Column
Adds a new column to a table.

```sql
ALTER TABLE table_name ADD column_name column_type [constraint];
```
**Example:**
```sql
ALTER TABLE empployees ADD HR_id BIGINT NOT NULL;
```

### b. Drop Column
Deletes a column from a table.

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```
**Example:**
```sql
ALTER TABLE employees DROP COLUMN HR_id;
```

### c. Modify Column
Changes the data type of a column.

```sql
ALTER TABLE table_name MODIFY column_name new_column_type [constraint];
```
**Example:**
```sql
ALTER TABLE employees MODIFY mobile_no INT;
```

### d. Rename Column
Renames a column in a table.

```sql
ALTER TABLE table_name CHANGE old_column_name new_column_name column_type;
```
**Example:**
```sql
ALTER TABLE employees CHANGE department dept_id VARCHAR(100);
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

## **18. Aggregate Functions**

```sql
SELECT SUM(column_name) FROM table_name;
SELECT MIN(column_name) FROM table_name;
SELECT MAX(column_name) FROM table_name;
SELECT COUNT(column_name) FROM table_name;
SELECT AVG(column_name) FROM table_name;
```

Examples -

```sql
SELECT dept_name, SUM(salary) FROM employees GROUP BY dept_name;
SELECT MIN(salary) FROM employees;
SELECT MAX(salary) FROM employees;
SELECT dept_name, COUNT(salary) as employee_count FROM employees GROUP BY dept_name;
SELECT dept_name, AVG(salary) FROM employees GROUP BY dept_name;
```
## **19. CASE in MY SQL**

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
	) * 2,3)
AS processing_time FROM Activity GROUP BY machine_id;

Note for question : 2 is the partition as start and end makes 1 partition here we have 2 partition for each
```
**Note - You can add multiple WHEN as per requirements and skip ELSE.**

---

## **20. Indexes in MySQL**

Indexes are used to improve the speed of data retrieval operations on a database table at the cost of additional storage and slower write operations.

#### Creating Indexes

**Creating Index with Table Creation**

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...,
    INDEX index_name (column_name)
);
```

**Example:**

```sql
CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(100),
    INDEX idx_department (department)
);
```

**Creating Index After Table Creation**

```sql
CREATE INDEX index_name ON table_name (column_name);
```

**Example:**

```sql
CREATE INDEX idx_department ON employees (department);
```

#### Types of Indexes

1. **Primary Key Index**
   - Automatically created when defining a primary key.
   ```sql
   CREATE TABLE employees (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(100)
   );
   ```

2. **Unique Index**
   - Ensures all values in a column are distinct.
   ```sql
   CREATE UNIQUE INDEX index_name ON table_name (column_name);
   ```
   **Example:**
   ```sql
   CREATE UNIQUE INDEX idx_employee_id ON employees (id);
   ```

3. **Full-Text Index**
   - Used for text searching.
   ```sql
   CREATE FULLTEXT INDEX index_name ON table_name (column_name);
   ```
   **Example:**
   ```sql
   CREATE FULLTEXT INDEX idx_name ON employees (name);
   ```

4. **Composite Index**
   - Index based on multiple columns.
   ```sql
   CREATE INDEX index_name ON table_name (column1, column2);
   ```
   **Example:**
   ```sql
   CREATE INDEX idx_name_department ON employees (name, department);
   ```

5. **Spatial Index**
   - Used for spatial data types like geometry.
   ```sql
   CREATE SPATIAL INDEX index_name ON table_name (column_name);
   ```
   **Example:**
   ```sql
   CREATE SPATIAL INDEX idx_location ON geo_table (location);
   ```

#### Viewing Indexes 

**List All Indexes in a Table**

```sql
SHOW INDEX FROM table_name;
```

---

## **21.  Views in MySQL**

A view is a virtual table based on the result-set of an SQL statement. Views can simplify complex queries, enhance security, and provide a layer of abstraction.

#### Creating a View

```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Example:**

```sql
CREATE VIEW employee_view AS
SELECT id, name, department
FROM employees
WHERE department = 'Engineering';
```

#### Using a View

```sql
SELECT * FROM view_name;
```

**Example:**

```sql
SELECT * FROM employee_view;
```

#### Updating a View

```sql
CREATE OR REPLACE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Example:**

```sql
CREATE OR REPLACE VIEW employee_view AS
SELECT id, name, department
FROM employees
WHERE department = 'Sales';
```

#### Dropping a View

```sql
DROP VIEW view_name;
```

**Example:**

```sql
DROP VIEW employee_view;
```

---

## **22. Subqueries in MySQL**

A subquery is a query nested inside another query. It can be used in `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statements or inside another subquery.

#### Types of Subqueries

1. **Single Row Subquery**
   - Returns a single row.
   ```sql
   SELECT column1
   FROM table1
   WHERE column2 = (SELECT column2 FROM table2 WHERE condition);
   ```

   **Example:**

   ```sql
   SELECT name
   FROM employees
   WHERE department_id = (SELECT id FROM departments WHERE name = 'HR');
   ```

2. **Multiple Row Subquery**
   - Returns multiple rows.
   ```sql
   SELECT column1
   FROM table1
   WHERE column2 IN (SELECT column2 FROM table2 WHERE condition);
   ```

   **Example:**

   ```sql
   SELECT name
   FROM employees
   WHERE department_id IN (SELECT id FROM departments WHERE location = 'New York');
   ```

3. **Correlated Subquery**
   - References columns from the outer query.
   ```sql
   SELECT column1
   FROM table1 t1
   WHERE column2 = (SELECT column2 FROM table2 t2 WHERE t2.column3 = t1.column3);
   ```

   **Example:**

   ```sql
   SELECT e1.name
   FROM employees e1
   WHERE e1.salary > (SELECT AVG(e2.salary) FROM employees e2 WHERE e2.department_id = e1.department_id);
   ```

#### Using Subqueries

**Subquery in SELECT Clause**

```sql
SELECT column1,
    (SELECT column2 FROM table2 WHERE condition) AS alias_name
FROM table1;
```

**Example:**

```sql
SELECT name,
    (SELECT COUNT(*) FROM tasks WHERE tasks.employee_id = employees.id) AS task_count
FROM employees;
```

**Subquery in FROM Clause**

```sql
SELECT alias_name.column1
FROM (SELECT column1 FROM table2 WHERE condition) AS alias_name;
```

**Example:**

```sql
SELECT subquery.department, COUNT(*)
FROM (SELECT department FROM employees WHERE salary > 50000) AS subquery
GROUP BY subquery.department;
```
---
### **23. MySQL Comparison Functions**

MySQL provides several functions to compare values and handle NULL values effectively. Below are explanations and examples of `COALESCE`, `IFNULL`, `GREATEST`, `LEAST`, and `ISNULL`.

#### **COALESCE**

The `COALESCE` function returns the first non-NULL value in the list of arguments. It can take two or more arguments.

```sql
SELECT COALESCE(column1, column2, 'default_value') AS result
FROM table_name;
```

**Example:**

```sql
SELECT name,
    COALESCE(email, 'noemail@example.com') AS contact_email
FROM employees;
```

#### **IFNULL**

The `IFNULL` function returns the first argument if it is not NULL, otherwise, it returns the second argument.

```sql
SELECT IFNULL(column1, 'default_value') AS result
FROM table_name;
```

**Example:**

```sql
SELECT name,
    IFNULL(phone, 'No phone number') AS contact_phone
FROM employees;
```

**NOTE - 1. COALESCE is used for more than 2 arguments and IFNULL for 2 only. 
	 2. They both are used to handle NULL value in Query Result**
#### **GREATEST**

The `GREATEST` function returns the greatest value from the list of arguments.

```sql
SELECT GREATEST(column1, column2, column3, ...) AS greatest_value
FROM table_name;
```

**Example:**

```sql
SELECT name,
    GREATEST(salary_2022, salary_2023) AS max_salary
FROM employees;
```

#### **LEAST**

The `LEAST` function returns the smallest value from the list of arguments.

```sql
SELECT LEAST(column1, column2, column3, ...) AS least_value
FROM table_name;
```

**Example:**

```sql
SELECT name,
    LEAST(salary_2022, salary_2023) AS min_salary
FROM employees;
```

**Note - If NULL is there Then Both returns NULL without comparing values, to handle this use IFNULL(val, 0)**

#### **ISNULL**

The `ISNULL` function checks if a value is NULL. It returns 1 if the value is NULL, otherwise it returns 0.

```sql
SELECT ISNULL(column_name) AS is_null
FROM table_name;
```

**Example:**

```sql
SELECT name,
    ISNULL(phone) AS phone_missing
FROM employees;
```
---

## **24. MySQL Joins**

1. **Cross Join**:
   - Every row from one table is combined with every row from another table.
   ```sql
   SELECT * FROM TABLE1_NAME CROSS JOIN TABLE2_NAME;
   ```
   - Example:
   ```sql
   SELECT e1.name, e1.dept_name, d1.id, d1.manager_name 
   FROM employees e1 
   CROSS JOIN department d1;
   ```
   - Result:
   ```
   +---------------+-----------+----+---------------+
   | name          | dept_name | id | manager_name  |
   +---------------+-----------+----+---------------+
   | John Doe      | HR        |  3 | Fiona Black   |
   | John Doe      | HR        |  2 | Dana White    |
   | John Doe      | HR        |  1 | Charlie Davis |
   | Jane Smith    | IT        |  3 | Fiona Black   |
   | Jane Smith    | IT        |  2 | Dana White    |
   | Jane Smith    | IT        |  1 | Charlie Davis |
   | Alice Johnson | Finance   |  3 | Fiona Black   |
   | Alice Johnson | Finance   |  2 | Dana White    |
   | Alice Johnson | Finance   |  1 | Charlie Davis |
   | Bob Brown     | Marketing |  3 | Fiona Black   |
   | Bob Brown     | Marketing |  2 | Dana White    |
   | Bob Brown     | Marketing |  1 | Charlie Davis |
   | Charlie Davis | HR        |  3 | Fiona Black   |
   | Charlie Davis | HR        |  2 | Dana White    |
   | Charlie Davis | HR        |  1 | Charlie Davis |
   | Dana White    | IT        |  3 | Fiona Black   |
   | Dana White    | IT        |  2 | Dana White    |
   | Dana White    | IT        |  1 | Charlie Davis |
   | Evan Green    | Finance   |  3 | Fiona Black   |
   | Evan Green    | Finance   |  2 | Dana White    |
   | Evan Green    | Finance   |  1 | Charlie Davis |
   | Fiona Black   | Marketing |  3 | Fiona Black   |
   | Fiona Black   | Marketing |  2 | Dana White    |
   | Fiona Black   | Marketing |  1 | Charlie Davis |
   | George Harris | HR        |  3 | Fiona Black   |
   | George Harris | HR        |  2 | Dana White    |
   | George Harris | HR        |  1 | Charlie Davis |
   | Holly Evans   | IT        |  3 | Fiona Black   |
   | Holly Evans   | IT        |  2 | Dana White    |
   | Holly Evans   | IT        |  1 | Charlie Davis |
   | Ivy Collins   | Finance   |  3 | Fiona Black   |
   | Ivy Collins   | Finance   |  2 | Dana White    |
   | Ivy Collins   | Finance   |  1 | Charlie Davis |
   | Jack Lewis    | Marketing |  3 | Fiona Black   |
   | Jack Lewis    | Marketing |  2 | Dana White    |
   | Jack Lewis    | Marketing |  1 | Charlie Davis |
   +---------------+-----------+----+---------------+
   ```

2. **Inner Join**:
   - Returns only the rows where there is a match between the specified columns in both tables.
   ```sql
   SELECT * FROM employee INNER JOIN emp ON employee.id = emp.id;
   ```
   - Example:
   ```sql
   SELECT e1.id, e1.name, e1.employee_id, e2.name, e2.manager_id 
   FROM employees e1 
   INNER JOIN employees e2 
   ON e1.employee_id = e2.manager_id;
   ```
   - Result:
   ```
   +----+---------------+-------------+---------------+------------+
   | id | name          | employee_id | name          | manager_id |
   +----+---------------+-------------+---------------+------------+
   | 21 | George Harris |          20 | John Doe      |         20 |
   | 21 | George Harris |          20 | Jane Smith    |         20 |
   | 13 | John Doe      |          12 | Alice Johnson |         12 |
   | 21 | George Harris |          20 | Bob Brown     |         20 |
   | 24 | Jack Lewis    |          23 | Charlie Davis |         23 |
   | 13 | John Doe      |          12 | Dana White    |         12 |
   | 14 | Jane Smith    |          13 | Evan Green    |         13 |
   | 13 | John Doe      |          12 | Fiona Black   |         12 |
   | 24 | Jack Lewis    |          23 | George Harris |         23 |
   | 16 | Bob Brown     |          15 | Holly Evans   |         15 |
   | 24 | Jack Lewis    |          23 | Ivy Collins   |         23 |
   +----+---------------+-------------+---------------+------------+
   ```

3. **Self Join**:
   - When you perform a self join, each row from Table A is paired with every other row from the same Table A.
   - The result is a vast matrix—a complete fusion of all possibilities within the same universe!
   ```sql
   SELECT COLUMNS_FROM_A, COLUMNS_FROM_B 
   FROM TABLE_NAME T1 
   JOIN TABLE_NAME T2 
   ON CONDITION;
   ```
   - Example:
   ```sql
   SELECT e1.name, e1.email, e2.name, e2.dept_name 
   FROM employees e1 
   JOIN employees e2 
   ON e1.employee_id = e2.id;
   ```
   - Result:
   ```
   +---------------+---------------------------+---------------+-----------+
   | name          | email                     | name          | dept_name |
   +---------------+---------------------------+---------------+-----------+
   | Jane Smith    | jane.smith@example.com    | John Doe      | HR        |
   | Alice Johnson | alice.johnson@example.com | Jane Smith    | IT        |
   | Bob Brown     | bob.brown@example.com     | Alice Johnson | Finance   |
   | Charlie Davis | charlie.davis@example.com | Bob Brown     | Marketing |
   | Dana White    | dana.white@example.com    | Charlie Davis | HR        |
   | Evan Green    | evan.green@example.com    | Dana White    | IT        |
   | Fiona Black   | fiona.black@example.com   | Evan Green    | Finance   |
   | George Harris | george.harris@example.com | Fiona Black   | Marketing |
   | Holly Evans   | holly.evans@example.com   | George Harris | HR        |
   | Ivy Collins   | ivy.collins@example.com   | Holly Evans   | IT        |
   | Jack Lewis    | jack.lewis@example.com    | Ivy Collins   | Finance   |
   +---------------+---------------------------+---------------+-----------+
   ```

4. **Left Outer Join**:
   - Retrieves all records from the `employees` table and matched records from the `department` table. Unmatched records in the `department` table will have NULL values.
   ```sql
   SELECT e.name, e.employee_id, d.department_name, d.project_name 
   FROM employees e 
   LEFT JOIN department d 
   ON e.dept_id = d.id;
   ```
   - Result:
   ```
   +---------------+-------------+-----------------+--------------------+
   | name          | employee_id | department_name | project_name       |
   +---------------+-------------+-----------------+--------------------+
   | John Doe      |          12 | HR              | Cosmic Explorer    |
   | Jane Smith    |          13 | IT              | Stellar Innovators |
   | Alice Johnson |          14 | Finance         | Galactic Ventures  |
   | Bob Brown     |          15 | NULL            | NULL               |
   | Charlie Davis |          16 | HR              | Cosmic Explorer    |
   | Dana White    |          17 | IT              | Stellar Innovators |
   | Evan Green    |          18 | Finance         | Galactic Ventures  |
   | Fiona Black   |          19 | NULL            | NULL               |
   | George Harris |          20 | HR              | Cosmic Explorer    |
   | Holly Evans   |          21 | IT              | Stellar Innovators |
   | Ivy Collins   |          22 | Finance         | Galactic Ventures  |
   | Jack Lewis    |          23 | NULL            | NULL               |
   +---------------+-------------+-----------------+--------------------+
   ```

5. **Exclusive Left Outer Join**:
   - Retrieves all records from the `employees` table that do not have matching records in the `department` table.
   ```sql
   SELECT e.name, e.employee_id, d.department_name, d.project_name 
   FROM employees e 
   LEFT JOIN department d 
   ON e.dept_id = d.id 
   WHERE d.id IS NULL;
   ```
   - Result:
   ```
   +-------------+-------------+-----------------+--------------+
   | name        | employee_id | department_name | project_name |
   +-------------+-------------+-----------------+--------------+
   | Bob Brown   |          15 | NULL            | NULL         |
   | Fiona Black |          19 | NULL            | NULL         |
   | Jack Lewis  |          23 | NULL            | NULL         |
   +-------------+-------------+-----------------+--------------+
   ```

6. **Right Outer Join**:
   - Retrieves all records from the `department` table and matched records from the `employees` table. Unmatched records in the `employees` table will have NULL values.
   ```sql
   SELECT e.name, e.employee_id, d.department_name, d.project_name 
   FROM employees e 
   RIGHT JOIN department d 
   ON e.dept_id = d.id;
   ```
   - Result:
   ```
   +---------------+-------------+-----------------+--------------------+
   | name          | employee_id | department_name | project_name       |
   +---------------+-------------+-----------------+--------------------+
   | John Doe      |          12 | HR              | Cosmic Explorer    |
   | Charlie Davis |          16 | HR              | Cosmic Explorer    |
   | George Harris |          20 | HR              | Cosmic Explorer    |
   | NULL          |        NULL | Marketing       | Interstellar Brands|
   | Jane Smith    |          13 | IT              | Stellar Innovators |
   | Dana White    |          17 | IT              | Stellar Innovators |
   | Holly Evans   |          21 | IT              | Stellar Innovators |
   | NULL          |        NULL | R&D             | Quantum Discoveries|
   | Alice Johnson |          14 | Finance         | Galactic Ventures  |
   | Evan Green    |          18 | Finance         | Galactic Ventures  |
   | Ivy Collins   |          22 | Finance         | Galactic Ventures  |
   +---------------+-------------+-----------------+--------------------+
   ```

7. **Exclusive Right Outer Join**:
   - Retrieves all records from the `department` table that do not have matching records in the `employees` table.
   ```sql
   SELECT e.name, e.employee_id, d.department_name, d.project_name 
   FROM employees e 
   RIGHT JOIN department d 
   ON e.dept_id = d.id 
   WHERE e.id IS NULL;
   ```
   - Result:
   ```
   +------+-------------+-----------------+--------------------+
   | name | employee_id | department_name | project_name       |
   +------+-------------+-----------------+--------------------+
   | NULL |        NULL | Marketing       | Interstellar Brands|
   | NULL |        NULL | R&D             | Quantum Discoveries|
   +------+-------------+-----------------+--------------------+
   ```

8. **Full Outer Join**:
   - Retrieves all records when there is a match in either left (table1) or right (table2) table records.
   ```sql
   SELECT e.name, e.employee_id, d.department_name, d.project_name 
   FROM employees e 
   FULL JOIN department d 
   ON e.dept_id = d.id;
   ```
   - Result:
   ```
   +---------------+-------------+-----------------+--------------------+
   | name          | employee_id | department_name | project_name       |
   +---------------+-------------+-----------------+--------------------+
   | John Doe      |          12 | HR              | Cosmic Explorer    |
   | Jane Smith    |          13 | IT              | Stellar Innovators |
   | Alice Johnson |          14 | Finance         | Galactic Ventures  |
   | Bob Brown     |          15 | NULL            | NULL               |
   | Charlie Davis |          16 | HR              | Cosmic Explorer    |
   | Dana White    |          17 | IT              | Stellar Innovators |
   | Evan Green    |          18 | Finance         | Galactic Ventures  |
   | Fiona Black   |          19 | NULL            | NULL               |
   | George Harris |          20 | HR              | Cosmic Explorer    |
   | Holly Evans   |          21 | IT              | Stellar Innovators |
   | Ivy Collins   |          22 | Finance         | Galactic Ventures  |
   | Jack Lewis    |          23 | NULL            | NULL               |
   | NULL          |        NULL | Marketing       | Interstellar Brands|
   | NULL          |        NULL | R&D             | Quantum Discoveries|
   +---------------+-------------+-----------------+--------------------+
   ```
---
