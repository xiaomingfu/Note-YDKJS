### Types
#### Built-in Types
- `null`
- `undefined`
- `boolean`
- `number`
- `string`
- `object`
- `symbol`   -- ES6
*Note*: all of these types expcept `object` are 'primitives'
The `typeof` operator inspects the type of the given value, and return
one of seven string values
```javascript
typeof undefined === 'undefined'; //true
typeof true === 'boolean'; //true
typeof 42 === 'number'; // ture
typeof '42' === 'string'; // true
typeof {life : 42} === 'object'; // true
typeof Symbol() === 'symbol'; // true
typeof function(){/*...*/} === 'function'; // true
```
*special*-- `typeof null === 'object'; // true` this is buggy for nearly two decades
test:
```javascript
var a = null;
(!a && typeof a === 'object'); //ture
```
`function` is a 'subtype' of object, is referred to as a 'callable object'--
an object that has an internal `[[Call]]` property. function as object also has
properties.
```javascript
function foo(a,b){
    /*..*/
 }
 foo.length; //2
 ```
 `array` is also subtype of object.
#### Values as Types
 *In JavaScript variable don't have types -- values have types*
 ```javascript
 var a = 42;
 typeof a;  //"number"
 
 a = true;
 typeof a; // "boolean"
 ```
##### `undefined` vs "undeclared"
 "undefined" is not same as "undeclared"
 ```javascript
 var a;
 a; //"undefined"
 b: // ReferenceError: b is not defined
 ```
 `ReferenceError: b is not defined` actually means b is not declared
 ```javascript
 var a;
 typeof a; //"undefined"
 typeof b; //"undefined"
 ```
 This is also a special behavior associated with `typeof`, it return `"undefined"`
 even for "undeclared" variables.
 *`typeof` Undeclared*
 this safety guard is useful feature when dealing with JavaScript in the browser,
you have to take care in how you check for the global DEBUG variable in the rest of your application code, so that you don't throw a `ReferenceError`. 
 ```javascript
 if(DEBUG){
    console.log("Debugging is starting");
  }                                   // this would throw an ReferenceError
  if(typeof DEBUG !== "undefined"){
      console.log("Debugging is starting");
  }
  ```
If you are doing a feature check for a built-in API, you may also find it helpful to check without throwing an error:
  ```javascript
  if(typeof atob === "undefined"){
      atob = function(){/*..*/};
   }
   ```
a utility function that you want others to copy-and-paste into their programs or modules, in which you want to check to see if the including program has defined a certain variable (so that you can use it) or not:
```javascript
(function(){
  function FeatureXYZ(){ */...my XYZ feature ..*/}
  
  // include 'doSomethingCool(..)'
  function doSomethingCool(){
      var helper = 
          (typeof FeatureXYZ ! == "undefined") ? 
          FeatureXYZ :
          function(){ /*..default feature*/}
   
      var val = helper();
      //
   }
   
   doSomethingCool();
 })();
 ```
Other developers would prefer a design pattern called "dependency injection,"
```javascript
function doSomethingCool(FeatureXYZ){
    var helper = FeatureXYZ ||
          function(){ /*..default feature ..*/};
     var val = helper();
     ..
 }
 
 
 
 
 
 
 
 
 
 
 
