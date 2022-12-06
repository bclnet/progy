# Data Structures
xxx

## Memory allocation (malloc)

Memory allocation

* Shared fixed set of resource
* asked for contiguous blocks
* release allocated blocks

Parking garage

* works like a parking lot, where each parking space represents a byte
* ask for a parking space(s)
* release parking space(s)
* so many parking space(s) and garage levels where a whole floor is allocated to one process


```
void *stuff = malloc(100);
...
free(stuff);
```

### ARRAY
An array data structure, or simply an array, is a data structure consisting of a collection of elements (values or variables), each identified by at least one array index or key. An array is stored so that the position of each element can be computed from its index tuple by a mathematical formula.
- Player1 int, Player2 int, Player3 int -> Player int[3]
- Player + 3 * sizeof(int)

```
char Name[100]=string
```

### RECORD
a record (also called a structure, struct, or compound data) is a basic data structure. ... A record type is a data type that describes such values and variables. Most modern computer languages allow the programmer to define new record types.

- Players int[12], Wins int[12], Pizzas bool[12]

```
struct Month {
   int Players,
   int Wins,
   bool Pizza,
};
```

Months Month[12]

Month.Players = 100

sizeof(Month)=9


### LINKED LIST
an ordered set of data elements, each containing a link to its successor (and sometimes its predecessor).

```
struct Item {
   int Players,
   struct Item *Next,
};
```

### BINARY TREE
a data structure in which a record is linked to two successor records, usually referred to as the left branch when greater and the right when less than the previous record.



---
## Glossary
Name | Description
--- | ---
`variable`, `scaler` | a single element - 1d
`array`, `vector`, `list` | a list of elements - 2d
`linked list`, `circular liked list`, `doubly linked list` | a list of elements - 2d
`dictionary`, `map` | a list of key=value pairs indexed by key - 3d
`binary tree`, `b-tree` | the brains of the computer
