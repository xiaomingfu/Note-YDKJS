### Values
#### Arrays
__Warning__:using `delete` on an `array` value will remove that slot but not update the
`length` property
```javascript
var a = [1,"42", [0]];
delete a[0];
a;     //(3) [empty, "42", array[1]]
```
`array` are numerically indexed, and also have `string` keys/properties added to them
which is not good to add `string` keys/properties
##### Array-Likes
DOM query operations return lists of DOM elements are `array`-like
and functions expose the `arguments`(`array`-like) object
One common way to covert an `array`-like value into a true `array` is to borrow
the `slice(..)` utility against the value:
```javascript
function foo() {
	var arr = Array.prototype.slice.call( arguments );
	arr.push( "bam" );
	console.log( arr );
}

foo( "bar", "baz" ); // ["bar","baz","bam"]
```
Also `Array.from(..)` of ES6 can do the same task
#### Strings
Strings is `array`-likes, have some same properties and methods: `length` `indexOf(..)` `concat(..)`
But `string` is immutable, `array` is mutable, 
and many of the `array` methods are not 
actually available for `string`, but can "borrow" non-mutation methods against `string`
such as: `Array.prototype.join.call(..)`, `Array.prototype.map.call(..)`
#### Numbers
the implementation of JavaScript's number is based on the "IEEE 754" standard
##### Numeric Syntax
```javascript
var a = 42.0;
a; // 42 the trailing portion of a decimal value after the ., if 0, is optional, and return with trailing fractional 0 removed

0.42 === .42 // the leading portion of a decimal value, 0 is optional

var a = 5E10;
var b = a * a;
b;  //2.5e+21 default be outputted in exponent form

var a = 42.59;

a.toFixed(0); // "43" specify how many fractional decimal places
a.toPrecision(1); // "4e+1" specifies how many significant digits
```
##### Small Decimal Values
` 0.1 + 0.2 === 0.3  // false`
it is side effect of using binary floating-point nubmers
`Number.EPSILON` is predefined with this tolerance value
##### Safe Integer Ranges
`Number.MAX_VALUE` Max positive number, `-MAX_VALUE` min negative number
`Number.MIN_VALUE` Min positive number close to zero `-MIN_VALUE` max negative number
`Number.MAX_SAFE_INTEGER` is `2^53 - 1`
`Number.MIN_SAFE_INTEGER` is `-2^53 - 1`
##### Testing for Integers
`Number.isInteger(..)`
`Number.isSafeInteger(..)`
##### 32-bit(Signed) Integers










