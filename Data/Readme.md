# Data Representation

## From Number Lines to Complex Data

---

# Introduction — The Big Idea

Computers ultimately represent data using **bits — 0 and 1**.

Everything else is an interpretation or organization of those bits.

```text
Bits → Bytes → Values → Primitives → Structures → Application Data
```

> **Bits are representation. Interpretation creates meaning.**

The same bits can represent completely different things depending on how they are interpreted.

| Bits       | Interpretation         | Meaning            |
| ---------- | ---------------------- | ------------------ |
| `01000001` | Unsigned integer       | `65`               |
| `01000001` | ASCII                  | `A`                |
| `01000001` | Part of a larger value | Depends on context |

This concept is the foundation for understanding memory, programming languages, databases, files, networks, serialization, and binary formats.

---

# 1. Number Lines and Bases

A number represents a value or position on a number line.

The number line does **not** change because we use a different number base. Only the way we write the number changes.

| Base                  | Representation | Value |
| --------------------- | -------------: | ----: |
| Decimal (base 10)     |           `10` |    10 |
| Binary (base 2)       |         `1010` |    10 |
| Hexadecimal (base 16) |            `A` |    10 |

### Common Number Bases

| Base | Name        | Digits     |
| ---: | ----------- | ---------- |
|    2 | Binary      | `0–1`      |
|    8 | Octal       | `0–7`      |
|   10 | Decimal     | `0–9`      |
|   16 | Hexadecimal | `0–9, A–F` |

### Key Concept

> **A number base is a representation system, not a different number line.**

For example:

```text
Decimal:      10
Binary:       1010
Hexadecimal:  A
```

All three represent the same value.

---

# 2. Binary — Base 2

Binary uses only two digits:

```text
0
1
```

Each binary digit is called a **bit**.

Each position represents a power of two.

For example:

```text
01011010₂
```

can be expanded as:

```text
0×128
+ 1×64
+ 0×32
+ 1×16
+ 1×8
+ 0×4
+ 1×2
+ 0×1
```

Therefore:

```text
01011010₂ = 90₁₀
```

### Bit Capacity

| Bits |      Possible Combinations |
| ---: | -------------------------: |
|    1 |                          2 |
|    4 |                         16 |
|    8 |                        256 |
|   16 |                     65,536 |
|   32 |              4,294,967,296 |
|   64 | 18,446,744,073,709,551,616 |

The number of possible combinations is:

```text
2ⁿ
```

where `n` is the number of bits.

### MSB and LSB

```text
MSB                    LSB
 ↓                       ↓
0101 1010
```

**MSB — Most Significant Bit**

The bit with the highest positional value.

**LSB — Least Significant Bit**

The bit with the lowest positional value.

---

# 3. Signed and Unsigned Numbers

Bits do not inherently mean positive or negative numbers.

The interpretation determines whether a bit pattern is treated as **signed** or **unsigned**.

### Unsigned

An unsigned value represents zero and positive numbers.

For 8 bits:

```text
00000000 = 0
11111111 = 255
```

Range:

```text
0 to 255
```

### Signed

Signed integers allow both positive and negative values.

Modern general-purpose computers normally use **two's complement** for signed integers.

| Representation           | Number of Values |   8-Bit Range |
| ------------------------ | ---------------: | ------------: |
| Unsigned                 |              256 |    `0 to 255` |
| Signed, two's complement |              256 | `-128 to 127` |

---

## One's Complement

One's complement is created by inverting every bit.

Example:

```text
+5

0000 0101
```

Invert the bits:

```text
1111 1010
```

In one's complement this represents `-5`.

One's complement has an unusual property: it has **two representations of zero**.

```text
0000 0000 = +0
1111 1111 = -0
```

---

## Two's Complement

Two's complement is created by:

1. Inverting all bits
2. Adding 1

Example:

```text
+5

0000 0101
```

Invert:

```text
1111 1010
```

Add 1:

```text
1111 1011
```

Therefore:

```text
1111 1011 = -5
```

Two's complement provides one representation of zero and makes binary arithmetic practical for signed integers.

### Same Bits — Different Interpretation

```text
1111 1111
```

| Interpretation                | Value |
| ----------------------------- | ----: |
| Unsigned 8-bit                | `255` |
| Signed 8-bit two's complement |  `-1` |

> **Same bits. Different interpretation. Different meaning.**

---

# 4. Hexadecimal — Base 16

Binary is ideal for computers but can be difficult for humans to read.

Hexadecimal provides a compact representation of binary data.

Hexadecimal uses:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

