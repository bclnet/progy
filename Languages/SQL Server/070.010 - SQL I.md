## SQL I - BASIC ## 

Prerequisites: [DATA](000.010%20-%20DATA.md), [DATA SHAPE](000.011%20-%20DATA%20SHAPE.md), [LANGUAGE](010.000%20-%20LANGUAGE.md).

Glossary:
  - Technical debt - the implied cost of additional rework caused by choosing an easy solution now instead of using a better approach that would take longer.
  - RDBMS - Relational Database Management System
  - CRUD - Create Read Update Delete
  - ACID - Atomicity, Consistency, Isolation, Durability
  - DDL - Data Definition Language : CREATE, ALTER
  - DML - Data Manipulation Language : INSERT, UPDATE, DELETE
  - DCL* - Data Control Language : GRANT, REVOKE

## LIGHT DATA STRUCTURES ##

**BTREE** - a B-tree is a self-balancing tree data structure that keeps data sorted and allows searches, sequential access, insertions, and deletions in logarithmic time.


## CONTEXT ##

From scratch using data structures, adds technical debt.

What about
- Recoverability - Backup and Restore
- Efficiency - Faster data access
- Volatility and Scale - Rollbacks, Federation
- Concurrency - multiple threads concurently accessing same data
- Durability - Power outages in middle of operation
- Plasticity - Change the schema

Wrapped into a middle ware, that can be reused and bring these forward. Deployed as an in-process or server component.

## INTERFACE ##

Need a way to inteface with SQL, In-Proc or Server:

* **MDAC** - Microsoft Data Access Components is a framework of interrelated Microsoft technologies that allows programmers a uniform and comprehensive way of developing applications that can access almost any data store.

* **SQL Native Client** - can be used rather than Microsoft Data Access Components (MDAC) to create new applications or enhance existing applications that need to take advantage of new SQL Server 2005 features such as Multiple Active Result Sets (MARS), Query Notifications, User-Defined Types (UDT), and XML data type support.

  * **TDS** - Specifies the Tabular Data Stream Protocol, which is an application layer request/response protocol that facilitates interaction with a database server and provides for authentication and channel encryption negotiation; specification of requests in SQL (including Bulk Insert); invocation of a stored procedure, also known as a Remote Procedure Call (RPC); returning of data; and Transaction Manager Requests.
    - Single command
    - Recordset
    - Print

* **ODBC** - Open Database Connectivity is a standard application programming interface for accessing database management systems. The designers of ODBC aimed to make it independent of database systems and operating systems.

## SCHEMA/PERMISSIONS ##

**Schema**

* **dbo**, database owner
* ***anything else***, custom schemas
* act like folders
* only when schema referenced objects are used can an execution plan be stored

**Permissions**
* Server role permissions
* object permissions
* role level permisions are done using view or functions


## STRUCTURE ##

* **Record**
  - holds the data

* **Page**
  - holds record(s) per page
  - record can span multiple pages, used to be limted to 8k ***new***

* **Table**
  - holds page(s) for data
  - holds page(s) for index(s)
  - can be virtual

* **View**
  - virtual table based on query

* **Database**
  - is the primary document file, think .xls
  - holds table(s)
  - holds all other database object(s)
  - virtual security domain
  - clones *model database* to create
  - uses *database* to hold settings
  

* **Server**
  - is the document application, think Excel
  - holds database(s)
  - real security domain
  - uses *master database* to hold settings
  
  


## DDL ##

Data Definition Language (DDL) is a standard for commands that define the different structures in a database. DDL statements create, modify, and remove database objects such as tables, indexes, and users. Common DDL statements are CREATE, ALTER, and DROP.

**CREATE**, **ALTER**, used to add or modify existing objects

```
CREATE TABLE dbo.Board(
  BoardId int NOT NULL,
  Title nvarchar(300) NULL,
  CONSTRAINT [PK_Board] PRIMARY KEY CLUSTERED (BoardId ASC),
)
```

