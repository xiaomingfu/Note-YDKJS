#### What is Scope?
Scope is the set of rules for storing variables in some location, and for finding 
those variables at a later time.
##### Compiler Theory
Compilation: can simplify into three typically steps
 - 1 Tokening/Lexing: `var a = 2;` `var`, `a`, `=`, `2`, `;`
 - 2 Parsing: taking a stream of tokens and turning it into a tree of nested elements:called "AST"
(Abstract Syntax Tree)
`var a = 2;` from tope-level node to child nodes are:
`VariableDeclaration` -> `Identifier` -> `AssignmentExpression` -> `NumericLiteral`

 - 3 Code-Generation: taking an AST and truning it into executalbe code
JavaScript engine is more complex than those three steps. For simplicity's sake,
JS compiler will take the program and compile it first and execute it.

##### Understanding Scope
###### The Cast
 - 1. Engine: compile and execute 
 - 2. Compiler: parse and code-generation
 - 3. Scope: collects and maintains a look-up list of all the declared identifiers
###### Back & Forth
For `var a = 2;` program, engine sees two distinct statements. 
 - Step 1: for `var a` statement, Compiler search a variable`a` in existing Scope, if it doesn't 
 exist, it will declare one. If it exists, compiler moves on.
 - Step 2: for `a = 2` statement, search if there is a variable `a` in existing Scope. If so, Engine
 uses that variable. If not, Engine looks elsewhere. If eventually finds, assigns `2` to it.
 If not, throw an error.
###### Compiler Speak
for step 2, engine has to look-up the variable. There are two type of look-up Engine performs
 - "LHS": find the variable container and assign the value to it(the target of the assignment)
 - "RHS": retrieve the source(value)(the source of the assignment)
 ##### Nested Scope
 The simple rules of nested Scope: Engine starts at the currently executing Scope for look-up variable,
 if not found, keeps going up one level until reach the outermost global scope.
 ##### Errors
 If an RHS look-up fails to find a variable anywhere in the nested Scopes, it results in a `ReferenceError`
 By contrast, LHS look-up fails, and the Engine arrives at the global Scope without finding it,
 and if the program is not running in "Strict Mode", the global Scope will create a new variable
 of that name in the **global scope**.
 
 
