#### Function vs. Block Scope
##### Scope From Functions
function-based scope encourages that all variables belong to the function, and can be used and reused throughout the entirety
of the function.
###### Hiding in Plain Scope
"Principle of Least Privilege"("Least Authority" or "Least Exposure") - the software design principle is one of the reasons 
motivating this scope-based hiding.
###### Collision Avoidance
```javascript
function foo(){
  function bar(a){
      var i = 3;
      console.log(a + i);
   }
   for (var i = 0; i < 10; i++){
      bar(i * 2);      //i = 3; alway i < 10; infinite loop
    }
 }
 foo();
 ```
 ###### Global "Namespaces"
 libraries will create a signle variable declaration with an unique name in the global scope. This object is used as a "namespace" for that library,
 where all specific exposures of functionality are made as properties of that object(namespace)
 ###### Module Management
 ##### Functions As Scopes
 ```javascript
 var a = 2;
 (function foo(){
    var a = 3;
    console.log(a); // 3
  })();
  cosole.log(a);    // 2
  ```
  This statement is different from `function...`, Instead of declare the function, the function is treated as a function-expression.
  The key difference between a function declaration and a function expression relates to where its name is bound as an identifier.
  `(function foo(){..})` `foo` is found only in the scope where the `..` indicates. It does not pollute the enclosing scope.
  ###### Anonymous vs. Named
  Function expression can be anonymous, but function declarations cannot omit the name.
  The best practice is always name function expressions
  ###### Invoking Function Expressions Immidiately
  This pattern is called IIFE(Immediately Invoked Function Expression)
  `(function (){..})()`-- the `()` makes the function an expression, the second `()` executes the function. 
  The most common form of IIFE is to use an anonymous function expression. another form: `(function (){..}())`
  ##### Blocks As Scopes
  Block-scoping is to declare variables as local as poosible. JavaScript has no facility for block scope on the surface.
  Follow are block scope construct.
   - **`with`** 
   - **`try/catch`**
   - **`let`**
   - **`const`** Any attempt to change that value at a later time results in a error
  ```javascript
  {
    console.log(bar);   //ReferenceError
    let bar = 2;
   }
   ```
   `let` will not hoist to the entir scope of the block. We can create an arbitrary block for `let` to bind to by including a `{..}` pair 
   anywhere a statement is a valid grammar.
   **`let` Loops**
   ```javascript
   for (let i = 0; i < 10; i++){
      console.log(i);
   }
   console.log(i);    //ReferenceError
   ```
   `let` in the for-loop header bind the `i` to the for-loop body, and re-binds it to each iteration of the loop, making sure to re-assign 
   it the value from the end of the previous loop iteration.
   
   
   
   
   
   
   
   
   
   
   
  
  
  
  
  
  
  
  
  
