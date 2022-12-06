# C, C++, C# Lexicon
https://www.w3schools.com/cs/index.php

## Syntax
* commenting with `//` line or `/*...*/` block
* whitespace does not matter
* every statement ends in `;`
* multiple files combine along with libraries for the final compiled file

## Literal
```c#
char literal = 's';
string literal = "string";
int literal = 1; uint literal = 1U;
long literal = 1L; ulong literal = 1UL;
float literal = 1F;
double literal = 1.1; double literal = 1D;
decimal literal = 1M;
```

## Namespace & Scope

* keyword `namespace` defines "folders" to prevent name collisions.
* keyword `using` defines includes the symbols in the namespace.
* { } defines scope
* `C, C++` only; uses a single pass compiler, and the pre-processor to combine multiple files into a single file.
  - #include
  - #define
  - #ifndef

```c#
// example usings
using System;
using System.Collections;

// example namespace
namespace MyNamespace.SubNamespace
{
   // scope by itself
   {
      int myvar = 0;
   }

   // example if statement with scope
   if (true) {
      ...
   }
}
```

## Variable

[`modifiers`] `type` `symbol` [= `initializer`];
```c#
int symbol;       // simple variable
int symbol2 = 1;  // variable with initialization
var symbol3 = 1;  // variable with automatic type

// variable assigment
symbol = 1;
symbol = symbol2;
symbol = symbol + 1;
symbol = EnumName.Value;

// variable assigment short-hand
symbol += 1; symbol -= 1; // arithmetic
symbol++; symbol--; // increment/decrement after evaluation
++symbol; --symbol; // increment/decrement before evaluation
symbol *= 1; symbol /= 1; symbol %= 1; // arithmetic
symbol |= 1; symbol &= 1; // bit assignment

// evaluation
// || short circuit or leaves statement when condition fails
// && short circuit and leaves statement when condition fails
while (x == 1 || x != 1) { ... } // equal/not-equal comparison
while (x > 1 || x < 1 || 1 >= 1 || 1 <= 1) { ... } // greater/less comparison
```

## Conditional Branching

```c#
// if/else statement
if (condition) { ... }
else if (condition) { ... }
else { ... }

// switch statement
switch (expression) {
   case x: break;
   case y: break;
   default: break;
}

// ternary operator
variable = condition ? expressionTrue :  expressionFalse;

// while loop
while (condition) { ... }

// do/while loop
do { ... }
while (condition);

// for loop
for (statement 1; statement 2; statement 3) { ... }

// foreach loop
foreach (type variableName in arrayName) { ... }

// break
for (var i = 0; i < 10; i++) {
   if (i == 4) break;
   Console.WriteLine(i);
}

// continue
for (var i = 0; i < 10; i++) {
   if (i == 4) continue;
   Console.WriteLine(i);
}
```

## Functions

[`modifiers`] void `symbol`([`type` symbol], `...`) { `body` }
```c#
// function with zero parameters
void symbol() { ... }
symbol();

// function with one parameter
void symbol(int abc) { ... }
symbol(1);

// function with one parameter with a default value
void symbol(int abc = 0) { ... }
symbol();
symbol(1);
```

[`modifiers`] `returntype` `symbol`([`type` symbol], `...`) { `body` }
```c#
// function with zero parameters
int symbol() {
   ...
   return 0;
}
int result = symbol();

// function with one parameter
int symbol(int abc) {
   ...
   return 0;
}
int result = symbol(1);

// function with one parameter with a default value
int symbol(int abc = 0) {
   ...
   return 0;
}
int result1 = symbol();
int result2 = symbol(1);
```

## Enums
[`modifiers`] enum `symbol` [: `type`] { `body` }
```c#
enum symbol : int { One, Two, Three }

// simple variable
symbol example = symbol.One;

// variable with automatic type
var example = symbol.One;
```

## Struct / Class
[`modifiers`] struct/class `symbol` { `body` }
```c#
struct symbol {
   int first;
   int second;
}

class symbol2 {
   int first;
   int second;
}

// simple variable
symbol example = new symbol();
example.first = 1;
example.second = 1;

// variable initialization
symbol example = new symbol {
   first = 1,
   second = 1,
};

// variable with automatic type
var example = new symbol();
```

## Generic
class `symbol`<`generic`[, `generic`, `...`]>(`...`);
```c#
class List<T> {
   void Add(T value) { ... }
}

// simple variable
List<int> symbol = new List<int>();
symbol.Add(1);
symbol.Add(2);
```

