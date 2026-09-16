# Languages

## 1. The Big Idea

A programming language provides a structured way for humans to express instructions and data operations.

```text
SOURCE CODE
    ↓
TOKENS
    ↓
PARSE
    ↓
AST
    ↓
SEMANTIC ANALYSIS
    ↓
COMPILE / INTERPRET
    ↓
MACHINE CODE / BYTECODE
    ↓
RUNTIME
    ↓
CPU
```

| Concept           | Purpose                                     |
| ----------------- | ------------------------------------------- |
| Language          | Defines syntax and meaning                  |
| Lexer             | Converts source into tokens                 |
| Parser            | Determines structure                        |
| AST               | Represents program structure                |
| Semantic Analysis | Validates meaning and types                 |
| Compiler          | Translates the program                      |
| Runtime           | Executes and supports the program           |
| Framework         | Provides application structure and services |

---

# 2. Tokenization

**Tokenization** breaks source text into meaningful units.

```text
1.234 my name;
       ↓
number: 1.234
identifier: my
identifier: name
symbol: ;
```

| Token      | Example                 |
| ---------- | ----------------------- |
| Keyword    | `if`, `class`, `return` |
| Identifier | `name`, `age`           |
| Number     | `123`, `1.234`          |
| String     | `"hello"`               |
| Operator   | `+`, `=`, `==`          |
| Symbol     | `;`, `{`, `}`           |

Whitespace may separate tokens but its significance depends on the language.

---

# 3. Strings and Escaping

Strings can contain characters that otherwise have special meaning. **Escaping** provides a way to represent them literally.

```text
"my \"name\" was here"
        ↓
my "name" was here
```

| Sequence | Common Meaning  |
| -------- | --------------- |
| `\0`     | Null            |
| `\'`     | Single quote    |
| `\"`     | Double quote    |
| `\\`     | Backslash       |
| `\n`     | Newline         |
| `\r`     | Carriage return |
| `\t`     | Tab             |

Escape rules are language-specific.

| Language           | Example                          |
| ------------------ | -------------------------------- |
| C / C++ / C#       | `"my \"name\""`                  |
| JavaScript         | `'text'`, `"text"`, `` `text` `` |
| SQL                | `'text'`                         |
| C# verbatim string | `@"my ""name"""`                 |

---

# 4. Lexical Analysis

The **lexer** converts source code into tokens.

```text
SOURCE
   ↓
 LEXER
   ↓
TOKENS
```

Example:

```c
int age = 10;
```

| Text  | Token      |
| ----- | ---------- |
| `int` | Keyword    |
| `age` | Identifier |
| `=`   | Operator   |
| `10`  | Number     |
| `;`   | Symbol     |

The lexer answers:

> **What are the pieces?**

---

# 5. Parsing

The **parser** determines how tokens fit together according to the language grammar.

```text
TOKENS
   ↓
PARSER
   ↓
AST
```

Example:

```c
age = 10 + 5;
```

```text
       Assignment
       /         \
     age          +
                /   \
              10     5
```

| Stage             | Question                 |
| ----------------- | ------------------------ |
| Lexer             | What are the tokens?     |
| Parser            | How are they structured? |
| Semantic analysis | Do they make sense?      |

---

# 6. Abstract Syntax Tree

An **AST** represents the logical structure of source code as a tree.

ASTs are used by:

| Use             | Purpose                     |
| --------------- | --------------------------- |
| Compiler        | Generate executable code    |
| IDE             | Understand source structure |
| Formatter       | Reformat code               |
| Refactoring     | Safely modify code          |
| Linter          | Find problems               |
| Static analyzer | Analyze program behavior    |
| Code generator  | Produce source/code         |

---

# 7. Semantic Analysis

After parsing, the language processor checks whether the program is meaningful.

```c
int age = "hello";
```

The syntax can be valid while the types are incompatible.

| Check       | Example                        |
| ----------- | ------------------------------ |
| Type        | `int = string`                 |
| Scope       | Is `age` visible?              |
| Declaration | Does `foo()` exist?            |
| Access      | Is the member accessible?      |
| Arguments   | Are function parameters valid? |
| Return      | Is the returned value valid?   |

