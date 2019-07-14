#### Natives
most commonly used matives(bulid-in function):
- `String()`
- `Number()`
- `Boolean()`
- `Array()`
- `Object()`
- `Function()`
- `RegExp()`
- `Date()`
- `Error()`
- `Symbo()` --ES6
```javascript
var a = new String( "abc" );

typeof a; // "object" ... not "String"

a instanceof String; // true

Object.prototype.toString.call( a ); // "[object String]"
```
`new String("abc")` creates a string wrapper **object** around `"abc"`

##### Internal `[[Class]]`
use `Object.prototype.toString()` method to call against an internal `[[Class]]` property
In most cases, this internal `[[Class]]` value corresponds to the built-in native constructor that's related to the value
but except `null` and `undefined`
for primitve values:
```javascript
Object.prototype.toString.call( null );			// "[object Null]"
Object.prototype.toString.call( undefined );	// "[object Undefined]"
```
And for the simple primitives are atuomatically boxed by their repective object wrappers
```javascript
Object.prototype.toString.call( "abc" );	// "[object String]"
Object.prototype.toString.call( 42 );		// "[object Number]"
Object.prototype.toString.call( true );		// "[object Boolean]"
```
##### Boxing Wrappers
In general, JS will automatically box the primitive value to fulfill properties or methods accesses
###### Object Wrapper Gotchas
```javascript
var a = new Boolean(false);
if (!a){
      console.log("Oops");    //never runs
      }
```
a as object is alway "truthy". If you want to manually box a primitve value, you can use the `Object(..)` function
##### Unboxing
Use `valueOf()` method to get the underlying primitive value out.
##### Natives as Constructors
It is almost universally preferred that you use the literal form for creating `array` `object` `function` values
###### `Array(..)`
```javascript
var a = Array(3);
a.length; // 3
a;  /(3)[empty * 3]
```
If there is only one `number` argument is passed in `Array` constructor, it's taken as a length. This needs avoid
###### `Object()`, `Function()`, `RegExp()`
The `Object()/Function()/RegExp()` constructors are also general optional
`RegExp()` has some reasonable utility: to dynamically define the pattern for a  regular expression
###### `Date()` and `Error()`
To create a date object value, you must use `new Date()`, an even easier way is to just call the static helper function `Date.now()`.
If you call `Date()` without `new`, you'll get back a string representation of the date/time at that momnet.
The `Error()` constructor behaves the same with the `new` keyword present or omitted. You would typically use an error object with the `throw` operator.
###### `Symbol()`
Use `Symbol()` native to define your own symbols, you are not allowed to use `new` with it.
###### Native prototypes
by doctumentation convention, for all the other `.prototype`s can be shortened to `#`, like `String.prototype.XYZ` is shortened to `String#XYZ`
- `String#indexOf()`
- `String#charAt()`
- `String#substr()`
- `String#toUpperCase()` and `String#toLowerCase()`
- `String#trim()`
None of the methods modify the string in place. Modifications create a new value from the exiting value.
###### Prototypes As Defaults
`Function.prototype` being an empty function, `RegExp.prototype` beging an "empty" regex and `Array.prototype` being an empty array, can make them "default" values



















