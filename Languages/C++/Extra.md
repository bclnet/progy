

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




### C SYMATICS