### Binary-to-Hex Mapping

| Binary | Hex | Decimal |
| ------ | --: | ------: |
| `0000` | `0` |       0 |
| `0001` | `1` |       1 |
| `0010` | `2` |       2 |
| `0011` | `3` |       3 |
| `0100` | `4` |       4 |
| `0101` | `5` |       5 |
| `0110` | `6` |       6 |
| `0111` | `7` |       7 |
| `1000` | `8` |       8 |
| `1001` | `9` |       9 |
| `1010` | `A` |      10 |
| `1011` | `B` |      11 |
| `1100` | `C` |      12 |
| `1101` | `D` |      13 |
| `1110` | `E` |      14 |
| `1111` | `F` |      15 |

### Why Hex Works So Well

```text
4 bits  = 1 hex digit
8 bits  = 2 hex digits
```

Example:

```text
0101 1010
```

becomes:

```text
5A
```

Therefore:

```text
01011010₂ = 5A₁₆ = 90₁₀
```

Hexadecimal is commonly used for:

* Memory addresses
* Raw bytes
* File formats
* Network packets
* Debugging
* Machine code
* Color values

---

# 5. Mathematical Operations

Because different bases represent the same number line, mathematical operations work regardless of the base.

### Example

```text
Decimal:
3 + 4 = 7

Binary:
0011 + 0100 = 0111
```

### Hexadecimal

```text
9 + 3 = C
```

and:

```text
1F + 03 = 22
```

The mathematics has not changed.

Only the notation has changed.

> **The base changes representation, not mathematics.**

---

# 6. Characters and Alphanumeric Data

Computers also need to represent text.

One approach is to assign numerical values to characters.

For example, ASCII assigns:

| Character | Numeric Value |
| --------- | ------------: |
| `A`       |            65 |
| `B`       |            66 |
| `C`       |            67 |

Therefore:

```text
A
↓
65
↓
01000001
```

The computer stores bits, but a character encoding tells software how to interpret those bits.

---

## ASCII

ASCII stands for:

**American Standard Code for Information Interchange**

Original ASCII uses **7 bits** and defines **128 codes**.

It includes:

* Uppercase letters
* Lowercase letters
* Digits
* Punctuation
* Control characters

---

## Unicode

Unicode provides a much larger system for representing characters from many writing systems.

Unicode defines **code points**.

Encodings determine how those code points are stored.

Common encodings include:

| Encoding | Typical Storage                 |
| -------- | ------------------------------- |
| UTF-8    | 1–4 bytes per encoded character |
| UTF-16   | Usually 2 or 4 bytes            |
| UTF-32   | 4 bytes per code point          |

> **Unicode is the character standard. UTF-8, UTF-16, and UTF-32 are encoding formats.**

---

# 7. Decimal and Exact Decimal Values

Decimal numbers include values such as:

```text
10
10.5
123.75
```

It is important to distinguish between **decimal representation** and a programming language or database's **decimal data type**.

Different applications require different numeric representations.

| Use Case                | Common Representation |
| ----------------------- | --------------------- |
| Whole numbers           | Integer               |
| Currency                | Decimal / fixed point |
| Scientific calculations | Floating point        |
| Measurements            | Often floating point  |
| Exact quantities        | Decimal / fixed point |

Decimal or fixed-point representations are often useful when exact decimal arithmetic matters, such as financial calculations.

---

# 8. Floating-Point Numbers

Floating-point numbers are designed to represent a very large range of values.

Examples:

```text
3.14159
98.6
0.125
12345.678
```

Conceptually, a floating-point number contains:

```text
Sign
Exponent
Fraction / Significand
```

### 32-Bit Floating Point

A common IEEE 754 single-precision representation uses:

| Component |   Bits |
| --------- | -----: |
| Sign      |      1 |
| Exponent  |      8 |
| Fraction  |     23 |
| **Total** | **32** |

### 64-Bit Floating Point

A common IEEE 754 double-precision representation uses:

| Component |   Bits |
| --------- | -----: |
| Sign      |      1 |
| Exponent  |     11 |
| Fraction  |     52 |
| **Total** | **64** |

Floating-point numbers are approximate for many decimal fractions.

For example:

```text
0.1 + 0.2
```

can produce a value extremely close to, but not exactly equal to:

```text
0.3
```

This is one reason exact decimal types are useful for applications such as financial calculations.

---

# 9. Primitives

Primitive types are the basic building blocks used to construct more complex data.

A useful analogy is **LEGO**.

Individual pieces are simple, but they can be combined to create increasingly complex structures.

