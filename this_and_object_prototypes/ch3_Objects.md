#### Objects
##### Syntax
two forms: literal form and the constructed form. Always use the literal syntax form.
```javascript
var myObj = {
    key: value,
    // ...
};
```
##### Type
7 primary types
- `string`
- `number`
- `null`
- `undefined`
- `boolean`
These are simple primitives. `null` is referred to as an object type, but this misconception. `null` is its own primitive type.
- `object`
- `symbol` ES6
There are two special sub-types, are refered to as complex primitives.
- `function`s are basically just normal objects
- `array`s are a form of objects with exta behavior.
###### Bulit-in Objects
- `String`
- `Number`
- `Boolean`
- `Object`
- `Function`
- `Array`
- `Date`
- `Error`
- `RegExp`
These built-ins are actually built-in functions. Each of these built-ins can be used as a constructor, with the result being a newly constructed object.
```javascript
var strPrimitive = "I am a string";
typeof strPrimitve;                    // "string"
strPrimitive instanceof Stirng;       //false
console.log(strPrimitive.length);    // 13
```
The primitvie value is not an object. JavaScript automactically coerces a `string` primitve to a `String` object when necessary. 
It is strongly preferred to use the literal form for a value.

`null` and `undefined` has no object wrapper form. `Date` values can only be created with their constructed object form.

`Object`s, `Array`s, `Function`s and `RegExp`s are all objects regardless of whether the literal or constructed form is used.
Only use the constructed form if you need the extra options.

`Error` object created automatically when exception are thrown.

##### Contents
The contents of an object are properties, which act as pointers to where the values are stored.

There are two syntaxes to access the value of the object property.
`.` syntax is referred to as "property" access, whereas `[".."]` syntax is referred to as "key" access.

The main difference between the two syntaxes is that the `.` operator requires an `Indentifier` compatible property name after it.

whereas the `[".."]` syntax can take basically any UTF-8/unicode compatible string as the name for the property. for instance, you
would like to use the `["Super-Fun!"]` access syntax.
Also, `[".."]` syntax uses a string's **value** to specify the location, the program can build up the value of the string.

In objects, property names are always strings. If other value besides a `string` (primitive) as the property, it will first be converted to a string.

###### Computed Property Names
ES6 adds computed property names surrounded by a `[]` pair, in the key-name position of an object-literal declaration.

###### Property vs. Method
Every time you access a property on an object, that is a **property access**. If you happen to get a function from that proerty access, it's not magically a "method" at that point(belong to the object). Neither implies anything about the function being special or "owned" by any other object. 

##### Arrays
Arrays assume numeric idexing, which means that values are stored in locations, called indices.
Arrays as objects can add properties onto it. Notice that adding named properties does not change the reported `length` of the array. But this is bad idea. Use objects to store key/value pairs, and arrays to store vaules at numeric indices.

##### Duplicating Objects ??
ES6 use `Object.assign(..)` for a shallow copy.

##### Property Descriptors
ES5 use `getOwnProertyDescriptor` to get property characteristics, and use `Object.defineProperty(..)` to add a new property or modify an existing one.

###### Writable
`writable` change the ability to modify the value of a property
`strict mode` will get `TypeError` when a property descriptor is `writable : false`, but you try to modify the value later.

###### Configurable
Change `configurable` to `false` is a **one-way action, and cannot be undone!**. `configurable:false` prevents the ability to use the `delete` operator.

###### Enumerable
`enumerable:false` keep it from showing up in such enumerations, even though it's still completely accessible.

###### Immutability

 **Object Constant**
By combining `writable: false` and `configurable:false`, can create constant as an object property.

**Prevent Extensions**
`Object.preventExtensions(..)` prevent an object from having new properties added to it.

**Seal**
`Object.seal(..)` which means it takes an existing object and essentially calls `Object.preventExtensions(..)` and marks all its exitsing properties as `configurable:false`

**Freeze**
`Object.freeze(..)` which means it takes an existing object and essentially calls `Object.seal(..)`, and marks all "data accessor" properties as `writable:false`. It is the highest level of immutability. 

###### `[[Get]]`
There is internally defined `[[Get]]` operation for getting a value from a propery. If it cannot through any means come up with a value for the requested property, it returns `undefined`

###### `[[Put]]`
When invoking `[[Put]]`, if the property is present, the `[[Put]]` check:
 1. Is the property an accessor descriptor (see "Getters & Setters" section below)? If so, call the setter, if any.
 2. Is the property a data descriptor with writable of false? If so, silently fail in non-strict mode, or throw TypeError in strict mode.
 3. Otherwise, set the value to the existing property as normal.

###### Getter & Setters ???
ES5 introduced Getter and Setters to override part of `[[Put]]` and `[[Get]]` operations, on a per-property level. 
Getters are properties which actually call a hidden function to retrieve a value. Setters are properties which call a hidden function to set a value.
```javascript
var myObject = {
  get a(){ return this._a_;},
  set a(val){ this._a_ = val * 2;}
};
myObject.a = 2;
myObject.a;     //4
```

###### Existence
`in` operator will check to see if the property is in the object, or exists at any higher level of the `[[Prototype]]` chain. 
`hasOwnProperty(..)` checks to see if only `myObject` has the property or not.

###### Enumeration
`propertyIsEnumerable(..)` tests whether the given property name exists directly on the object and `enumerable:true`

`Object.keys(..)` returns an array of all enumerable properties.

`Object.getOwnPropertyNames` returns an array of all properties.

###### Iteration
`for..in` loop iterates over the list of enumerable properties. With numerically-indexed arrays, iterating with `for`.

ES5 has `forEach(..)`, `every(..)`, and `some(..)` for arrays to iterate value.

ES6 adds `for..of` loop syntax for iterating over the values instead of the array indices




































