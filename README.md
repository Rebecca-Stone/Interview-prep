# Interview-prep

## What is Hoisting? [^1]

JavaScript Hoisting refers to the process whereby the interpreter appears to move the _declaration_ of functions, variables, or classes to the top of their scope, prior to execution of the code.

Hoisting allows functions to be safely used in code before they are declared.

Variable and class _declarations_ are also hoisted, so they too can be referenced before they are declared. Note that doing so can lead to unexpected errors, and is not generally recommended.

Note:
: The term hoisting is not used in any normative specification prose prior to [ECMAScript 2015 Language Specification](https://262.ecma-international.org/6.0/). Hoisting was thought up as a general way of thinking about how execution contexts (specifically the creation and execution phases) work in JavaScript.

### Function Hoisting

One of the advantages of hoisting is that it lets you use a function before you declare it in your code.

```
    catName("Tiger");

    function catName(name) {
        console.log(`My cat's name is ${name}`);
    }
    // The result of the code above is: "My cat's name is Tiger"
```

Without hoisting you would _have_ to write the same code like this:

```
    function catName(name) {
        console.log(`My cat's name is ${name}`);
    }

    catName("Tiger"); // The result of the code above is the same: "My cat's name is Tiger"
```

### Variable Hoisting

Hoisting works with variables too, so you use a variable in code before it is declared and/or initialized.

However JavaScript only hoists declarations, not initialization! This means that initialization doesn't happen until the associated line of code is executed, even if the variable was originally initiated then declared, or declared and initialized in the same line.

Until that point in the execution is reached the variable has its _default_ initialization (`undefined` for a variable declared using `var`, otherwise uninitialized).

Note:
: Conceptually variable hoisting is often presented as the interpreter "splitting variable declaration and initialization, and moving (just) the declarations to the top of the code".

Below are some examples showing what can happen if you use a variable before it is declared.

### var hoisting

Here we declare then initialize the value of a `var` after using it. The default initialization of the `var` is `undefined`.

```
console.log(num); // Returns 'undefined' from hoisted var declaration (not 6)
var num; // Declaration
num = 6; // Initialization
console.log(num); // Returns 6 after the line with initialization is executed.
```

The same thing happens if we declare and initialize the variable in the same line.

```
console.log(num); // Returns 'undefined' from hoisted var declaration (not 6)
var num = 6; // Initialization and declaration.
console.log(num); // Returns 6 after the line with initialization is executed.
```

If we forget the declaration altogether (and only initialize the value) the variable isn't hoisted. Trying to read the variable before it is initialized results in `ReferenceError` exception.

```
console.log(num); // Throws ReferenceError exception - the interpreter doesn't know about `num`.
num = 6; // Initialization
```

Note however that initialization also causes declaration (if not already declared). The code snippet below will work, because even though it isn't hoisted, the variable is initialized and effectively declared before it is used.

```
a = 'Cran'; // Initialize a
b = 'berry'; // Initialize b

console.log(`${a}${b}`): // 'Cranberry'
```

### let and const hoisting

Variables declared with `let` and `const` are also hoisted but, unlike `var`, are not initialized with a default value. An exception will be thrown if a variable declared with `let` or `const` is read before it is initialized.

```
console.log(num); // Throws ReferenceError exception as the variable value is uninitialized
let num = 6; // Initialization
```

Note that it is the order in which code is _executed_ that matters, not the order in which it is written in the source file. The code will succeed provided the line that initializes the variable is executed before any line that reads it.

### class hoisting

Classes defined using a [class declaration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#class_declarations) are hoisted, which means that JavaScript has a reference to the class. However the class is not initialized by default, so any code that uses it before the line in which it is initialized is executed will throw a `ReferenceError`

### Function and class expression hoisting

[Function expressions](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) and [class expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#class_expressions) are not hoisted.

The expressions evaluate to a function or class (respectively), which are typically assigned to a variable. In this case the variable declaration is hoisted and the expression is its initialization. Therefore the expressions are not evaluated until the relevant line is executed.

---

## What is the difference between synchronous and asynchronous?

---

## What are the pros and cons of Javascript?

---

## Global vs block level scopes?

---

## Why do we use the "use strict" directives?

---

## What is an IIFE?

---

## What's your coding style?

---

## Dot vs bracket notation?

---

## How do you write clean code with Javascript?

---

[^1]: [mdn web docs](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)
