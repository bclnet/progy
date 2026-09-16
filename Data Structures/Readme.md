# Data Structures

Data structures organize data in memory or storage so that it can be efficiently **accessed, modified, searched, and processed**.

The previous document covered bits and bytes. Here we focus on how those bytes are organized.

```text
BYTES → MEMORY → VALUES → DATA STRUCTURES → APPLICATION DATA
```

| Structure       | Purpose                              |
| --------------- | ------------------------------------ |
| Variable        | Store one value                      |
| Array           | Store an indexed sequence            |
| Struct / Record | Group related fields                 |
| Pointer         | Refer to another memory location     |
| Stack           | Last-in, first-out                   |
| Queue           | First-in, first-out                  |
| List            | Maintain an ordered collection       |
| Hash            | Convert data into a lookup value     |
| Tree            | Represent hierarchical relationships |
| B-Tree          | Organize data for block/page storage |
| Stream          | Process data incrementally           |

---

# 1. Memory Allocation

Programs request memory from a pool of available memory.

```c
void *stuff = malloc(100);

/* use memory */

free(stuff);
```

| Operation   | Purpose                             |
| ----------- | ----------------------------------- |
| `malloc(n)` | Request at least `n` bytes          |
| `free(p)`   | Release previously allocated memory |
| `sizeof(x)` | Determine the size of a type/object |

### Parking Garage Analogy

```text
Memory
┌─────┬─────┬─────┬─────┬─────┬─────┐
│Used │Free │Free │Used │Free │Used │
└─────┴─────┴─────┴─────┴─────┴─────┘
```

Think of memory as parking spaces:

* Space = storage
* Group of spaces = allocation
* `malloc` = request space
* `free` = release space
* Allocator = garage manager

As allocations are created and released, free memory can become scattered. This is **fragmentation**.

---

# 2. Memory Size

Use bytes when discussing storage requirements.

| Common Type |           Typical Size |
| ----------- | ---------------------: |
| `byte`      |                 1 byte |
| `short`     |                2 bytes |
| `int`       |                4 bytes |
| `long`      |                8 bytes |
| `double`    |                8 bytes |
| Pointer     | Typically 4 or 8 bytes |

Actual sizes depend on the language and platform.

For structures, account for **padding and alignment**.

---

# 3. Arrays

An array stores elements of the same type, normally in contiguous memory.

```text
[ A ][ B ][ C ]
  0    1    2
```

```c
int Player[3];
```

An element's location can be calculated:

```text
Address = Base + Index × Element Size
```

If `int` = 4 bytes:

| Element     |  Offset |
| ----------- | ------: |
| `Player[0]` | 0 bytes |
| `Player[1]` | 4 bytes |
| `Player[2]` | 8 bytes |

### Array Tradeoffs

| Pros                          | Cons                                    |
| ----------------------------- | --------------------------------------- |
| Fast indexed access           | Fixed-size arrays cannot grow           |
| Compact                       | Insert/delete may require shifting      |
| Contiguous and cache-friendly | Requires appropriate contiguous storage |
| Simple                        | Growing arrays may require copying      |

---

# 4. Character Arrays

C strings are commonly stored as character arrays.

```c
char Name[100];
```

Example:

```text
[ S ][ K ][ Y ][ \0 ][ ][ ][ ... ]
```

The `\0` marks the end of a C string.

---

# 5. Structs / Records

A struct groups related fields, potentially of different types.

```c
struct Month {
    int Players;
    int Wins;
    bool Pizza;
};
```

```text
Month
├── Players
├── Wins
└── Pizza
```

| Structure        | Organizes                                |
| ---------------- | ---------------------------------------- |
| Array            | Multiple values of the same element type |
| Struct           | Related fields                           |
| Array of structs | Multiple related records                 |

Example:

```c
struct Month Months[12];
```

creates 12 `Month` records.

### Struct Size

Do not assume:

```text
4 + 4 + 1 = 9 bytes
```

Compilers may add padding.

Use:

```c
sizeof(struct Month)
```

to determine the actual size.

---

# 6. Pointers

A pointer stores an address that identifies another object.

```c
int x = 100;
int *p = &x;
```

Conceptually:

```text
p ─────→ x
        [100]
```

| Operator | Meaning                          |
| -------- | -------------------------------- |
| `&x`     | Address of `x`                   |
| `*p`     | Value at the address held by `p` |

Pointers allow structures to connect objects that are **not physically adjacent in memory**.

---

# 7. Enumeration and Traversal

**Enumeration** means visiting elements in a collection.
**Traversal** means moving through the structure to visit those elements.

For a linear collection:

