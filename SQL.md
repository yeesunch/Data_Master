# SQL
# Table of Contents
1. [SQL Basic](#ch1)
2. [SQL Grammer](#ch2)
3. [Chapter 2 - Data Collection](#ch2)
4. [Chapter 3 - Data Preparation](#ch3)
5. [Chapter 4 - Data Cleansing: 4C Correcting, Completing, Creating, Converting](#ch4)
5. [Chapter 5 - Exploratory Data Analysis(EDA)](#ch5)
6. [Chapter 6 - Data Modeling](#ch6)
7. [Chapter 7 - Model Validation and Implementation](#ch7)
8. [Chapter 8 - Model Optimization and Strategization](#ch8)


<a id="ch1"></a>
## 1. SQL Basic
### Definition
**SQL** stands for **Structured Query Language**, which is used to access and manipulate databases. <br>
According to ANSI (American National Standards Institute), it is the standard language for **RDBMS** (rational database management systems). <br>
<br><br>

### Usage
* Execute queries against a database
* Create databases/tables
* Insert/update/delete records from a database
* retrieve data and create views in a database
* Create stored procedures in a database
* Set permissions on tables, procedures and views
<br><br>

### RDBMS
RDBMS (Ralational Database Management System) is the basis for SQL (and other databases systems such as MS SQL Server, MySQL, Oracle, Microsoft Access, IBM DB2) 
Databases -> Tables -> Columns & Rows
<br><br>

### Types of Statements
1. DQL(Data Query Language)
    * select
    * from
    * where
    * order by
    * group by
    * having
2. DDL(Data Definition Language) - CRUD (Create/Retrieve/Update/Delete)
    * create
    * drop
    * alter
    * rename
3. DML(Data Manipulation Language)
    * insert
    * update
    * delete
4. DCL(Data Control Language)
    * grant
    * revoke
5. TCL (Transaction Control Language)
    * commit
    * rollback
    * savepoint
<br><br>

### Data Types
1. Text

| Name        | Max Length         | Type                                |
| ----------- | ------------------ | ----------------------------------- |
| TEXT        | 2<sup>16</sup> - 1 | Strings                             |
| CHAR        | Fixed Length       | Strings, Number, Special Characters |
| VARCHAR     | Variable Length    | Strings, Number, Special Characters |
| TINYTEXT    | 2<sup>8</sup> - 1  | Strings                             |
| MEDIUMTEXT  | 2<sup>24</sup> - 1 | Strings                             |
| LONGTEXT    | 2<sup>32</sup> - 1 | Strings                             |
| BLOB        |                    | BLOBs (Binary Large Objects)        |
| MEDIUMBLOB  |                    | BLOBs (Binary Large Objects)        |
| LONGBLOB    |                    | BLOBs (Binary Large Objects)        | 
| ENUM        |                    | Allow to enter                      |
| SET         | 64                 | Allow to enter multiple             |


2. Number

| Name        | Size     | Range                                                             | Type                                    |
| ----------- | -------- | ----------------------------------------------------------------- | --------------------------------------- |
| INT         | 11       | [-2<sup>31</sup>, 2<sup>31</sup> - 1], or [0, 2<sup>32</sup> - 1] | Integer                                 |
| FLOAT       |          |                                                                   | Small number with .                     |
| DOUBLE      |          |                                                                   | Large number with .                     |
| DECIMAL     |          |                                                                   | DOUBLE as string, fixed digits after .  |
| TINYINT     |          | [-2<sup>7</sup>, 2<sup>7</sup> - 1], or [0, 2<sup>8</sup> - 1]    |                                         |
| SMALLINT    | 6        | [-2<sup>15</sup>, 2<sup>15</sup> - 1], or [0, 2<sup>16</sup> - 1] |                                         |
| MEDIUMINT   | 9        | [-2<sup>23</sup>, 2<sup>23</sup> - 1], or [0, 2<sup>24</sup> - 1] |                                         |
| BIGINT      | 20       | [-2<sup>63</sup>, 2<sup>63</sup> - 1], or [0, 2<sup>64</sup> - 1] |                                         |


3. Date

| Name        | Fortmat                          | Range                                           |
| ----------- | -------------------------------- | ----------------------------------------------- |
| DATE()      | YYYY-MM-DD                       | '1000-01-01' to '9999-12-31'                    |
| DATETIME()  | YYYY-MM-DD HH:MM:SS              | '1000-01-01 00:00:00' to '9999-12-31 23:59:59'  |
| TIMESTAMP   | Unix ('1970-01-01 00:00:00' UTC) | '1970-01-01 00:00:00' -                         |
| TIME()      | HH:MM:SS                         | '-838:59:59' to '838:59:59'                     |
| YEAR()      | YY or YYYY                       | 70 to 69 (from 1970 - 2069) or 1901 to 2155     |



<a id="ch2"></a>
## 2. SQL Grammer
### Syntax
1. Indentation
    * 4 spaces, do not use TAB

2. Linefeed
    * Clauses requires a new ling (SELECT/FROM/WHERE/ORDER BY/GROUP BY)
    * SELECT/FROM (Clauses within SELECT/FROM)
        * 1 Clause - stay in the same line
        * Multiple Clauses - each requires a new line, with 4 more spaces (from SELECT/FROM)
    * WHERE (Conditions within WHERE)
        * Each condition requires a new line, start with AND or OR, with 4 more spaces (from WHERE)
    * (UPDATE) SET - each clause requires a new line, with no indent
    * INSERT - each column name requires a new line, with no indent; each value requires a new line, with no indent
    * Parameters in store process or function
        * Input start with in and output start with out, e.g. @in_Year, @out_Money
        * Local variable first letter lowercase, first letter from second word uppercase, no '_' allowed, e.g. @customerCount
    * No empty line allowed
    
3. Space
    * Operators - 1 space preceding and 1 space folloing ( OR / IN / AND , = / <= / >= , etc.)
    * Comma - 1 space after , 
    * Left bracket - 1 space between keyword and (

4. Name Rules
    * Basic Rules
        * variable_name = attribute + type + description
        * Keyword  - all uppercase, e.g. SELECT
        * Table name -  first letter uppercase, e.g. Tablename
        * Column name - all lowercase, e.g. colname
    * 4 common methods
        * ALL UPPERCASE
        * all lowercase
        * Camel - applicationException, id
        * Pascal - ApplicationException, ID

5. Comment
    * Where to add comments
        * Complex statements, comment before statement
        * Conditions hard to understand
        * Important calculation
        * Long function, comment by paragraph
        * Variable, comment on its value and range
    * How to add comments - 3 ways
        * '## comment1'
        * '-- comment2'
        * '/* comment3 */'
    * Header - Author + Create date + Modification
    * Transaction - state the function of the section
```
Header:
-- =============================================
-- Author:     
-- Create date:
-- Description:
-- Modify [n]: < Modifier,Date, Description >
-- =============================================

Example:
-- ======================================================================
-- Author:     Yeesun
-- Create date: 2021-04-16
-- Description: My summary of SQL
-- Modify [1]:  Original Author1, 2006-12-31, Summarize their paragraphs
-- Modify [2]:  Original Author2, 2007-01-20, Add more sections
-- =======================================================================
```
_Note: Date format should be yyyy-MM-dd. Modify [n] n represents order of modifications_

```
Transaction:
-- < Modifier, Date, Description >
```


6. Execution order

(8) SELECT (9) DISTINCT <select_list> <br>
(1) FROM <left_table> <br>
(3) <join_type> JOIN <right_table> <br>
(2) ON <join_condition> <br>
(4) WHERE <where_condition> <br>
(5) GROUP BY <group_by_list> <br>
(6) WITH {CUBE|ROLLUP} <br>
(7) HAVING <having_condition> <br>
(10) ORDER BY <order_by_list> <br>
(11) LIMIT <limit_number> <br>



<a id="ch3"></a>
## 3. SQL Examples
### SQL Database
1. Create a new database
```
CREATE DATABASE dbname;
```

2. Drop a database
```
DROP DATABASE dbname;
```

3. Backup a database
```
BACKUP DATABASE testDB
TO DISK = 'D:\backups\testDB.bak';
```

Back up with differential part
```
BACKUP DATABASE testDB
TO DISK = 'D:\backups\testDB.bak'
WITH DIFFERENTIAL;
```

4. Create a new table
Create new
```
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
Example:
```
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
```

Create from existing
```
CREATE TABLE new_table AS
    SELECT column1, column2,...
    FROM existing_table
    WHERE ....;
```
Example:
```
CREATE TABLE TestTable AS
SELECT customername, contactname
FROM customers;
```

5. Drop a table
Delete table
```
DROP TABLE table_name;
```

Clear but not delete table
```
TRUNCATE TABLE table_name;
```

6. Alter a table
Use to add, delete, modity columns or add/drop constraints on an existing table.
Add column
```
ALTER TABLE Customers
ADD Email varchar(255);
```
Drop column
```
ALTER TABLE Customers
DROP COLUMN Email;
```