### Common Primitive Categories

| Category         | Examples            |
| ---------------- | ------------------- |
| Boolean          | `true`, `false`     |
| Integer          | `int`, `long`       |
| Unsigned integer | `uint`, `ulong`     |
| Floating point   | `float`, `double`   |
| Decimal          | `decimal`           |
| Character        | `char`              |
| Binary           | `byte`              |
| Reference        | Pointer / reference |

### Storage

| Bits | Bytes |
| ---: | ----: |
|    8 |     1 |
|   16 |     2 |
|   32 |     4 |
|   64 |     8 |

---

# 10. Primitive Types Across Platforms

Different programming languages and databases use different type names, even when they represent similar underlying concepts.

| Concept        | C/C++                  | C#                | SQL Server                  |
| -------------- | ---------------------- | ----------------- | --------------------------- |
| 8-bit unsigned | `unsigned char`        | `byte`            | `tinyint`                   |
| 16-bit signed  | `short`                | `short`           | `smallint`                  |
| 32-bit signed  | `int`                  | `int`             | `int`                       |
| 64-bit signed  | `long long`            | `long`            | `bigint`                    |
| Floating point | `float`, `double`      | `float`, `double` | `real`, `float`             |
| Decimal        | Library/type dependent | `decimal`         | `decimal`, `numeric`        |
| Boolean        | `bool` / `_Bool`       | `bool`            | `bit`                       |
| Character      | `char` / wide types    | `char`            | `char`, `nchar`             |
| Text           | C strings / libraries  | `string`          | `varchar`, `nvarchar`       |
| Binary         | Buffers / arrays       | `byte[]`          | `binary`, `varbinary`       |
| Structure      | `struct`, `class`      | `struct`, `class` | Tables / user-defined types |

---

## C and C++ Primitive Types

C and C++ intentionally leave some type sizes platform-dependent.

| Type             |           Typical Size | Notes                                               |
| ---------------- | ---------------------: | --------------------------------------------------- |
| `char`           |                 1 byte | Character type; signedness varies by implementation |
| `unsigned char`  |                 1 byte | `0–255`                                             |
| `short`          |                2 bytes | Typically `-32,768–32,767`                          |
| `unsigned short` |                2 bytes | `0–65,535`                                          |
| `int`            |       Commonly 4 bytes | Platform-dependent                                  |
| `unsigned int`   |       Commonly 4 bytes | Platform-dependent                                  |
| `long`           |           4 or 8 bytes | Platform-dependent                                  |
| `long long`      |       Commonly 8 bytes | At least 64 bits                                    |
| `size_t`         |           4 or 8 bytes | Platform-dependent                                  |
| Pointer          | Typically 4 or 8 bytes | Architecture-dependent                              |

When an exact number of bits is required, C and C++ provide fixed-width integer types such as:

```text
int8_t
uint8_t
int16_t
uint16_t
int32_t
uint32_t
int64_t
uint64_t
```

These are especially useful for binary formats and network protocols.

---

## C# / .NET Primitive Types

C# provides defined sizes for its integral numeric types.

| Type      |                            Size | Range / Purpose       |
| --------- | ------------------------------: | --------------------- |
| `byte`    |                          1 byte | `0–255`               |
| `sbyte`   |                          1 byte | `-128–127`            |
| `short`   |                         2 bytes | `-32,768–32,767`      |
| `ushort`  |                         2 bytes | `0–65,535`            |
| `int`     |                         4 bytes | `-2³¹–2³¹−1`          |
| `uint`    |                         4 bytes | `0–2³²−1`             |
| `long`    |                         8 bytes | `-2⁶³–2⁶³−1`          |
| `ulong`   |                         8 bytes | `0–2⁶⁴−1`             |
| `float`   |                         4 bytes | 32-bit floating point |
| `double`  |                         8 bytes | 64-bit floating point |
| `decimal` |                        16 bytes | Decimal arithmetic    |
| `char`    |                         2 bytes | UTF-16 code unit      |
| `bool`    | Language-defined representation | `true` / `false`      |

C# also provides:

* `enum`
* `struct`
* `class`
* `string`
* Arrays
* References

A C# `char` is a **UTF-16 code unit**, so one `char` does not necessarily represent an entire Unicode character.

---

## SQL Server Data Types

SQL Server provides types designed for database storage and queries.

### Exact Numeric

