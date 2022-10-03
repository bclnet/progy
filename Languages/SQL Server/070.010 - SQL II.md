## SQL II - INTERNALS ##
- prereq: [SQL I](070.010 - SQL I)


## PROCESSING ##
* In-Process vs Client/Server
* In-Process
  - Microsoft Access
  - Each person on their own
  - Use external file for Control/Locks
  - Easy to corrupt
* Client/Server
  - Single Process becomes a broker
  - Clients speak with broker
  - Easy to control and serialize
  - Inherently parallel

## STORAGE ##
* File Group
* Record
* Partition
* Table Tree


## RECORDS ##
* Record as main object
  - Only categorize by one attribute (even if its two or more, its still virtualy one)
  - Use reference
  - Cluster, unclustored using cars example
* Scan vs Seek
* Index
  - Clustered vs Nonclustered Index
  - Covering Index
  - Best match
* Statistics - not always best answer
  - Update Statistics
* Sargeable
* Constraints - Inforces Data Integrety, The following constraints are commonly used in SQL:
  - CHECK - ensure some custom validation
  - NOT NULL - Ensures that a column cannot have a NULL value
  - UNIQUE - Ensures that all values in a column are different
  - PRIMARY KEY - A combination of a NOT NULL and UNIQUE
    * A primary key (PK) is a single column or combination of columns (called a compound key) that uniquely identifies each row in a table. A primary key constraint contains unique, non-null values. When you apply the primary key constraint, the NOT NULL and unique constraints are added implicitly.
  - FOREIGN KEY - Uniquely identifies a row/record in another table
    * In a foreign key reference, a link is created between two tables when the column or columns that hold the primary key value for one table are referenced by the column or columns in another table.
    * Unlike primary key constraints, when a foreign key constraint is defined for a table, an index is not created by default by SQL Server. However, it's not uncommon for developers and database administrators to add them manually.
* Primary Key
  - Identity(1,1)
  - Default NEWGUID()
  - Compound Keys
  - Natural Keys, Surragate Keys
* Foreign Key
  - Cascade Modes






## MICROSOFT TESTS ##
* https://www.microsoft.com/en-us/learning/mcsa-sql2016-database-development-certification.aspx

* Exam 70-761 - Querying Data with Transact-SQL
* Exam 70-762 - Developing SQL Databases