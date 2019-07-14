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
