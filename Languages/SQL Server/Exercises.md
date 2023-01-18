## 070.010 - SQL EXERCISES ##

Prerequisites: [SQL I](070.010 - SQL II), Adventure Works (sample database)

## QUERY ##

* simple query

```Sql
Select Title, FirstName, LastName
From Person.Person

Select Title, FirstName, LastName
From Person.Person
  Order By FirstName

Select Title, FirstName, LastName
From Person.Person
  Order By FirstName, LastName

Select Title, FirstName, LastName
From Person.Person
  Order By FirstName Desc, LastName
```

```Sql
Select *
From Production.Product

Select Top 10 SafetyStockLevel
From Production.Product

Select Distinct SafetyStockLevel
From Production.Product

Select Distinct Top 3 SafetyStockLevel
From Production.Product
```

* where clause
  * `=`	Equal
  * `>`	Greater than
  * `<`	Less than
  * `>=` Greater than or equal
  * `<=` Less than or equal
  * `<>` Not equal to
  * `LIKE` Wildcard match

```Sql
Select ProductID, Name, ProductNumber
From Production.Product
  Where ProductNumber = 'MA-7075'

Select ProductID, Name, ProductNumber
From Production.Product
  Where SafetyStockLevel < 5

Select ProductID, Name, ProductNumber
From Production.Product
  Where Name Like 'Paint%'
```

* [not] in, between, exists
  * `in` Value in set
  * `between` Value between range
  * `exists` Query returns at least one record
  * `not` Negated or opposite condition

```Sql
Select ProductID, Name, ProductNumber
From Production.Product
  Where ProductNumber In ('MA-7075', 'BL-2036', 'ABC')

Select ProductID, Name, ProductNumber, StandardCost
From Production.Product
  Where StandardCost Between 14 And 20

Select ProductID, Name, ProductNumber
From Production.Product
  Where Exists(Select * From Sales.SalesOrderDetail Where ProductID = Product.ProductID And OrderQty > 30)
```

* aggregates
  * `MIN` returns the smallest value in a given column
  * `MAX` returns the largest value in a given column
  * `SUM` returns the sum of the numeric values in a given column
  * `AVG` returns the average value of a given column
  * `COUNT` returns the total number of values in a given column
  * `COUNT(*)` returns the number of rows in a table

```Sql
Select MIN(ReorderPoint), MAX(ReorderPoint)
From Production.Product

Select COUNT(Color), COUNT(*)
From Production.Product

Select MAX(StandardCost), AVG(StandardCost)
From Production.Product
  Where SafetyStockLevel < 5
```

```Sql
Select SafetyStockLevel, MAX(StandardCost), AVG(StandardCost)
From Production.Product
  Group By SafetyStockLevel

Select SafetyStockLevel, MAX(StandardCost), AVG(StandardCost)
From Production.Product
  Where SafetyStockLevel <= 500
  Group By SafetyStockLevel

Select SafetyStockLevel, MAX(StandardCost), AVG(StandardCost)
From Production.Product
  Where SafetyStockLevel <= 500
  Group By SafetyStockLevel
  Having MAX(StandardCost) > 0
```

* window functions & select queries
  * Ranking functions
    * `ROW_NUMBER`
    * `RANK`
    * `DENSE_RANK`
    * `NTILE`
  * Aggregate functions
  * Offset functions
    * `LAG`
    * `LEAD`
    * `FIRST_VALUE`
    * `LAST_VALUE`
  * Distribution functions
    * `PERCENT_RANK`
    * `CUME_DIST`
    * `PERCENTILE_DISC`
    * `PERCENTILE_CONT`

    A window function is a function that's applied to a set of rows defined by a window descriptor and returns a single value for each row from the underlying query.

```Sql
Select ProductID, Name, ProductNumber, Size,
ROW_NUMBER() Over (Partition By Size Order By Name)
From Production.Product
  Where SafetyStockLevel < 5
  ```

## JOIN ##

```Sql
Select *
From Sales.SalesPerson
	Join Sales.SalesOrderHeader
	On SalesPerson.BusinessEntityID = SalesOrderHeader.SalesPersonID

Select *
From Sales.SalesPerson
	Join Sales.SalesOrderHeader
	On SalesPerson.BusinessEntityID = SalesOrderHeader.SalesPersonID
	Where SalesPerson.TerritoryID = 4

Select *
From Sales.SalesPerson
	Join Sales.SalesOrderHeader
		Join Sales.SalesOrderDetail
		On SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID
	On SalesPerson.BusinessEntityID = SalesOrderHeader.SalesPersonID
	Where SalesPerson.TerritoryID = 4
```

```Sql
Select *
From Sales.SalesPerson
	Left Join Sales.SalesOrderHeader
	On SalesPerson.BusinessEntityID = SalesOrderHeader.SalesPersonID
	And OrderDate = '2011-05-31' And SalesOrderHeader.TerritoryID = 2

Select *
From Sales.SalesPerson
	Left Join Sales.SalesOrderHeader
	On SalesPerson.BusinessEntityID = SalesOrderHeader.SalesPersonID
	And OrderDate = '2011-05-31' And SalesOrderHeader.TerritoryID = 2
  Where SalesOrderHeader.SalesOrderID Is Null
```