# YAML

YAML is a human-readable data-serialization language. It is commonly used for configuration files and in applications where data is being stored or transmitted.

## Basic Syntax

* The file starts with three dashes. These dashes indicate the start of a new YAML document. YAML supports multiple documents, and compliant parsers will recognize each set of dashes as the beginning of a new one.
* Typical YAML element is a key: value pair
* You can enclose strings in single or double-quotes or no quotes at all. YAML recognizes unquoted numerals as integers or floating point.
* Indentation is how YAML denotes nesting. The number of spaces can vary from file to file, but tabs are not allowed.

*example*
```
---
 string: "value"
 floating: 3.14159
 boolean: true
 integer: 3
 list:
   - item1
   - item2
 dictionary:
   key1: item
   key2: 3
   subkey3:
     count: 1
     location: "string"
   key4: two
```