---

# 8. Keywords and Symbols

Languages reserve certain words for their own purposes.

| Category    | Examples                               |
| ----------- | -------------------------------------- |
| Keywords    | `if`, `else`, `for`, `class`, `return` |
| Operators   | `+`, `-`, `*`, `/`, `==`               |
| Delimiters  | `(`, `)`, `{`, `}`, `[` , `]`          |
| Terminators | `;`                                    |
| Identifiers | Programmer-defined names               |

Identifiers may have:

* scope
* lifetime
* visibility
* access level

---

# 9. High-Level Language Features

Languages add features that make source code easier to express.

| Feature       | Description                         | Example         |
| ------------- | ----------------------------------- | --------------- |
| Macro         | Source transformation               | `#define`       |
| Preprocessor  | Processes source before compilation | `#include`      |
| Interpolation | Inserts values into strings         | `$"Age: {age}"` |
| Generics      | Parameterized types/code            | `List<T>`       |
| Lambda        | Inline function                     | `x => x + 1`    |
| Async         | Non-blocking programming model      | `await`         |

### C/C++ Preprocessor

```c
#include <stdio.h>
#define VALUE 10

#if VALUE
#endif
```

### String Interpolation

```csharp
var age = 3;
var text = $"my {age}";
```

```javascript
let age = 3;
let text = `my ${age}`;
```

---

# 10. Language Architecture

Languages can execute through different architectures.

| Architecture    | Description                                       | Examples                      |
| --------------- | ------------------------------------------------- | ----------------------------- |
| Native compiled | Compiled directly to CPU instructions             | C, C++, Rust                  |
| Interpreted     | Runtime executes source/intermediate instructions | Python                        |
| Virtual Machine | Executes intermediate code on a VM                | Java, C#                      |
| JIT             | Compiles code during execution                    | JVM, .NET, JavaScript engines |
| AOT             | Compiles before execution                         | Native/AOT deployments        |
| Hybrid          | Combines multiple techniques                      | Many modern languages         |

### Native

```text
C / C++ / Rust
      ↓
   Compiler
      ↓
 Machine Code
      ↓
     CPU
```

### Virtual Machine

```text
Java / C#
    ↓
 Compiler
    ↓
Bytecode / IL
    ↓
 JVM / CLR
    ↓
Machine Code
    ↓
   CPU
```

---

# 11. Language Release

Languages, compilers, runtimes, and frameworks evolve through versions.

| Release | Typical Purpose                            |
| ------- | ------------------------------------------ |
| Major   | Major features / possible breaking changes |
| Minor   | New compatible features                    |
| Patch   | Bug and security fixes                     |
| Preview | Pre-release features                       |
| LTS     | Long-term support                          |

A language, compiler, runtime, and framework can have different release schedules.

```text
LANGUAGE
   │
   ├── Compiler
   ├── Runtime
   ├── Standard Library
   └── Framework
```

---

# 12. Static vs Dynamic Typing

|                  | Static                 | Dynamic                     |
| ---------------- | ---------------------- | --------------------------- |
| Type checking    | Primarily compile time | Primarily runtime           |
| Variable types   | Known before execution | Determined during execution |
| Typical examples | C, C++, C#, Java, Rust | Python, JavaScript, Ruby    |
| Flexibility      | More constraints       | More runtime flexibility    |

Example:

```c
int age = 10;
```

versus:

```python
age = 10
age = "ten"
```

**Dynamic does not mean typeless.**

Static/dynamic describes **when type information is checked**.

---

# 13. Strong vs Weak Typing

Static/dynamic and strong/weak are separate concepts.

| Concept           | Question                                  |
| ----------------- | ----------------------------------------- |
| Static vs Dynamic | When are types checked?                   |
| Strong vs Weak    | How strictly are different types treated? |

Because "strong" and "weak" do not have universally consistent definitions, it is often more precise to describe actual conversion and type-checking behavior.

---

# 14. Memory Management

Languages use different approaches to memory and resource management.