**DROP**, used to drop existing objects
```
DROP TABLE dbo.Board
```

## DML ##

DML is abbreviation of Data Manipulation Language. It is used to retrieve, store, modify, delete, insert and update data in database. Examples: SELECT, UPDATE, INSERT statements. DDL is abbreviation of Data Definition Language. It is used to create and modify the structure of database objects in database.

SQL is a set language, more like the army then a recipe
- everyone with a red shirt step forward. everyone in company A flank right.
- sets often join, and there are multiple [**JOIN**](https://en.wikipedia.org/wiki/Join_(SQL)) types: 
  - inner
  - left outer join
  - right outer join
  - full outer join
  - cross join - produces a result set which is the number of rows in the first table multiplied by the number of rows in the second table if no WHERE clause is used along with CROSS JOIN
  - cross apply - returns only those rows from left table expression (in its final output) if it matches with right table expression
  - outer apply - returns all the rows from left table expression irrespective of its match with the right table expression

[***Example***]( https://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins)
  ![sql joins](/assets/sql-joins.jpg)

[**SELECT**](https://docs.microsoft.com/en-us/sql/t-sql/queries/select-transact-sql)
```
SELECT {TOP N} {field(s)}
FROM {schema}.{table}
  JOIN {schema}.{table} ON {condition}
  WHERE {condition}
  GROUP BY {field(s)}
  HAVING {condition}
```

Select statements are used to stream record(s), or set variables. Select statements have two halves:

The select or projection side:
- insert into
- Streams records
- Acts like a whole seperate part of query
- Can have sub querys
- Can select into variables
- Top

The From side:
- From
- Join joins tables together
- Group A grouping clause
- Having Second Where


[**INSERT**](https://docs.microsoft.com/en-us/sql/t-sql/statements/insert-transact-sql)
```
INSERT {schema}.{table} ({field})
OUTPUT inserted.{field}
VALUES ({value})
```

Insert statements are used to insert record(s) into a table. Literal values, or a select statement can be used to define data. Optionally effected record(s) can be streamed with the OUTPUT keyword.


[**UPDATE**](https://docs.microsoft.com/en-us/sql/t-sql/queries/update-transact-sql)
```
UPDATE {schema}.{table} SET {field} = {value}
OUTPUT inserted.{field}, deleted.{field}
  WHERE {condition}
```

Update statements are used to update record(s) in a table. Optionally effected  record(s) can be streamed with the OUTPUT keyword.


[**DELETE**](https://docs.microsoft.com/en-us/sql/t-sql/statements/delete-transact-sql)
```
DELETE {TOP N} {schema}.{table}
OUTPUT deleted.{field}
  WHERE {condition}
```

Delete statements are used to delete record(s) from a table.  Optionally effected record(s) can be streamed with the OUTPUT keyword.


***Recommend*** - Having a convention for table alias, indenting, nameing is recomended.

## DCL ##

A data control language (DCL) is a syntax similar to a computer programming language used to control access to data stored in a database (Authorization). In particular, it is a component of Structured Query Language (SQL). Examples of DCL commands include: GRANT to allow specified users to perform specified tasks.



backps
* full from data
* diff from data
* transactional - from log file
* can recover to any point in time
* log shipping - new

Filegroups
* mdf/ldf on different drives, can target objects to a file group
* default is PRIMARY


MDF/LDF
all state is from sql changes
slower to change file system so changes are made in memory
old model - simple mode
* flushed at a checkpoint
* pull the plug evertthing is lost,
* so first every sql is writen to a log file
* log file grows as needed, and restarts on checkpoint 
new model - full mode
* checkpoint doesnt flush log but keeps growing
* only backup will flush log
* can recover to any point in time
shrink log file
* move back to old model
* checkpoint
* shrink log file

##INDEXES##
Data can only be stored in one physical place
  So if I have parking lot full of cars, I can sort by color or make but can't sort both at the same time
    Only has one unclustered location
    So to have cake and eat it too, have pointer on the object. This creates a sort of mapping.

##TRIGGERS##
Functions or sotre procedures that run on an event that happens to the table
  "Everytime new record is added, run query"
  3 Types
    After - run function after new record
      predominant
    Before - run function before new record
    Instead of - instead of adding new record, run query
  Because of triggers, the last record @@IDENTITY is not necessarily the last one you added. That record is identified as SCOPE_IDENTITY()

  With triggers, I can make

## TRANSACTIONS ##
```
Begin Transaction;
..DO SQL..
Rollback Transaction;
```
makes atomic
- good for verifying or other things

video game save/reload analogy
inline vs wal
nested transactions
try catch


## EXECUTION PLAN ##

Refers to queries
  Like a firing solution on a submarine
  This is going to be how I find all this data for you
  Can cache plan if schema hasn't changed, making it faster
    2 schemas
      If you don't specify schema on object, then can't cache plan
      Is direct string match (can't change data within), unless you parameterize
Hacking - SQL injection
  If you don't use parameterized queries, then it's much easier to inject other queries (Statements) into yours

SQL will figure out the best way to get your data
  Scanning through tables
    1 by 1 record
  or Seek
    Trees to search
  If you have small table, faster to use 1 by 1 
  Table can use statistics (how many records are in tables)
    Meta data about the table, figures out best way to search data



## STORED PROCEDURES ##
small client request expands on server to larger request
does a direct string match
parameters


## FUNCTIONS ##

Adding 1 + 1 or A + B
  Instead of doing that, call the function that does it
  This is called scalar value
  A function is a reusable formula

Functions come in 2 flavors
  Deterministic and non deterministic
    D: Will return same value with same inputs
      Results are always the same given the same inputs
      Have to use schema binding for something to be deterministic
    N: Uses changing values (no side effects)
    When you're creating a table, you can create calculated fields*
      *Those fields will be calculated at runtime
      Use the word "Persistent" to "cache" or keep the result initially generated from calculation
        Persist HAS to be determinisitic, because will change too much
      Can also replace the calculation with a function.

```
ALTER FUNCTION [dbo].[fn_GetDateIDByDate](@date datetime) Returns int With SCHEMABINDING as Begin
	Return (CASE when @date Is Null Then Null Else CAST(CONVERT(nvarchar, @date, 112) as int) End);
End;
```

## COLLATION ##

Has to do with languages.
  There are special instances where this breaks down (letters with accents and whether or not they're matched with those that don't have them, for example)

This mapping can be set by default by DB, table, and field, and can be overwritten by query

Collation refers to a set of rules that determine how data is sorted and compared. Character data is sorted using rules that define the correct character sequence, with options for specifying case-sensitivity, accent marks, kana character types and character width.

[Reference](https://www.databasejournal.com/features/mssql/article.php/3302341/SQL-Server-and-Collation.htm)

```
Create table Mytable (
[colu] char(10) COLLATE Albanian_CI_AI_KS_WS NULL,
[Maydate] [char] (8) COLLATE Korean_Wansung_Unicode_CS_AS_KS NOT NULL,
[Risk_Rating] [char] (2) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL 
)
```



## CTE, RECURSION ##

## TRANSACT-SQL ##

SQL has its own programming language
  This is called TSQL
  P-SQL is Oracle's version

## LINKED SERVERS/OPENROWSET ##

SQL uses a 4 part naming convention (I know, there's 5, but usually don't put the server on there)
  Server.database.table.schema.object

There are also open queries
  Select * from table
  Querying any remote servers

Advanced techniques for scaling out

Federated/Federations
  Can federate using partition
    A-K on this database, L-Z on this other one
      These two are linked, and one is the primary

## .NET ##

Now you can use .NET integrated with SQL (can use .NET assembly within SQL)

##LICENSING##
  Licensing is expensive
    Used to be by seat
    Then there's Internet license to avoid people putting a web front end and going through license
      Then people put virtual machines behind license
        So now it's per [virtual] core