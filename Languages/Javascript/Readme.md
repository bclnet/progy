# Javascript

Javascript is a type-less, proto-typical language that uses the {} scope operator, it is similar to C.


## C like semantics
* commenting with // line or /* */ block
* whitespace does not matter
* every statement ends in ;
- `var {symbol}`, `let {symbol}`, `const {symbol}` - defines a new variable 
- literal strings use `'` or `"` inter-changeably, `\`` can be used for string-interpolation.
- literals are scalar, arrays or objects: `{scaler}` defines a scaler, `[]` defines an array, `{}` defines an object
- everything is an object, all object can have additional fields or methods added to them
- runs single threaded
- has global or local variables

*local and function variables*
```javascript
var a;

function foo() {
   var b;
}
```

*function returning a value*
```javascript
function foo() {
  return 1;
}
```

*function with parameters*
```javascript
function foo(a, b) {
}
foo(1, 2);
```