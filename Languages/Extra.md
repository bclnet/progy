## FRAMEWORKS

**Abstract syntax tree** - an abstract syntax tree (AST), or just syntax tree, is a tree representation of the abstract syntactic structure of source code written in a programming language. Each node of the tree denotes a construct occurring in the source code.

**Lex & Yacc**

**Lemon Parser Generator**
```
%token_type {int}

%left PLUS MINUS.
%left DIVIDE TIMES.
   
%include {
#include <iostream>
#include "example1.h"
}
   
%syntax_error {
  std::cout << "Syntax error!" << std::endl;
}
   
program ::= expr(A). { std::cout << "Result=" << A << std::endl; }  
   
expr(A) ::= expr(B) MINUS  expr(C).  { A = B - C; }  
expr(A) ::= expr(B) PLUS   expr(C).  { A = B + C; }  
expr(A) ::= expr(B) TIMES  expr(C).  { A = B * C; }  
expr(A) ::= expr(B) DIVIDE expr(C).  { 
    if (C != 0) { A = B / C; }
    else { std::cout << "divide by zero" << std::endl; }
}

expr(A) ::= INTEGER(B). { A = B; }
```
[Tutorial](http://souptonuts.sourceforge.net/readme_lemon_tutorial.html)



## COMPILERS ##

Tool chains

Coordinators: MSBUILD, LLVM