| Type           |  Storage | Range / Purpose                        |
| -------------- | -------: | -------------------------------------- |
| `tinyint`      |   1 byte | `0–255`                                |
| `smallint`     |  2 bytes | `-32,768–32,767`                       |
| `int`          |  4 bytes | `-2³¹–2³¹−1`                           |
| `bigint`       |  8 bytes | `-2⁶³–2⁶³−1`                           |
| `decimal(p,s)` | Variable | Exact precision and scale              |
| `numeric(p,s)` | Variable | Equivalent to `decimal`                |
| `money`        |  8 bytes | Fixed-precision monetary value         |
| `smallmoney`   |  4 bytes | Smaller fixed-precision monetary value |

### Approximate Numeric

| Type    |      Storage | Purpose                    |
| ------- | -----------: | -------------------------- |
| `real`  |      4 bytes | 32-bit approximate numeric |
| `float` | 4 or 8 bytes | Approximate numeric        |

### Date and Time

SQL Server includes:

```text
date
datetime
datetime2
datetimeoffset
smalldatetime
time
```

### Character Strings

```text
char(n)
varchar(n)
varchar(max)

nchar(n)
nvarchar(n)
nvarchar(max)
```

The `n` types support Unicode text.

### Binary

```text
binary(n)
varbinary(n)
varbinary(max)
```

### Specialized Types

SQL Server also provides types such as:

```text
uniqueidentifier
xml
geography
geometry
hierarchyid
sql_variant
table
cursor
```

---

# 11. Records and Complex Data Structures

Primitives can be combined into more meaningful structures.

For example:

```text
Customer
├── ID
├── Name
├── Email
├── Address
└── Account Balance
```

The individual fields can use primitive types, while the overall object provides a higher-level meaning.

| Field           | Example Type |
| --------------- | ------------ |
| ID              | Integer      |
| Name            | String       |
| Email           | String       |
| Address         | Record       |
| Account Balance | Decimal      |

### Nested Data

```text
Customer
├── ID
├── Name
├── Address
│   ├── Street
│   ├── City
│   ├── State
│   └── Zip
└── Account
    ├── AccountNumber
    └── Balance
```

This is the same idea as building a larger LEGO model from smaller pieces.

```text
Primitives
    ↓
Structures
    ↓
Complex Objects
    ↓
Application Data
```

---

# 12. Crossing System Boundaries — The Representation Stack

When data moves between applications, files, networks, databases, and hardware, it passes through multiple layers of representation.

The important idea is that **each layer may represent the same underlying information differently**.

## The Representation Stack

| Layer            | What It Represents                   | Example                            |
| ---------------- | ------------------------------------ | ---------------------------------- |
| **Application**  | Business meaning                     | Customer, Order, Product           |
| **Complex Data** | Related information grouped together | Customer record                    |
| **Primitives**   | Basic data types                     | `int`, `decimal`, `string`, `bool` |
| **Values**       | Individual numbers or characters     | `42`, `19.95`, `A`                 |
| **Bytes**        | Groups of 8 bits                     | `2A`, `FF`, `41`                   |
| **Bits**         | Binary representation                | `01000001`                         |
| **Hardware**     | Physical storage and signals         | Memory cells, registers            |

### Linear Map of the Layers

```text
┌──────────────────────────────┐
│          APPLICATION         │
│     Customer / Order / Game  │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│        COMPLEX DATA          │
│       Customer Record        │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│          PRIMITIVES          │
│ int / decimal / string / bool│
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│            VALUES            │
│       42 / 19.95 / "A"       │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│            BYTES             │
│        2A / FF / 41          │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│             BITS             │
│          01000001            │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│           HARDWARE           │
│ Memory / Registers / Signals │
└──────────────────────────────┘
```

The same path can be viewed in reverse when data is retrieved:

```text
HARDWARE
   ↓
BITS
   ↓
BYTES
   ↓
VALUES
   ↓
PRIMITIVES
   ↓
COMPLEX DATA
   ↓
APPLICATION
```

---

## Crossing Between Systems

A typical application-to-database flow might look like:

```text
C# APPLICATION
      ↓
    OBJECT
      ↓
 SERIALIZATION
      ↓
 JSON / BINARY
      ↓
 NETWORK BYTES
      ↓
     API
      ↓
 SQL SERVER
      ↓
 DATABASE STORAGE
```

For example:

```text
C#:
int CustomerId = 42
```

The same information can cross several representation boundaries:

| Layer          | Representation        |
| -------------- | --------------------- |
| C# application | `int CustomerId = 42` |
| Serialization  | JSON number `42`      |
| Network        | Encoded bytes         |
| Database       | SQL Server `int`      |
| Storage        | Binary bits           |

