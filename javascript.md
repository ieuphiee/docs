## JavaScript
### What is event delegation?
The technique of attaching event listeners to parent elements instead of child elements, so that whenever an event is fired on a child element, due to event bubbling up the DOM, the parent event listener will be able to “catch” that event.
- Removes the need to attach different event listeners on multiple descendants, have a single handler on the parent element

### Describe the “this” keyword.
The value of “this” depends on the context in which the function was called.

### Difference between undeclared, undefined, and null variables.
- Undeclared – no such variable has been created with either the const, var, or let keywords
- Undefined – variable created, but no value was ever explicitly assigned to it
- Null – variable created, and value of “null” was explicitly assigned to it

### What is a closure?
Refers to the combination of a function bundled together with the lexical environment (surrounding state) that that function was declared. Lexical scoping determines where variables are available.

A closure is a function that has access to outer (enclosing) function’s variables.

### Difference between: function `Person(){}`, `var person = Person()`, and `var person = new Person()`?
1.	Function declaration
2.	Invokes the Person function, is a mistake if the function is intended to be used as a constructor, typically constructor does not return anything, so this will return “undefined” to the person variable intended as the instance
3.	Creates a new instance “person” of the Person object using the “new” operator

### Explain hoisting.
Hoisting is the process in which variable/function declarations are “hoisted” to the top of their module/function-level scope. Only the declaration is hoisted and not the assignment of the value.
- Function declarations have their entire body hoisted while function expressions (variable declarations) only has the variable declaration hoisted

### What is “use strict”?
Turns on strict mode, opt into restricted variant of JavaScript:
-	“this” is undefined in the global context
-	Catches common coding bloops, throws exceptions
-	Disables certain features that are confusing
-	Impossible to accidentally create global variables

### What are promises?
A promise is an object that will definitely have a value in the future, either a resolved value or unresolved with an error.

### What is a callback function?
“called at the back of a function” / “call after” function
Is a function which is immediately called after the first function, if it completes. Usually passed in as an argument to another function, such that when the parent method completes the callback fn is invoked afterwards

### Explain the difference between synchronous and asynchronous functions.
-	Synchronous – blocking; statements must complete before the next statement can be run, program is executed in the order the code is written 
-	Asynchronous – non-blocking; often accept a callback function to run after the function is invoked, other code will not wait for the function to complete (aka will continue execution after the function is invoked)
    - Heavy duty operations like fetching data from an API call should be done asynchronously so that the main thread can continue to perform other tasks, instead of waiting for the network call to complete

### What are the differences between variables created using `let`, `var` or `const`?
•	Var – scoped to the function in which they are created, else scoped to the global object
•	Let – is block-scoped, only accessible within nearest pair of curly brackets (like if else), is mutable (value can be changed)
•	Const – is block-scoped, is immutable (value cannot be changed)

### Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
Arrow functions are an ES6 feature
•	Simplifies syntax for creating functions
•	The “this” keyword is lexically scoped in arrow functions, compared to regular functions where the `this` keyword is bound to the object from which it was called

### What is destructuring?
ES6 expression which allows you to extract specific values of an object or array and place them into distinct variables.

### What is spread syntax?
ES6 syntax that allows you to quickly create copies of arrays or objects.
Also shorthand for including an arbitrary # of arguments to be passed into a function.


