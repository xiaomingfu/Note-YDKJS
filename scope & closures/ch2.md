#### Lexical Scope
"scope" as the set of rules that govern how the Engine can look-up a variable by its
**identifier** name and find it.
Two predominant models: **Lexical Scope** and **Dynamic Scope**
##### Lex-time
lexical scope is scope that is defined at lexing time.(based on where variables and blocks
of scope are authored, at write time, and this is (mostly) set in stone by the time the lexer 
processer your code.
```javascript
function foo(a) {

	var b = a * 2;

	function bar(c) {
		console.log( a, b, c );
	}

	bar(b * 3);
}

foo( 2 ); // 2 4 12
```
Think these scopes as bubbles inside of each other
**Bubble 1** global scope, one identifier `foo`
**Bubble 2** `foo` scope, identifiers: `a`, `b`, `bar`
**Bubble 3** `bar` scope, identifier: `c`
##### Look-ups
It starts with the innermost scope bubble(`bar()` function scope) for `a`, `b`, and `c`
and works outward/upward until the fist match, and stops.
**Scope look-up stops once it finds the first match**. (the inner identifier "shadows" 
the outer identifier)
**Note** Global variables are also automatically properties of the global object. 
This technique gives access to a global variable which would otherwise be inaccessible dut 
to it being shadowed.
##### Cheating Lexical
**`eval`**: takes a string as an argument and treats it as code. It modifies lexical scope 
at runtime.
**`with`**: short-hand for making multiple property referneces without repeating the object refernce itself
It creats new lexical scope at runtime.
These mechanisms defeat the Engine's abilty. So do not use them.
