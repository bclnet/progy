


## Language : C, C++

Data type | Range | Storage
--- | --- | ---
`char/unsigned char` | 0 to 255 / -126 to +127 | 1 byte
`short/usigned short` | -32,768 to 32,767 / 0 to 65,535 | 2 bytes
`int/unsigned int` | -2,147,483,648 to 2,147,483,647 / 0 to 4,294,967,295 | 4 bytes
`long/unsigned long` | -2,147,483,648 to 2,147,483,647 / 0 to 4,294,967,295 | 4 bytes
`long long/unsigned long long` | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 / 0 to 18,446,744,073,709,551,615 | 8 bytes
`size_t` | | 4/8 bytes
`ptrtype_t` | | bus* byte


## Language : C#

Data type | Range | Storage
--- | --- | ---
`bool` | true/false | 1 byte
`byte/sbyte` | 0 to 255 / -128 to 127 | 1 byte
`char` | U+0000 to U+FFFF | 2 bytes
`decimal` | (-7.9 x 10+28 to 7.9 x 10+28) / (10+0 to 10+28) | 16 bytes
`double` | ±5.0 × 10−324 to ±1.7 × 10+308 | 8 bytes
`enum` | * | *
`float` | -3.4 × 10+38 to +3.4 × 10+38 | 4 bytes
`int/uint` | -2,147,483,648 to 2,147,483,647 / 0 to 4,294,967,295 | 4 bytes
`long` | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 / 0 to 18,446,744,073,709,551,615 | 8 bytes
`short` | -32,768 to 32,767 / 0 to 65,535 | 4 bytes
`struct` | * | *


## Language : SQL Server

[*Exact Numerics*](https://technet.microsoft.com/en-us/library/ms187752(v=sql.105).aspx)

Data type | Range | Storage
--- | --- | ---
`bigint` | -2^63 (-9,223,372,036,854,775,808) to 2^63-1 (9,223,372,036,854,775,807) | 8 bytes
`bit` | 0 to 1 | *
`decimal(18, 0)`, `numeric(18, 0)` | * | *
`int` | -2^31 (-2,147,483,648) to 2^31-1 (2,147,483,647) | 4 bytes
`money` | -922,337,203,685,477.5808 to 922,337,203,685,477.5807 | 8 bytes
`smallint` | -2^15 (-32,768) to 2^15-1 (32,767) | 2 bytes
`smallmoney` | - 214,748.3648 to 214,748.3647 | 4 bytes
`tinyint` | 0 to 255 | 1 byte

[*Approximate Numerics*](https://technet.microsoft.com/en-us/library/ms187752(v=sql.105).aspx)

Data type | Range | Storage
--- | --- | ---
`float` | - 1.79E+308 to -2.23E-308, 0 and 2.23E-308 to 1.79E+308 | Depends on the value of n
`real`, `float(24)` | - 3.40E + 38 to -1.18E - 38, 0 and 1.18E - 38 to 3.40E + 38 | 4 bytes

[*Date and Time*](https://technet.microsoft.com/en-us/library/ms187752(v=sql.105).aspx)

Data type | Output
--- | ---
`date` | 2007-05-08
`datetime` | 2007-05-08 12:35:29.123
`datetime2(7)` | 2007-05-08 12:35:29.1234567
`datetimeoffset(7)` | 2007-05-08 12:35:29.1234567 +12:15
`smalldatetime` | 2007-05-08 12:35:00
`time(7)` | 12:35:29.1234567

 [*Character Strings*](https://technet.microsoft.com/en-us/library/ms187752(v=sql.105).aspx)

Data type | Range | Storage
--- | --- | ---
`char(10)` |
`text` | 
`varchar(50)`, `varchar(MAX)` |

[*Unicode Character Strings*](https://technet.microsoft.com/en-us/library/ms187752(v=sql.105).aspx)

Data type | Range | Storage
--- | --- | ---
`nchar(10)` |
`ntext` | 
`nvarchar(50)`, `nvarchar(MAX)` |

[*Binary Strings*](https://technet.microsoft.com/en-us/library/ms187752(v=sql.105).aspx)

Data type | Range | Storage
--- | --- | ---
`binary(50)` | 
`varbinary(50)`, `varbinary(MAX)` |
`image` | 


[*Other Data Types*](https://technet.microsoft.com/en-us/library/ms187752(v=sql.105).aspx)

Data type | Range | Storage
--- | --- | ---
`hierarchyid` |
`sql_variant` |
`timestamp` |
`uniqueidentifier` |
`xml` |
`geography` |
`geometry` | 
`cursor*` |
`table*` |
