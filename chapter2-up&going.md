## Into JS

### Value & Type
- built-in types: `number`, `string`, `boolean`, `undefinded` and `null`, `object`, `symbol` and subtype: `array`, `function`
- `typeof` operator to exam the value type, return one of 6(7 for ES6) string values.
- `typeof null` returns "object", it is a bug.
- `a = undefined` `typeof` return undefined.
#### Objects
- most useful value type in JS
- Properties can either be accessed with dot notation (i.e., obj.a) or bracket notation (i.e., obj["a"])
##### Array
- arrays are special objects, they can also have properties, like `length` property.
##### Function
- bulid-in type methods are methods on its prototype
- like `toUpperCase` for String object, `toFixed` for Number object and etc
##### Comparing values
- There are two types of value comparison: equality and inequality
###### Coercion
- explicit 

```javascript
var a = "42";
var b = Number( a );
a;				// "42"
b;				// 42 -- the number!
```
- implicit
```JavaScript
var a = "42";
var b = a * 1;	// "42" implicitly coerced to 42 here
a;				// "42"
b;				// 42 -- the number
```

###### Truthy and Falsy
- Falsy value:
  -  `''`(empty string)
  -  `0` `-0` `NaN`(invalid `number`)
  -  `undefined` `null`
  -  `false`
- Truty value:
  - `true`
  - `1`
  - `hello world`
  - `[ ]`
  - `{ }`
  - `function foo(){..}`
##### Equality
- loose-equality comparasion: `==` `!=` allow coercion
```JavaScript
 var a = 42;
 var b = '42';
 a == b;    // b coercion to 42;
 ```

- strict-equality comparasion`===` `!=` not allow coercion
- non-primitve type: object( array and function) both `==` and `===` comparisons will simply check whether the references match, not anything about the underlying values.
```JavaScript
var a = [1,2,3];
var b = [1,2,3];
var c = '1,2,3';
a == c; // true
b == c; // true
a == b; // false
```
##### Ineqaulity
- `>` `<` `>=` `<=`
- for string compare using alphabetic rules ` 'apple' > 'bear' //true`
```JavaScript
      var a = 42;
      var b = '41';
      var c = '43';
      a > b; // true '41' coerce to 41;
      c > a; // true
      var a ='foo';
      var b = 42;
      a > b;  //false;
      a < b; // false;
      a == b; // false;
 ```
 - explain: a coerce to invalid number:`NaN` `NaN` is neither greater-than nor less-than any other value
 
#### Variables
- variable names must be valid identifiers which are start with `a-z` `A-Z` `$` `_`
- reversed words: certain words cannot be used as variables, but are OK as property names. Include the JS keywords (`for`, `in`, `if`, etc.) as well as `null`, `true`, and `false`.
##### Hoisting
- when `var` declaration conceptually 'move' to the top of its enclosing scope.
- It's more common and accepted to use hoisted function declarations
##### Nesting
- variable when declared, it available anywhere in that scope, as well as lower/inner scopes  
- Always declare a valuable. 
If you try to access a valuable's value in a scope where it's not available, you will be thrown `ReferenceError`. 
If you try to set a valuable that haven't been declared, you will end up create a globle valuable or get error
- declare a valuable at function scope, ES6 use `let` create indivadual `{}` block valuable

#### Conditionals
```javascript
if(){
           // do something
     }
else if(){
          // do something
     }
else{   
          // fallback to here
     }

swith(){
   case ..:
       // do something
   break;
   case ..:
        // do another thing
   default:
        // fallback to here
      }
```  
- conditional operator or ternary operator
 `? :`
 `var a = (b > 1) ? 'hello' : 'world';`
#### Strict Mode
  - ES5 add a "strict mode" to language
  - one key improvement is disallowing implicit auto-globale valuable declarasion from ommitting the `var`
#### Function as values
- function declaration:
```JavaScript
 function foo(){
          ...
  }
 ```
- In this case `foo` is valuable refer `function`, `function` itself is value
- we also can assign function to a valuable
```javascript
 var foo = function(){
          ...
         }
  var b = function bar(){
          ...
         }
 ```
- the second function expression is named `bar`, also as a reference to it is assigned to valuable b
#### Immidiately Invoked Function Expressions(IIFEs)
`(function IIFE(){..})()`
- Because an IIFE is just a function, and functions create variable scope, using an IIFE in this fashion is often used to declare variables that won't affect the surrounding code outside the IIFE:
#### Closure
- use inner function to 'remember' and access function's scope( it's valuable), even once the function has finished running
```javascript
function makeAdder(x){
    function add(y){
        return x + y;
        };
    return add;
}

var plusOne = makeAdder(1);     // call makeAdder(1), get back a reference to its inner add(..), and remember x as 1, we call this function reference plusOne(..)
var plusTen = makeAdder(10);    // when call makeAdder(10), get back another reference to its inner add(..), and remember x as 10, call this function reference plusTen(..)
plusOne(2);            // return 3 it add 2(inner y) to 1 (remember by x), and get 3
plusTen(3);            // return 13
```
##### Modules
- closure used most in module pattern. 
Modules let you define private implementation details (variables, functions) that are hidden from the outside world, as well as a public API that is accessible from the outside.

#### This Identifier
- If a function has a `this` reference in it, that `this` usually points to an `object`, does not refer to the function itself

#### Prototypes
- The internal prototype reference *linkage* from one object to its fallback happens at the time the object is created.
the simplest way to illustrate it is with a built-in utility called Object.create(..)


















