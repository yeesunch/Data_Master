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


Examples
```
1. Create a new database
CREATE DATABASE <dbname>

2. Delete a database
DROP DATABASE <dbname>

3. Backup a SQL Server

```


引言
 进行SQL和T-SQL编程时常常会忽略编码标准，但这些标准却是开发小组顺利开展工作的关键工具，SQL和T-SQL代码的格式似乎并不重要，但一致的格式可以使您的同事（不论是同一小组的成员还是更大范围的SQL和T-SQL开发团队的成员）更轻松地浏览和理解您的代码。T-SQL语句有一个结构，遵循一目了然的结构使您可以更轻松地查找和确认语句的不同部分,可以加快开发效率。

1 书写标准
1.1  缩进 
1) 一般缩进为4个空格。
2) 不要用Tab制表符来作缩进。

1.2  换行
1) Select/From/Where/Order by/Groupby等子句必须另起一行写。
2) Select子句内容如果只有一项，与Select同行写。
3) Select子句内容如果多于一项，每一项单独占一行，在对应Select的基础上向右缩进4空格。
4) From子句内容如果只有一项，与From同行写。
5) From子句内容如果多于一项，每一项单独占一行，在对应From的基础上向右缩进4个空格。
6) Where子句的条件如果有多项，每一个条件占一行，以AND或者OR开头，在对应Where的基础  上向右缩进4个空格。
7) (Update)Set子句内容每一项单独占一行，无缩进。
8) Insert子句内容每个表字段单独占一行，无缩进；values每一项单独占一行，无缩进。
9) SQL文中间不允许出现空行。
10) 存储过程或函数输入参数命名以in开头，如@in_Year；输出参数以out开头，如@out_money；局部变量首字母小写，第二个单词起的每个单词的首字母大写，不使用“_”，如@customerCount；

1.3 空格
1) 连接符or、in、and、以及＝、<=、>=等前后加上一个空格。
2) 逗号之后必须接一个空格。
3) 关键字、保留字和左括号之间必须有一个空格。


2. 命名规则
常见命名规则有四种样式：完全大写、完全小写、Pascal 大小写和 Camel 大小写。
1) Camel 大小写
标识符的首字母小写，每个后面连接的单词的首字母大写，其余字母小写的书写约定。对于缩写的双字母单词，要求它们出现在标识符首部时全部小写，否则全部大写。
例如：applicationException id

2) Pascal 大小写
组成标识符的每个单词的首字母大写，其余字母小写的书写约定。对于缩写的双字母单词，要求全部大写。
例如：ApplicationExceptionID

3) 匈牙利命名法
匈牙利命名法由匈牙利程序员发明，他在微软工作了多年，此命名法就是通过微软的各种产品和文档传出来。多数有经验的程序员，不管他们用的是哪门语言，都或多或少在使用它。
基本原则：变量名 = 属性 ＋ 类型 ＋ 对象描述
即一个变量名是由三部分信息组成，这样，程序员很容易理解变量的类型、用途，而且便于记忆。


3 注释
1) 对较为复杂的SQL语句加上注释，说明算法、功能。注释风格：注释单独成行、放在语句前面。
2) 应对不易理解的分支条件表达式加注释。
3) 对重要的计算应说明其功能。
4) 过长的函数实现，应将其语句按实现的功能分段加以概括性说明。
5) 常量及变量注释时，应注释被保存值的含义(必须)，合法取值的范围(可选)。
6) 可采用单行/多行注释。（-- 或 ）。

3.1 代码头部注释
1 代码头部注释
在SQL代码块（sql文件或存储过程）的头部进行注释，标注创建人(Author)、创始日期(Create date)、修改信息(Modify [n])。
格式：
-- =============================================
-- Author:     
-- Create date:
-- Description:
-- Modify [n]: < Modifier,Date, Description >
-- =============================================

示例：
-- ================================================
-- Author:     Zhanghaifeng
-- Create date: 2006-12-25
-- Description: H2000报关单回执处理
-- Modify [1]:  郑佐, 2006-12-31, 简化逻辑判断流程
-- Modify [2]:  郑佐, 2007-01-20, 更新条件判断
-- ================================================
注：日期格式使用 yyyy-MM-dd。Modify [n] n代表修改序号，从1开始，每次修改加1。


2. TRANSACTION注释
建议在每个事务的开头进行注释，说明该事务的功能。
-- < Modifier,Date, Description >
BEGIN TRANSACTION;
分享：
3

喜欢

0

赠金笔赠金笔