```c
for (int i = 0; i < 10; i++) {
    /* process element */
}
```

```text
[0] → [1] → [2] → ... → [9]
```

| Structure   | Typical Traversal     |
| ----------- | --------------------- |
| Array       | Index → index → index |
| Linked list | Node → next node      |
| Tree        | Node → child nodes    |
| Hash table  | Key → bucket → entry  |

For a simple linear traversal, work generally grows with the number of elements.

---

# 8. Stack

A stack follows:

> **LIFO — Last In, First Out**

```text
       TOP
        ↓
      [ C ] ← Pop
      [ B ]
      [ A ]
```

| Operation | Meaning         |
| --------- | --------------- |
| Push      | Add to top      |
| Pop       | Remove from top |
| Peek      | Inspect top     |

Common uses:

* Function calls
* Undo operations
* Expression processing
* Depth-first traversal

---

# 9. Queue

A queue follows:

> **FIFO — First In, First Out**

```text
IN                         OUT
 ↓                          ↓
[A] → [B] → [C] → [D] ─────→
```

| Operation | Meaning           |
| --------- | ----------------- |
| Enqueue   | Add to back       |
| Dequeue   | Remove from front |
| Peek      | Inspect front     |

Common uses:

* Work queues
* Network messages
* Task scheduling
* Event processing
* Breadth-first traversal

---

# 10. Lists

A list is an ordered collection.

```text
LIST
├── Linked List
├── Doubly Linked List
└── Dynamic / Expanding Array
```

| Type               | Storage         | Main Characteristic            |
| ------------------ | --------------- | ------------------------------ |
| Linked list        | Scattered nodes | Nodes connected by pointers    |
| Doubly linked list | Scattered nodes | Previous + next pointers       |
| Dynamic array      | Contiguous      | Automatically expands capacity |

### Linked List

```text
[ A | Next ] → [ B | Next ] → [ C | Next ] → NULL
```

The physical memory may be scattered:

```text
[ A ][ unused ][ C ][ unused ][ B ]
```

The pointers create the logical order:

```text
A → B → C
```

### Dynamic / Expanding Array

```text
Initial:
[ A ][ B ][ C ][ D ]

Expand:
[ A ][ B ][ C ][ D ][ E ][ ][ ][ ]
```

When capacity is exhausted, a larger block may be allocated and the existing elements copied.

---

# 11. Collections

A **collection** is an abstraction representing multiple elements.

```text
                 COLLECTION
                     │
       ┌─────────────┼─────────────┐
       ↓             ↓             ↓
     ARRAY          LIST          MAP
       │             │             │
       │       ┌─────┼─────┐       │
       │       ↓     ↓     ↓       │
       │    Linked Doubly Dynamic  │
       │     List   List   Array   │
```

The collection interface describes **what you can do** with the data.

The underlying data structure determines **how it is stored and accessed**.

---

# 12. Hashing

A hash function converts input data into a hash value.

```text
DATA
 ↓
HASH FUNCTION
 ↓
HASH VALUE
```

A hash can be used to help locate data quickly.

```text
KEY
 ↓
HASH
 ↓
BUCKET
 ↓
VALUE
```

### Hash vs. Digest

| Term       | Meaning                                                                   |
| ---------- | ------------------------------------------------------------------------- |
| Hash       | Value produced by a hash function                                         |
| Hash table | Data structure using hashes for lookup                                    |
| Digest     | Output of a hashing algorithm, commonly referring to cryptographic hashes |
| SHA-256    | Cryptographic hash producing a 256-bit digest                             |

A hash table may have **collisions**, where multiple keys map to the same bucket.

---

# 13. Trees

Trees represent hierarchical relationships.

```text
             [A]
            /   \
          [B]   [C]
         /  \     \
       [D]  [E]   [F]
```

Common tree types:

| Tree               | Characteristic                                 |
| ------------------ | ---------------------------------------------- |
| Binary tree        | Maximum of 2 children                          |
| Binary search tree | Ordered binary tree                            |
| AVL tree           | Self-balancing binary search tree              |
| B-tree             | Multi-way tree designed for block/page storage |

---

# 14. Binary Trees

A binary tree has at most two children per node.

```text
          [A]
         /   \
       [B]   [C]
       / \
     [D] [E]
```

The two child positions are commonly called **left** and **right**.

A binary tree does not inherently require the values to be ordered.

---

# 15. Binary Search Trees

A binary search tree adds an ordering rule.

```text
             [50]
            /    \
          [25]   [75]
          / \     / \
        [10][30][60][90]
```

Common rule:

```text
Left < Node < Right
```

This allows searching to eliminate portions of the tree.

