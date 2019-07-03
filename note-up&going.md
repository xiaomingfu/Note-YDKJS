## Chapter 1: Into Programming
### Code
  - Statements
  - Expressions: 
    - 1. literal value expression: `2`; 
    - 2. varial expression: `b`; 
    - 3. arithmetic expression: `b * 2`; 
    - 4. assignment expression: `a = b * 2`;
    - 5. general expression(expression statement): `b * 2`(not common); function(common): `alert(a)`;
  - Executing a program
    - Interpreter: For some computer languages, this translation of commands is typically done from top to bottom, line by line, every time the program is run, which is usually called interpreting the code.
    - Compiler: For other languages, the translation is done ahead of time, called compiling the code, so when the program runs later, what's running is actually the already compiled computer instructions ready to go.
### Try it yourself
  - Output: `console.log()`; `alert()`; 
  - Input: `prompt()`;
  - Operators: 
    - Assignment: `=`;
    - Math: `+`, `-`, `*`, `/`;
    - Compound assignment: `+=`, `-=`, `*=`, `/=`;
    - Incremnet/decrement: `++`, `--`;
    - Object property access: `.` as in `console.log()` or `obj['a']`;
    - comparison: `<`, `<=`, `>`, `>=`;
    - logical: `&&`, `||`;
    - Equality: `==`, `===`, `!=`, `!===`;
  - Declare the variable: `var`, `const`, `let`;
    - declare a variable once for each scope;
### Values & Types
  - Primitive Values: `number`, `string`, `boolean`;
  - Converting Between Types
    > If you have a number but need to print it on the screen, you need to convert the value to a string, and in JavaScript this conversion is called "coercion."
    - `Number(..)` > (a built-in function) as shown is an explicit coercion from any other type to the number type. 
    - `==` > loose equals operator to make the comparison "99.99" == 99.99, JavaScript will convert the left-hand side "99.99" to its number equivalent 99.99. The comparison then becomes 99.99 == 99.99, which is of course true.
#### Code Comments
  > Code without comments is suboptimal.
  > Too many comments (one per line, for example) is probably a sign of poorly written code.
  > Comments should explain why, not what. They can optionally explain how if that's particularly confusing.
  - `// This is for single-line comment`
  -  `/* This is 
         a mulitline
                comment.
                        */` 
 #### Variables
  - Static typing > otherwise known as type enforcement
  - Weak typing, aslo know as Dynamic typing 
  
    ````var amount = 99.99; // 

      amount = amount * 2;

      console.log( amount );		// 199.98

      // convert 'amount' to a string, and
      // add "$" on the beginning
      amount = "$" + String( amount );

      console.log( amount );		// "$199.98"````
      
   > The first console.log(..) command has to implicitly coerce that number value to a string to print it out.
   
   > Then the statement amount = "$" + String(amount) explicitly coerces the 199.98 value to a string and adds a "$" character to the beginning. 
   
   > Either way, you'll note that amount holds a running value that changes over the course of the program, illustrating the primary purpose of variables: managing program state.
   
   - constants: intend for that value to not change throughout the program. often at the top of a program, are usually capitalized, with underscores _ between multiple words. `var TAX_RATE = 0.08 \\using const instead of var ('ES6')` 
 #### Blocks
   - general block `{..}`, not common, Typically, blocks are attached to some other control statement
 #### Conditionals
   - `if` statement
   > The if statement expects a boolean, but if you pass it something that's not already boolean, coercion will occur
 #### Loops
   -  `while` loop and `do..while` loop: difference between these loops is whether the conditional is tested before the first iteration (while) or after the first iteration (do..while).
   -  `for` loop
 #### Functions
   - > Functions are often used for code that you plan to call multiple times, but they can also be useful just to organize related bits of code into named collections, even if you only plan to call them once.
 #### Scope
   - > Lexical scope rules say that code in one scope can access variables of either that scope or any scope outside of it.