The meaning remains **Customer ID 42**, but the representation changes as the data crosses each boundary.

---

## Common Representation Problems

| Problem             | Example                            |
| ------------------- | ---------------------------------- |
| Signed vs. unsigned | `11111111` → `255` or `-1`         |
| Integer size        | 32-bit vs. 64-bit                  |
| Character encoding  | UTF-8 vs. UTF-16                   |
| Floating point      | `0.1 + 0.2` precision              |
| Decimal precision   | `decimal(18,2)` vs. floating point |
| Date/time           | Time zones and offsets             |
| Endianness          | Byte ordering                      |
| Serialization       | JSON vs. binary representation     |
| Null handling       | `NULL` vs. `0` vs. empty string    |

---

## Endianness

A multi-byte value such as:

```text
0x12345678
```

may be stored in different byte orders.

### Big-Endian

```text
12 34 56 78
```

### Little-Endian

```text
78 56 34 12
```

The bytes contain the same information, but the order determines how the value is reconstructed.

---

## The Key Principle

At every system boundary, two questions must be answered:

1. **How are the bits represented?**
2. **How should those bits be interpreted?**

```text
BITS
  ↓
REPRESENTATION
  ↓
INTERPRETATION
  ↓
MEANING
```

Data interoperability is therefore not simply about moving bytes from one system to another.

The receiving system must understand **how those bytes are organized and what they mean**.

---

# 13. Verification Digests

Another way systems process data is by creating a **digest** or hash.

The general process is:

```text
DATA
  ↓
HASH ALGORITHM
  ↓
DIGEST
```

A digest can be used to determine whether data has changed.

| Algorithm | Primary Use / Characteristic                                                         |
| --------- | ------------------------------------------------------------------------------------ |
| CRC       | Detect accidental data corruption                                                    |
| MD5       | 128-bit hash; cryptographically broken for security applications                     |
| SHA-1     | 160-bit hash; cryptographically broken for collision-resistant security applications |
| SHA-256   | 256-bit cryptographic hash widely used for modern applications                       |

### Verification vs. Security

A checksum or hash used for **error detection** is not necessarily suitable for **security**.

For example:

```text
Original Data
     ↓
 SHA-256
     ↓
Digest
```

The recipient can calculate the SHA-256 digest again and compare the result.

If the values differ, the data has changed.

> **A digest represents the data; it does not contain the original data in a directly reversible form.**

---

# 14. Same Bits — Different Meaning

Consider:

```text
01000001
```

Those bits do not inherently mean `65` or `A`.

Their meaning depends on the interpretation.

| Interpretation         | Meaning                      |
| ---------------------- | ---------------------------- |
| Unsigned integer       | `65`                         |
| ASCII                  | `A`                          |
| Part of a larger value | Depends on surrounding bytes |
| Raw binary             | One byte of data             |

This is the central lesson of data representation:

> **The bits themselves do not provide the complete meaning.**

Meaning comes from the rules used to interpret them.

---

# 15. From Bits to Applications

The entire concept can be viewed as a progression from physical representation to application-level meaning.

```text
APPLICATION
      ↓
COMPLEX DATA
      ↓
RECORDS / CLASSES
      ↓
PRIMITIVES
      ↓
NUMBERS / CHARACTERS
      ↓
BYTES
      ↓
BITS
      ↓
PHYSICAL HARDWARE
```

Programmers work with concepts such as:

```text
Customer
Order
Product
Address
Image
Game Asset
Database Record
```

The computer does not inherently know what these concepts mean.

The application creates that meaning by organizing and interpreting lower-level data.

---

# 16. Final Takeaway

When working with data, ask three questions:

| Question                      | What to Determine                                        |
| ----------------------------- | -------------------------------------------------------- |
| **What are the bits?**        | What data is physically represented?                     |
| **How are they organized?**   | How are bits grouped into bytes, fields, and structures? |
| **How are they interpreted?** | What rules determine their meaning?                      |

The complete model is:

```text
BITS
  ↓
REPRESENTATION
  ↓
INTERPRETATION
  ↓
MEANING
```

And the larger hierarchy is:

```text
BITS
  ↓
BYTES
  ↓
VALUES
  ↓
PRIMITIVES
  ↓
STRUCTURES
  ↓
COMPLEX DATA
  ↓
APPLICATION MEANING
```

This foundation applies to:

* Computer memory
* Programming languages
* File formats
* Databases
* Networking
* Serialization
* Binary protocols
* Compression
* Encryption
* Game assets
* Data interchange

> **Everything a computer does with data begins with bits and ends with interpretation.**
