#### Scope Closure
Closure is when a function is able to rememeber and access its lexical scope enven when that function is executing outside its lexical scope.
```javscript
function foo() {
	var a = 2;

	function bar() {
		console.log( a );
	}

	return bar;
}

var baz = foo();

baz(); // 2 -- Whoa, closure was just observed, man.
```
`bar()` has a lexical scope closure over that inner scope of `foo()`, which keeps that scope alive for `bar()` to reference at later
**`bar()` still has a reference to that scope, and that reference is called closure.**
##### Loops + Closure
```javscript
for (var i=1; i<=5; i++) {
	setTimeout( function timer(){
		console.log( i );
	}, i*1000 );
}
```
-1 The timeout function callbacks are all running well after the completion of the loop.  and thus print 6 each time.
-2 each iteration create a new function, in which has new avariable `i`
Mistake: get "6" printed out 5 times

```javascript
for (var i=1; i<=5; i++) {
	(function(){
		setTimeout( function timer(){
			console.log( i );
		}, i*1000 );
	})();
}
```
IIFE is just an empty do-nothing scope. ???
```javscript
for (var i = 1; i <= 5; i++){
    (function (j){
        setTimeout(function timer(){
            console.log(j);
         }, 100 * j);
    })(i);
}
```
**Block Scoping Revisited**
```javascript
for(let i = 1; j <=5; i++){
    setTimeout(function timer(){
        console.log(i);
        }, 1000*i)
 }
 ```
 `let` delarations used in the head of a for-loop. This behavior says that the variable will be declared not one for the loop, but each iterations.
 ##### Modules
 - 1.There must be an outer enclosing function, and it must be invoked at least once (each time creates a new module instance).

 - 2.The enclosing function must return back at least one inner function, so that this inner function has closure over the private scope, and can access and/or modify that private state.
        
