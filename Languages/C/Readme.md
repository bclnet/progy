# C Symantics



### ARRAY ###
- Player1 int, Player2 int, Player3 int -> Player int[3]
- Player + 3 * sizeof(int)

```
char Name[100]=string
```

### STRUCT ###

- Players int[12], Wins int[12], Pizzas bool[12]

```
struct Month {
   Players int,
   Wins int,
   Pizza bool,
};
```

Months Month[12]

Month.Players = 100

sizeof(Month)=9


array[] vs array [][]
x+y*pitch
graphic example


union {

}


### POINTERS ###

* dereference
& address of
-> dereference structure member 


char *Name - pointer to an array of characters (i.e., string in C)
 
Name[10] -> *(name +10* sizeof(char))

passby ref vs/ passby value



### C Engine ###

Keywords vs. Symbols:

global (image) / local (stack) variables

int a;

void foo() {
   int b;
}

image: [a] code code code
stack: [IP], [b];

return through eax
int foo() {
  return 1;
}

paramaters though stack
void foo(int a, int b) {
}
foo(1, 2);

stack: [IP], 1, 2

preamble / postable
mov ebp, esp
add esp, (size needed)
CODE
sub esp, (size needed)
ret



CODECODE
HEAP
STACK




### C SYMATICS ###
* commenting with // line or /* */ block
* whitespace does not matter
* every statement ends in ;
* single pass compiler (dumb!)
* linking for multiple source files
* has pre-processor
  - #include
  - #define
  - #ifndef