| Model              | Description                               | Example  |
| ------------------ | ----------------------------------------- | -------- |
| Manual             | Programmer allocates/releases memory      | C        |
| RAII               | Resource lifetime follows object lifetime | C++      |
| Garbage Collection | Runtime reclaims unreachable objects      | C#, Java |
| Reference Counting | Tracks references to objects              | Swift    |
| Ownership          | Compiler enforces ownership/lifetime      | Rust     |

---

# 15. Single-Threaded vs Multi-Threaded

A process may contain one or many threads.

| Model           | Description                       |
| --------------- | --------------------------------- |
| Single-threaded | One execution path                |
| Multi-threaded  | Multiple execution paths          |
| Process         | Running program and its resources |
| Thread          | Execution path within a process   |

```text
Single Thread

PROCESS
   │
 THREAD
   │
 EXECUTE
```

```text
Multiple Threads

PROCESS
   ├── THREAD 1
   ├── THREAD 2
   ├── THREAD 3
   └── THREAD 4
```

Threads within a process commonly share memory and other process resources.

---

# 16. Concurrency and Parallelism

| Concept     | Meaning                                                             |
| ----------- | ------------------------------------------------------------------- |
| Concurrency | Multiple tasks make progress during the same period                 |
| Parallelism | Multiple tasks execute simultaneously                               |
| Async       | Operations can continue without blocking the current execution path |
| Thread Pool | Reuses a collection of worker threads                               |
| Event Loop  | Processes events and scheduled work                                 |

```text
CONCURRENCY
Task A ──┐
         ├── execution over time
Task B ──┘
```

```text
PARALLELISM
Core 1 → Task A
Core 2 → Task B
Core 3 → Task C
```

**Asynchronous execution does not necessarily require multiple threads.**

---

# 17. Language Execution Models

A language may support one or several programming models.

| Model           | Description                               |
| --------------- | ----------------------------------------- |
| Sequential      | Instructions execute in an ordered flow   |
| Procedural      | Procedures/functions organize operations  |
| Object-Oriented | Objects combine data and behavior         |
| Functional      | Functions and transformations are central |
| Declarative     | Describes desired results                 |
| Event-Driven    | Responds to events                        |
| Data-Oriented   | Organizes data for efficient processing   |
| Query           | Describes desired data                    |

---

# 18. Assembly

Assembly is a low-level language associated with a specific **Instruction Set Architecture (ISA)**.

```text
HIGH LEVEL
    ↓
C / C++ / Rust
    ↓
ASSEMBLY
    ↓
MACHINE INSTRUCTIONS
    ↓
CPU
```

Examples of ISAs:

| ISA    | Common Architecture            |
| ------ | ------------------------------ |
| x86-64 | Intel / AMD PCs and servers    |
| ARM64  | Phones, Apple Silicon, servers |
| RISC-V | Open ISA ecosystem             |

Assembly is therefore much more architecture-specific than most high-level languages.

---

# 19. C and C++

C and C++ share historical roots but are separate languages.

| Feature               | C / C++ |
| --------------------- | ------- |
| Native compilation    | Yes     |
| Preprocessor          | Yes     |
| Multiple source files | Yes     |
| Linking               | Yes     |
| Direct memory access  | Yes     |
| `//` comments         | Yes     |
| `/* */` comments      | Yes     |
| Semicolon statements  | Common  |

Typical build:

```text
SOURCE
  ↓
PREPROCESSOR
  ↓
COMPILER
  ↓
OBJECT FILES
  ↓
LINKER
  ↓
EXECUTABLE
```

Common preprocessor directives:

```text
#include
#define
#if
#ifdef
#ifndef
#endif
```

---

# 20. HTML, CSS, and Markdown

These are markup languages rather than general-purpose programming languages.

| Language | Purpose                     | Example                    |
| -------- | --------------------------- | -------------------------- |
| HTML     | Document structure          | `<a href="value">text</a>` |
| CSS      | Presentation/layout         | `.small { ... }`           |
| Markdown | Lightweight text formatting | `# Heading`                |

Typical processing:

```text
MARKUP
   ↓
PARSER
   ↓
STRUCTURED REPRESENTATION
   ↓
OUTPUT / RENDERING
```

---

