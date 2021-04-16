# SQL
# Table of Contents
1. [Introduction: SQL Basic](#ch1)
2. [Chapter 2 - Define the Problem](#ch1)
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
2. DDL(Data Definition Language)
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

### Syntax
1. Comment
    * '## comment1'
    * '-- comment2'
    * '/* comment3 */'
2. End with ';'
3. Not case sensitive
4. 
5. Execution order

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



