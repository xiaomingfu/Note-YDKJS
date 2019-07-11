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
The range is `Math.pow(-2,31)` up to `Math.pow(2, 31)-1`
#### Special Values
##### The Non-value Values
`undefined` type has only one value: `undefined`, `null` type has only one `null` value.
- `null` is an empty value, or had a value and doesn't anymore
- `undefined` is a missing value or hasn't had a value yet
`null` is a special keyword, `undefined` is an identifier
##### Undefined
`undefined` can be treated as a variable, but it is a terrible idea
###### `void` Operator
`void` operator can get `undefined` value
##### Special Numbers
###### The not Number, Number
`NaN` is "invalid number" "bad number". It represents a special kind of error condition within the `number` set
```javascript
var a = 2/"foo";

a == NaN;  //false
a === NaN; //false
```
`NaN` is never equal to itself, so `NaN != NaN`.
We can test for it by `Number.is.NaN(..)` in ES6
###### Infinites
```javascript
var a = 1 / 0;		//Infinity
var b = -1 / 0;		//-Infinity
```
`Infinity / Infinity; // NaN;`
`1 / Infinity; // 0`
`-1 / Infinity; // -0`
###### Zeros
`0` and `-0`
```javascript
var a = 0 / -3;	// -0
var b = 0 * -3;	// -0
```
if you try to stringify a negative zero value, it always be reported as `"0"`, going from `string` to `number` will get `-0`
```javascript
var a = 0/ -3;
a.toString();     //"0"
+ "-0"		// -0
Number("-0");	//-0
```
```javascript
var a = 0;
var b = 0 / -3;
a == b;		//true
-0 === 0;	//true
```
`-0` lies and pretends that it's equal to `0`, so if you want to distinguish a `-0` from `0`, you can use `isNegZero(..)`
##### Special Equality
ES6 give a new utility `Object.is(..)` to test two values for absolute equality, it is mostly for `NaN` and `-0`
#### Value vs.Reference
Primitive values are always assigned by value-copy: `null`, `undefined`, `number`,
`boolean`, and `symbol`.
Compound values -- `object`(including `array`) and `function` always create a cope of the reference on assignment
```javascript
var a = 2;
var b = a;
b++;
a;	//2 initial copy of 2
b;	//3 another copy of the value of a, changing b, in no way changing the value in a
var c = [1,2,3];
var d = c; // d is reference to the shared [1,2,3], c and d both point to [1,2,3]
d.push(4); // modify the actual shared `array` value itself
c; //[1,2,3,4]
d; //[1,2,3,4] both references will reference the newly modified value
```
```javascript
var a = [1,2,3];
var b = a;
b = [4,5,6];
a;	//[1,2,3] references point to the values themselves and not to the variables
b;	//[4,5,6]
```
To pass a compound value(`array`) by value-copy, you need to manually make a copy of it, `slice(..)` with no parameters by default makes an entirely new copy of the `array`
`foo(a.slice());`

To pass a primitive value in a way where its value updates can be seen, kinda like a reference-- you have to wrap the value in another compound value(`object`, `array`, etc) that can be passed by reference-copy.

```javascript
function foo(wrapper){
	wrapper.a = 42;
}
var obj = {
    a : 2,
}
foo(obj);
obj.a;  //42
```
The only control you have over reference vs. value-copy behavior is the type of the value itself, so you must indirectly influence the assignment/passing behavior by which value types you choose to use.






























