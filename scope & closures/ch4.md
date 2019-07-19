#### Hoisting
##### The Compiler Strikes
`var a = 2;` JavaScript Engine sees `var a` as compiler-phase task, and `a = 2` as execution-phase task. 
The Engine will compile JavaScript code before it interprets it. So both variables and functions, are declarated first before any 
part of the code is executed.
```javascript
console.log(a);
var a = 3;    //undefined for `var a;` come before `console.log(a);`
```
"Hoising": variable and function declarations are "moved" from where they apprear to the top of the code. Declarations themselves are hoisted, but assignments, even assignments of function expression are not hoisted.
##### Functions First
Function are hoisted first, and then variables. While multiple `var` declarations are effectively ignored, subssequent function declarations do override previous ones. This is a bad idea to have duplicate definitions in the same scope.