# 21. SQL

SQL is primarily a declarative language for working with relational data.

```sql
SELECT MyField
FROM MyTable
WHERE MyField = 'MyValue';
```

Typical database processing:

```text
SQL
 ↓
Parser
 ↓
Query Plan
 ↓
Optimizer
 ↓
Database Engine
 ↓
Storage
```

The SQL statement describes **what data is wanted**. The database engine determines how to retrieve it.

---

# 22. Frameworks

A framework builds on a language and runtime to provide reusable application structure.

```text
LANGUAGE
    ↓
RUNTIME
    ↓
LIBRARIES
    ↓
FRAMEWORK
    ↓
APPLICATION
```

| Language                | Example Framework / Ecosystem |
| ----------------------- | ----------------------------- |
| C#                      | .NET / ASP.NET Core           |
| Java                    | Spring                        |
| JavaScript / TypeScript | React / Angular / Node.js     |
| Python                  | Django / Flask                |
| C++                     | Qt                            |

A **language** defines how code is written.

A **framework** helps determine how an application is built.

---

# 23. Parser Generators

Parser generators create parsers from grammar definitions.

| Tool  | Primary Purpose                  |
| ----- | -------------------------------- |
| Lex   | Generate lexical analyzers       |
| Yacc  | Generate parsers                 |
| Flex  | Lex-compatible lexer generator   |
| Bison | Yacc-compatible parser generator |
| Lemon | Parser generator                 |

Typical relationship:

```text
SOURCE
  ↓
LEXER
  ↓
TOKENS
  ↓
PARSER
  ↓
AST
```

---

# 24. Lemon Parser Generator

Lemon describes grammar rules that can be converted into a parser.

Example:

```text
%left PLUS MINUS.
%left DIVIDE TIMES.

expr(A) ::= expr(B) PLUS expr(C).
expr(A) ::= expr(B) MINUS expr(C).
expr(A) ::= expr(B) TIMES expr(C).
expr(A) ::= expr(B) DIVIDE expr(C).
expr(A) ::= INTEGER(B).
```

The grammar defines relationships such as:

```text
expr → expr PLUS expr
expr → expr MINUS expr
expr → INTEGER
```

Parser generators are useful for:

* programming languages
* configuration languages
* query languages
* domain-specific languages
* file formats

---

# 25. Compilers and Toolchains

A **toolchain** is the collection of tools used to build software.

| Tool            | Responsibility           |
| --------------- | ------------------------ |
| Editor / IDE    | Create and manage source |
| Lexer           | Create tokens            |
| Parser          | Build program structure  |
| Compiler        | Translate code           |
| Assembler       | Create object code       |
| Linker          | Combine code/libraries   |
| Runtime         | Execute/support program  |
| Debugger        | Inspect execution        |
| Profiler        | Measure execution        |
| Build system    | Coordinate builds        |
| Package manager | Manage dependencies      |

### Build Coordinator

```text
SOURCE FILES
     │
     ↓
BUILD SYSTEM
     │
 ┌───┼────┐
 ↓   ↓    ↓
Compile Link Resources
 └───┼────┘
     ↓
  APPLICATION
```

Examples:

| Tool    | Role                           |
| ------- | ------------------------------ |
| MSBuild | Build system                   |
| LLVM    | Compiler infrastructure        |
| CMake   | Build configuration/generation |
| Make    | Build automation               |
| Ninja   | Build system                   |

---

# 26. Debug and Release

Build configurations commonly include:

| Debug                  | Release             |
| ---------------------- | ------------------- |
| Development            | Production          |
| Debug information      | Optimized output    |
| Easier troubleshooting | Performance-focused |
| More diagnostics       | Fewer diagnostics   |

Exact behavior depends on the language and build system.

---

# 27. Language Comparison