A poorly balanced tree can degrade toward a linear structure.

---

# 16. AVL Trees

An AVL tree is a **self-balancing binary search tree**.

When insertions or deletions make the tree unbalanced, rotations restore the balance.

```text
Unbalanced:

    30
      \
       40
         \
          50


Balanced:

      40
     /  \
   30    50
```

The goal is to keep the tree height controlled so searching remains efficient.

---

# 17. B-Trees

A B-tree differs from a binary tree because a node can contain **many keys and many child references**.

```text
          [100 | 500 | 1000 | 1500]
          /    |     |       |      \
        ...   ...   ...     ...     ...
```

This is particularly useful when storage is accessed in blocks or pages.

```text
DATABASE
   ↓
PAGES / BLOCKS
   ↓
B-TREE INDEX
   ↓
RECORDS
```

Instead of following many individual binary-tree nodes, a B-tree can retrieve many keys and references from one page.

> **B-trees align the logical data structure with block-oriented physical storage.**

---

# 18. Clustering

Clustering considers the **physical location of data**.

The goal is to organize related data so that data commonly accessed together is physically organized together.

```text
LOGICAL ACCESS
      ↓
DATA ORGANIZATION
      ↓
PHYSICAL LOCATION
      ↓
STORAGE
```

This matters particularly for databases and large storage systems.

> **Clustering connects logical organization with physical storage location.**

---

# 19. SQL Data Structures and Types

SQL databases provide both data types and physical structures for storing data.

### Character Types

| Type            | Description                                  |
| --------------- | -------------------------------------------- |
| `CHAR(n)`       | Fixed-length character data                  |
| `VARCHAR(n)`    | Variable-length character data               |
| `VARCHAR(MAX)`  | Large variable-length character data         |
| `NCHAR(n)`      | Fixed-length Unicode character data          |
| `NVARCHAR(n)`   | Variable-length Unicode character data       |
| `NVARCHAR(MAX)` | Large variable-length Unicode character data |

Example:

```sql
CHAR(10)
```

conceptually provides:

```text
[1][2][3][4][5][6][7][8][9][10]
```

while:

```sql
NVARCHAR(50)
```

stores variable-length Unicode text up to its declared limit.

---

# 20. Streaming

Streaming means processing data **incrementally rather than creating the entire result at once**.

```text
SOURCE
  ↓
ITEM → PROCESS → OUTPUT
  ↓
ITEM → PROCESS → OUTPUT
  ↓
ITEM → PROCESS → OUTPUT
```

This can reduce memory usage and allow processing to begin before the entire dataset has been produced.

---

# 21. `yield` and C#

C# uses `yield return` to create iterator-based sequences.

```csharp
IEnumerable<int> Numbers()
{
    for (int i = 0; i < 10; i++)
    {
        yield return i;
    }
}
```

The caller can consume the values:

```csharp
foreach (var number in Numbers())
{
    // process number
}
```

The important distinction is:

```text
Traditional collection:

Create ALL
    ↓
Store ALL
    ↓
Process ALL


Iterator / stream:

Create ONE
    ↓
Process ONE
    ↓
Create NEXT
    ↓
Process NEXT
```

---

# 22. LINQ

C# LINQ allows operations to be chained into a processing pipeline.

```csharp
var result =
    players
        .Where(p => p.Active)
        .Select(p => p.Name);
```

Conceptually:

```text
Players
   ↓
Filter
   ↓
Transform
   ↓
Names
```

Instead of explicitly creating an intermediate collection after every operation, an enumerable pipeline can process elements as they are requested.

### Copying vs. Streaming

```text
COPYING / MATERIALIZING

Collection A
     ↓
Filtered Collection
     ↓
Transformed Collection
     ↓
Final Collection
```

versus:

```text
ENUMERABLE PIPELINE

Item
 ↓
Filter
 ↓
Transform
 ↓
Output

Next Item
 ↓
Filter
 ↓
Transform
 ↓
Output
```

This is commonly associated with **deferred execution**.

The query describes the operations first; the operations are generally performed when the result is enumerated.

### Important Limitation

Not every operation can be purely streaming.

Operations such as:

| Operation         | Why                                               |
| ----------------- | ------------------------------------------------- |
| `Sort`            | Usually needs the complete set to determine order |
| `GroupBy`         | Must organize items by group                      |
| `Reverse`         | Generally needs prior items available             |
| Some aggregations | Must maintain accumulated state                   |

So streaming primarily provides **incremental processing and potentially lower memory usage**, not an automatic performance improvement.

---

# 23. Data Structure Comparison

