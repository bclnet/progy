# Languages
Computers do not understand our language and see everything as a stream of numbers. We must build a process to convert human languages to machine languages.


## Tokenize
Tokenization is the process of breaking a stream of numbers into continuous tokens of characters while breaking on whitespace

```psudo
1.234 my name;

BECOMES
number: 1.234
string: my
string: name
end: ;
```

sometimes we want to represent a token with a space retained, use quotes

```psudo
"my name";

BECOMES
string: my name
end: ;
```

## Escaping
adding a special encoding character like " introduces an issue if we want to espace the " and represent the literal " in a token.

```psudo
"my \"name\" was here";
--- becomes ---
string: my "name" was here
string: ;
```

escape characters and encoding sequences are based on the language. usualy a special character for escape, but then you have to escape the escape \ -> \\

c, c++, c#, javascript:
```psudo
\\ = \
\" = quote
"" = quote (.net if not @"")
\n = return
\t = tab
```

javascript:
```
string, single quote or double quote. 'string' or "string"
```

SQL:
```
string, single quote or double quote. 'string' or "string"

encoding: [Symbol]

```

Esc | Character Represented by Sequence
-- | --
\0 | An ASCII NUL (X'00') character
\' | A single quote (') character
\" | A double quote (") character
\b | A backspace character
\n | A newline (linefeed) character
\r | A carriage return character
\t | A tab character
\Z | ASCII 26 (Control+Z); see note following the table
\\ | A backslash (\) character
\% | A % character; see note following the table
\_ | A _ character; see note following the table


## Lexicon

The `Lexicon` is where the compiler, or instruction handler, applies meaning to the stream of tokens recieved based on the syntax of the language.

Based on the language the compiler will understand the syntax or throw a syntax error.

*`SQL`*
```sql
Select MyField
From MyTable
Where MyField = 'MyValue';
```

*`c`, `c++`*
```c
int age = 10;
printf("%d\n", age);
```

*`HTML`*
```html
<a href="value">text</a>
```

*`CSS`*
```css
.small { background: solid black }
```

## High Level Processing

high level languages have added additional features

**Macro expansion** - Macro expansion is always just a textual transform of the input source code. You should be able to see the code after the pre-processor (the part of the compilation that does the macro expansion) is done; this text is what the compiler proper then works on.

*`c`, `c++`*
```
#include <stdio.h>
#define foo bar
#if VALUE
#endif
```

**String interpolation** - string interpolation (or variable interpolation, variable substitution, or variable expansion) is the process of evaluating a string literal containing one or more placeholders, yielding a result in which the placeholders are replaced with their corresponding values.

*`c#`*
```
var age = 3;
var string = $"my {age}";
```

*`javascript`*
```
let age = 3;
let string = `my ${age}`;
```

## Keywords & Symbols

All language have reserved words refered to as keywords. These help direct the language with your intent.

If not a keyword you can define new symbols to represent elements in your code. Symbols sometimes have scope and access level definitions.


## [Language : Assembly](/Assembly/)
Low level ISA

## [Language : C, C++](/C/)
C and C++ share a common root language

* commenting with // line or /* */ block
* whitespace does not matter
* every statement ends in ;
* single pass compiler (dumb!)
* linking for multiple source files
* has pre-processor
  - #include
  - #define
  - #ifndef

## [Language : HTML](/HTML/)
Hyper Text Markup Language (HTML) is a text formating language used by the web.


## [Language : Markdown](/Markdown/)
A simple text formating language


## [Language : SQL Server](/SQL%20Server/)
Structured Query Language (SQL) is a language used to gather information.

---
# Glossary
Name | Description
--- | ---
`escaping` | Escaping (see above)
`macro expansion` | Macro expansion (see above)
`string interpolation` | String interpolation (see above)
`type-safe language` vs `type-less language` | a language that uses defined data types vs a language that uses dynamic data types which can be of any type and structure.
`low-level language` vs `high-level language` | a language that operates closer to metal vs a language operates more virtual
`sequential language` | a list of instructions with jump instructions for flow-control.
`procedural language` | functions containing sequential instructions with calls to other functions for flow-control.
`proto-typical language` | templated functions containing sequential instructions which are copied to new instances, and call other functions for flow-control.
`functional language` | truly function language with strict immutable data types.