| Language   | Execution        | Typing         | Memory         | Concurrency          |
| ---------- | ---------------- | -------------- | -------------- | -------------------- |
| Assembly   | Native           | Explicit       | Manual         | OS/platform          |
| C          | Native           | Static         | Manual         | OS/platform          |
| C++        | Native           | Static         | Manual / RAII  | OS/platform          |
| Rust       | Native           | Static         | Ownership      | Threads / async      |
| C#         | .NET / JIT / AOT | Static         | GC             | Threads / async      |
| Java       | JVM / JIT / AOT  | Static         | GC             | Threads / async      |
| JavaScript | Engine / JIT     | Dynamic        | GC             | Event loop / workers |
| Python     | VM / interpreter | Dynamic        | Managed        | Threads / async      |
| SQL        | Database engine  | Engine-defined | Engine-managed | Engine-managed       |

---

# 28. Putting It All Together

```text
                  SOURCE CODE
                       │
                       ↓
                    LEXER
                       │
                       ↓
                    TOKENS
                       │
                       ↓
                    PARSER
                       │
                       ↓
                     AST
                       │
                       ↓
              SEMANTIC ANALYSIS
                       │
                       ↓
             COMPILER / INTERPRETER
                       │
                 ┌─────┴─────┐
                 ↓           ↓
             BYTECODE      NATIVE
                 │           │
                 ↓           ↓
               RUNTIME      CPU
                 │
                 └─────┬─────┘
                       ↓
                    PROGRAM
```

The three documents now form a progression:

| Document                | Primary Question                             |
| ----------------------- | -------------------------------------------- |
| **Data Representation** | How is information represented?              |
| **Data Structures**     | How is information organized?                |
| **Languages**           | How do we express operations on information? |

And the complete progression becomes:

```text
REPRESENTATION
      ↓
STRUCTURE
      ↓
LANGUAGE
      ↓
COMPILER
      ↓
RUNTIME
      ↓
EXECUTION
```

---

# Glossary

| Term                  | Definition                                                 |
| --------------------- | ---------------------------------------------------------- |
| **Language**          | Rules for expressing computation or structured information |
| **Token**             | Individual lexical unit                                    |
| **Lexer**             | Converts source text into tokens                           |
| **Parser**            | Determines grammatical structure                           |
| **AST**               | Tree representation of source structure                    |
| **Grammar**           | Rules defining valid structures                            |
| **Semantic Analysis** | Determines whether code is meaningful                      |
| **Keyword**           | Reserved language word                                     |
| **Identifier**        | Programmer-defined name                                    |
| **Escaping**          | Representation of special characters                       |
| **Macro**             | Source-level transformation                                |
| **Interpolation**     | Inserting evaluated values into strings                    |
| **Compiler**          | Translates source into another executable representation   |
| **Interpreter**       | Executes source or intermediate instructions               |
| **Runtime**           | Environment supporting program execution                   |
| **JIT**               | Just-In-Time compilation                                   |
| **AOT**               | Ahead-Of-Time compilation                                  |
| **Framework**         | Reusable application structure and services                |
| **Static Typing**     | Primarily compile-time type checking                       |
| **Dynamic Typing**    | Primarily runtime type checking                            |
| **Process**           | Running program and its resources                          |
| **Thread**            | Execution path within a process                            |
| **Concurrency**       | Multiple tasks making progress                             |
| **Parallelism**       | Multiple tasks executing simultaneously                    |
| **Event Loop**        | Processes events and scheduled work                        |
| **Toolchain**         | Tools used to build software                               |
| **Linker**            | Combines object files and libraries                        |
| **Debugger**          | Tool for inspecting program execution                      |
| **Profiler**          | Tool for measuring program behavior                        |
| **Lex**               | Lexer generator                                            |
| **Yacc**              | Parser generator                                           |
| **Lemon**             | Parser generator                                           |
| **MSBuild**           | Microsoft build system                                     |
| **LLVM**              | Compiler infrastructure                                    |
| **LTS**               | Long-Term Support release                                  |

# Final Takeaway

> **A language defines how we express computation. The compiler and runtime determine how that expression becomes executable behavior.**

```text
DATA
 ↓
DATA STRUCTURE
 ↓
LANGUAGE
 ↓
TOKENS
 ↓
AST
 ↓
COMPILED / INTERPRETED
 ↓
RUNTIME
 ↓
CPU
```

Each layer adds another level of abstraction while ultimately connecting back to the same underlying data and computer hardware.