## Array
[`modifiers`] `type`[] `symbol` [= `initializer`];
```c#
int[] symbol;

// simple variable
int[] symbol = new int[2];
symbol[0] = 1;
symbol[1] = 2;

// variable initialization
int[] symbol = new int[] { 1, 2 };

// variable with automatic type
var symbol = new [] { 1, 2 };
```

Example hold Home and Away score and if we won
```c#
// example with 4 items
int HomeScore1; int HomeScore2; int HomeScore3; int HomeScore4;
int AwayScore1; int AwayScore2; int AwayScore3; int AwayScore4;
bool Win1; bool Win2; bool Win3; bool Win4;

// example with array
int[] HomeScore = new int[4];
int[] AwayScore = new int[4];
bool[] Win = new bool[4];

// example with struct and array
struct Game {
   int HomeScore;
   int AwayScore;
   bool Win;
}
Game[] Games = new Game[12];
// game 1
Games[0].HomeScore = 10;
Games[0].AwayScore = 5;
Games[0].Win = true;
// game 2
Games[1].HomeScore = 6;
Games[1].AwayScore = 9;
Games[1].Win = false;
```

## List&lt;`type`&gt;
[`modifiers`] List<`type`> `symbol` [= `initializer`];
```c#
List<int> symbol;

// simple variable
List<int> symbol = new List<int>();
symbol.Add(1);
symbol.Add(2);

// variable initialization
List<int> symbol = new List<int> { 1, 2 };

// variable with automatic type
var symbol = new List<int> { 1, 2 };
```

## Symbol Modifiers
```c#
// access modifier
public int variable;
private int variable;
protected int variable;
internal int variable;

// static vs instance
public static int variable;

// example class
public class MyClass {
   public int first;
   public int second;
}

// example function
public void MyFunction() { ... }
```

## Class Method and `this`
```c#
public class MyClass {
   public int first;
   public int second;
   public static int third;

   // this holds the current instance (is optional)
   public void Foo() {
      first = 1;
      this.second = 2;
      third = 3; // updates static "shared" field
   }

   // this does not exist, can only access the static value
   public static void Bar() {
      third = 3;
   }
}

// access instance members
MyClass example = new MyClass();
example.first = 1;
example.second = 2;
/*
example.third = 3;     // would error
*/
example.Foo();

// access static members
MyClass.third = 3;
MyClass.Bar();
```


## Class Properties
```c#
public class MyClass {
   public int _value;
   
   // methods only
   public int getValue() { return _value; }
   public void setValue(int value) { _value = value; }

   // get/set property
   public int value {
      get { return _value; }
      set { _value = value; }
   }
  
  // automaticly backed properties
   public int value { get; set; }
}

MyClass example = new MyClass();
// methods only
example.setValue(1);
example.getValue().Dump();
// get/set property
example.value = 1;
example.value.Dump();
```

## Class Inheritance
```c#
public class Vehicle {
   public string Model;
   public string Color;
}

public class Car : Vehicle {
   public string Type;
}

public class Truck : Vehicle {
   public int MaxCargo;
}

public class Bus : Vehicle {
   public int MaxPassengers;
}

void Print(Vehicle vehicle) { ... }

// example bus
var exampleBus = new Bus {
   Model = "Micro Bird",
   Color = "Yellow",
   MaxPassengers = 65,
}
Print(exampleBus);

// example truck
var exampleTruck = new Truck {
   Model = "Pickup",
   Color = "Black",
   MaxCargo = 1000,
}
Print(exampleTruck);
```

## Class Polymorphism 
```c#
public class Animal {
   public string Name;
   public virtual void MakeSound() {
      Console.Write("Animal is making a sound");   
   }
}

public class Horse : Animal {
   public override void MakeSound() {
      Console.Write("Neigh");   
   }
}

public class Cat : Animal {
   public override void MakeSound() {
      Console.Write("Meow");   
   }
}

// example Horse
var horse = new Horse()
horse.MakeSound();

// example Cat
var cat = new Cat()
cat.MakeSound();
```

## Interface
```c#
public interface IMakeSound {
   void MakeSound();
}

public class Horse : IMakeSound {
   public void MakeSound() {
      Console.Write("Neigh");   
   }
}

public class Cat : IMakeSound {
   public void MakeSound() {
      Console.Write("Meow");   
   }
}

// example Horse
var horse = new Horse()
horse.MakeSound();

// example Cat
var cat = new Cat()
cat.MakeSound();
```