| Structure     | Access Model     | Memory Layout             | Best Suited For                 |
| ------------- | ---------------- | ------------------------- | ------------------------------- |
| Array         | Index            | Contiguous                | Direct indexed access           |
| Dynamic Array | Index            | Contiguous                | Growing sequences               |
| Linked List   | Follow links     | Scattered                 | Frequent node insertion/removal |
| Stack         | Top              | Depends on implementation | LIFO processing                 |
| Queue         | Front/back       | Depends on implementation | FIFO processing                 |
| Hash Table    | Key              | Buckets                   | Key lookup                      |
| Binary Tree   | Hierarchical     | Usually linked nodes      | Hierarchical data               |
| AVL Tree      | Ordered search   | Linked nodes              | Balanced in-memory search       |
| B-Tree        | Multi-way search | Pages/blocks              | Database/storage indexes        |
| Enumerable    | Sequential       | Depends on source         | Incremental processing          |

---

# 24. Choosing a Data Structure

Choose based on **how the data will be used**.

| Requirement                      | Candidate           |
| -------------------------------- | ------------------- |
| Direct index access              | Array               |
| Growing indexed collection       | Dynamic Array       |
| Frequent node insertion/removal  | Linked List         |
| Last item processed first        | Stack               |
| First item processed first       | Queue               |
| Lookup by key                    | Hash Table          |
| Hierarchical relationships       | Tree                |
| Balanced ordered search          | AVL Tree            |
| Data stored in pages/blocks      | B-Tree              |
| Process large data incrementally | Enumerable / Stream |
| Physical data locality matters   | Clustering          |

---

# 25. Putting It All Together

```text
                    DATA
                      │
             ┌────────┴────────┐
             ↓                 ↓
        INDIVIDUAL          COLLECTION
          VALUES                │
                                ↓
                ┌───────────────┼───────────────┐
                ↓               ↓               ↓
              ARRAY            LIST            MAP
                                │               │
                         ┌──────┼──────┐        │
                         ↓      ↓      ↓        │
                      Linked  Doubly Dynamic   HASH
                       List    List   Array     │
                                                 ↓
                                              LOOKUP

                    COLLECTION
                         │
                         ↓
                       TREES
                         │
                ┌────────┼────────┐
                ↓        ↓        ↓
             Binary     AVL     B-Tree
                                  │
                                  ↓
                              DATABASE

                    DATA PROCESSING
                         │
                         ↓
                     ENUMERABLE
                         │
                         ↓
                      STREAMING
```

The progression is:

```text
MEMORY
  ↓
VALUES
  ↓
STRUCTURES
  ↓
COLLECTIONS
  ↓
ALGORITHMS
  ↓
DATA ACCESS
  ↓
APPLICATION BEHAVIOR
```

---

# Glossary

| Term               | Description                                         |
| ------------------ | --------------------------------------------------- |
| Array              | Indexed, typically contiguous collection            |
| Struct             | Group of related fields                             |
| Pointer            | Address/reference to another object                 |
| Enumeration        | Visiting elements in a collection                   |
| Traversal          | Moving through a data structure                     |
| Stack              | LIFO collection                                     |
| Queue              | FIFO collection                                     |
| List               | Ordered collection                                  |
| Linked List        | Nodes connected by pointers                         |
| Dynamic Array      | Array-backed collection that can grow               |
| Hash               | Value generated from input by a hash function       |
| Digest             | Output of a hashing algorithm                       |
| Hash Table         | Key lookup structure using hashes                   |
| Tree               | Hierarchical data structure                         |
| Binary Tree        | Tree with at most two children per node             |
| BST                | Ordered binary search tree                          |
| AVL Tree           | Self-balancing BST                                  |
| B-Tree             | Multi-way tree designed for block/page storage      |
| Collection         | Abstraction representing multiple elements          |
| Clustering         | Organization based partly on physical data location |
| Stream             | Incremental data processing                         |
| Iterator           | Mechanism for producing elements sequentially       |
| `yield`            | C# mechanism for producing iterator values          |
| LINQ               | C# query and transformation framework               |
| Deferred Execution | Delaying query execution until enumeration          |
| Fragmentation      | Free memory separated into multiple regions         |
| Padding            | Extra bytes added for alignment                     |

---

# Final Takeaway

Data structures answer a fundamental question:

> **How should data be organized so that the computer can work with it efficiently?**

```text
ARRAY      → indexed access
LIST       → connected sequence
STACK      → last in, first out
QUEUE      → first in, first out
HASH       → key-based lookup
TREE       → hierarchy
B-TREE     → block-based storage
STREAM     → incremental processing
```

The important design principle is:

> **Choose the structure based on how the data will be accessed, changed, searched, stored, and processed.**
