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
`arch (architecture)`, `cisc`, `risc` | the type of processing used
`stepping` | small modification to a `architecture and version`
`bus size` | size of the `freeway` in lanes. a `64bit computer` would be freeways with 64 lanes everywhere.
`cpu (central processing unit)`, `core` | the brains of the computer
`ram`, `memory` | the temporary storage used by the cpu
`pcie (peripheral component interconnect express)`, `bus` | a bus of peripherals
`storage`, `hard drive`, `ssd`, `nvme` | a device which connects to a long term storage like a hard drive
`nic (network interface card)` | a device which connects to a network, like an ethernet card
`hid (human inteface device)` | a device which interacts with a human, like a keyboard or mouse
`endian`, `little endian`, `big endian` | the way values are phyically layed down
*Application Elements* | *Description*
`os (operating system)` | tbd
`thread` | tbd
`process` | tbd
`handle` | tbd
`stack` | tbd
`heap` | tbd
`register` | tbd
`instruction pointer` | tbd
`page` | tbd
*Images* | *Description*
`image`, | tbd
`exe (executable)`, `app (application)` | tbd
`library`, `so (shared library)`, `dll (dynamic library)` | tbd
*Compiling* | *Description*
`ide (integrated development environment)` | tbd
`tool-chain` | tbd
`compiler` | tbd
`linker` | tbd
`debugger` | tbd
