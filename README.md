# Interview-prep

## What is Hoisting? [^1]

JavaScript Hoisting refers to the process whereby the interpreter appears to move the _declaration_ of functions, variables, or classes to the top of their scope, prior to execution of the code.

Hoisting allows functions to be safely used in code before they are declared.

Variable and class _declarations_ are also hoisted, so they too can be referenced before they are declared. Note that doing so can lead to unexpected errors, and is not generally recommended.

**Note The term hoisting is not used in any normative specification prose prior to [ECMAScript 2015 Language Specification](https://262.ecma-international.org/6.0/). Hoisting was thought up as a general way of thinking about how execution contexts (specifically the creation and execution phases) work in JavaScript.**

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

**Note Conceptually variable hoisting is often presented as the interpreter "splitting variable declaration and initialization, and moving (just) the declarations to the top of the code".**

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

**Note however that initialization also causes declaration (if not already declared). The code snippet below will work, because even though it isn't hoisted, the variable is initialized and effectively declared before it is used.**

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

**Note that it is the order in which code is _executed_ that matters, not the order in which it is written in the source file. The code will succeed provided the line that initializes the variable is executed before any line that reads it.**

### class hoisting

Classes defined using a [class declaration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#class_declarations) are hoisted, which means that JavaScript has a reference to the class. However the class is not initialized by default, so any code that uses it before the line in which it is initialized is executed will throw a `ReferenceError`

### Function and class expression hoisting

[Function expressions](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) and [class expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#class_expressions) are not hoisted.

The expressions evaluate to a function or class (respectively), which are typically assigned to a variable. In this case the variable declaration is hoisted and the expression is its initialization. Therefore the expressions are not evaluated until the relevant line is executed.

---

## What is the difference between synchronous and asynchronous? [^2]

Synchronous code runs in sequence. This means that each operation must wait for the previous one to complete before executing.

_JavaScript_

```
console.log('One');
console.log('Two');
console.log('Three');
// LOGS: 'One', 'Two', 'Three'
```

Asynchronous code runs in parallel. This means that an operation can occur while another one is still being processed.

_JavaScript_

```
console.log('One');
setTimeout(() => console.log('Two'), 100);
console.log('Three');
// LOGS: 'One', 'Three', 'Two'
```

Asynchronous code execution is often preferable in situations where execution can be blocked indefinitely. Some examples of this are network requests, long-running calculations, file system operations etc. Using asynchronous code in the browser ensures the page remains responsive and the user experience is mostly unaffected.

## What are the pros and cons of Javascript? [^3]

JavaScript is a programming language. Many of these are related to the way, JavaScript is often executed directly in a client's browser commonly utilized in web development. It was originally developed by netscape as a way to feature dynamic and interactive elements to websites. JavaScript is influenced by Java with similar syntax of C. JavaScript conforms to the ECMAScript specifications which were developed by Sun Microsystems.

JavaScript may be a client-side scripting language, which suggests the ASC11 text file is processed by the client's browser instead of on the online server. This can load the webpage without communicating with the main server by the help of JavaScript. For example, a JavaScript function may check an internet form before it's submitted to make sure all the specified fields are filled out. The JavaScript code can produce an error message before any information is really transmitted to the server.

Like server-side scripting languages, like PHP and ASP, JavaScript code are often inserted anywhere within the HTML of a webpage. The output of the server-side is displayed in the HTML but the JavaScript code remains visible in the source of the webpage. The file can be a separate ".js" file, which can be displayed in the browser.

JavaScript has some advantages and disadvantages. JavaScript is often executed directly on a client's browser. JavaScript can also have the same benefits as server-side languages.

**Advantages of JavaScript:**

- Regardless of where you host JavaScript, it always gets executed on client environment to save lots of a bandwidth and make execution process fast.
- In JavaScript, XMLHttpRequests is an important object that was designed by Microsoft. The object call made by XMLHttpRequest as a asynchronous HTTP request to the server to transfer the data to both sides without reloading the page
- The biggest advantage to JavaScript having an ability to support all modern browsers and produce an equivalent result.
- Global companies support community development by creating projects that are important. An example is Google (created Angular framework) or Facebook (created the React.js framework).
- JavaScript is employed everywhere on the web.
- JavaScript plays nicely with other languages and may be utilized in an enormous sort of applications.
- There are many open source projects that provide a useful help at the developer's add JavaScript.
- There are many available courses within the field of JavaScript, because of which you'll quickly and simply expand your knowledge of this programming language.
- It is not difficult to start working in JavaScript. For this reason, many of us prefer to start their adventure with the IT sector from learning this language.
- It gives power to make rich interfaces.
- There are some ways to use JavaScript through Node.js servers. It is possible to develop a whole JavaScript app from front to back using only JavaScript.

**Disadvantages of JavaScript:**

- This may be difficult to develop large applications, although you'll also use the TypeScript overlay.
- This applies to larger front-end projects. The configuration is often a tedious task to the amount of tools that require to figure together to make an environment for such a project. This is often directly associated with the library's operation.
- The main problem or problem of disadvantage in JavaScript is that the code is always visible to everyone anyone can view JavaScript code.
- No matter what proportion fast JavaScript interpret, JavaScript DOM (Document Object Model) is slow and can be a never fast rendering with HTML.
- If the error occurs in the JavaScript, it can stop to render the whole website. Browsers are extremely tolerant of JavaScript errors.
- JavaScript is usually interpreted differently by different browsers. This makes it somewhat complex to read and write cross-browser code.
- Though some HTML editors support debugging, it's not as efficient as other editors like C/C++ editors. Hence difficult for the developer to detect the matter.
- This continuous conversions take longer in conversion of number to an integer. This increases the time needed to run the script and reduces its speed.

---

## Global vs block level scopes? [^4]

Block scopes are different from function scopes in JavaScript. A function scope is created for every function (and we can nest them too):

```
function iHaveScope() {
    // local function scope

    function iHaveNestedScope() {
        // nested local function scope
    }
}
```

We often identify those scopes as local scopes and identify the top-level scope as the global scope. In a browser environment, the global scope is controlled by the _window_ object while in Node.js, it's controlled by the _global_ object.

It's hard to completely avoid global scope, unles you're coding purely functional style, but you should minimize the use of any global variables because they represent a state and having that defined globally makes it more vulnerable to conflicts and data corruption. You should use an _[Immediately Invoked Function Expression (IIFE)](https://en.wikipedia.org/wiki/Immediately_invoked_function_expression)_ - when you can - to wrap all your JavaScript code in a local function scope (in Node.js, this is actually done automatically for every module, so you don't have to do it there):

```
void function() {
    // your code here
}()
```

Block scopes are what you get when you use if statements, for statements, and the like. You can also use them stand-alone with a simple begin-end curly braces `{}`, not to be confused with empty object literals.

```
var a = {} //empty object literal

{ var a } // undefined object in a block scope

if(3 == '3') {
    // block scope for the if statement
}

for (var i = 0; i < 10; i++){
    // block scope for the for statement
}
```

### var vs. let

The var keyword behaves in function scopes and block scopes. A variable declared with var in a function scope can't be accessed outside that function scope.

```
function iHaveScope() {
    var secret = 42;
}

secret; //ReferenceError: secret is not defined (in this scope)
```

A variable declared with var in a block scope is available outside of that block scope.

```
for (var i = 0; i < 10; i++){
    // block scope for the for statement
}

console.log(i) // => 10 (why oh why)
```

The i variable that we often use in a for loop will continue to exist beyond the scope of that loop, and that does not make sense, really.

Luckily we now have a different way to declare variables, using let. Variables declared with let inside a block scope are only accessible inside that scope, making let the ideal solution to the for loop index variable scope problem. If we use let to declare the i variable in a for loop, that variable will only be available inside the for loop.

```
for(let i = 0; i < 10; i++) {
    // block scope for the for statement
}

console.log(i) // ReferenceError: i is not defined (D'oh!)
```

### const

Declaring a variable with const is exactly like let - when it comes to scopes - but creates a _constant reference_ for the variable. We can't change the value of a constant reference. If we put a primitive value in a constant, that value will be protected from getting changed:

```
const PI = 3.141592653589793
PI = 42 // SyntaxError: "PI" is read-only
```

Note that if the constant is an object, we can still change the properties of that object, so be careful about that:

```
const dessert = { type: 'pie' };
dessert.type = 'pudding'; // Sure thing

console.log(dessert.type) // pudding
```

We can't however, reassign an object declared with const:

```
const dessert = { type: 'pie' };
dessert = { type: 'cake' }; // SyntaxError: "dessert" is read-only
```

If we want a completely immutable object, we'll have to use something else. My favorite library for that is [Immutable.js](https://facebook.github.io/immutable-js/)

Constants are popularly used when importing things from other libraries so that they don't get changed accidentally. In Node.js for example, we use it with the require function:

```
const _ = require('lodash');
```

Constants are also great to use when defining functions, because we rarely need to update a function after we define it the first time.

In general, I think it's good to always use const for your declarations and only switch to let or var if you actually need to. With const, you get the peace of mind that no mutating reassignments are happening on a variable, while with let/var, you'll have to read the code to verify that:

```
let answer = 42;
// some code ...

//answer MIGHT be 42 here, read the code to be sure.

// ***
// VS.
// ***

const answer = 42;
// some code ...

// answer IS STILL 42 here, no matter what happens above
```

---

## Why do we use the "use strict" directives? [^5]

The **"use strict"** directive was new in ECMAScript version 5.

It is not a statement, but a literal expression, ignored by earlier versions of JavaScript.

The purpose of **"use strict"** is to indicate that the code should be executed in "strict mode".

With strict mode, you can not for example, use undeclared variables.

All modern browsers support **"use strict"** except Internet Explorer 9 and lower.

You can use strict mode in all your programs. it helps you to write cleaner code, like preventing you from using undeclared variables.

**"use strict"** is just a string, so IE 9 will not throw an error even if it does not understand it.

### Why Strict Mode?

Strict mode makes it easier to write "secure" JavaScript.

Strict mode changes previously accepted "bad syntax" into real errors.

As an example, in normal JavaScript, mistyping a variable name creates a new global variable. In strict mode, this will throw an error, making it impossible to accidentally create a global variable.

In normal JavaScript, a developer will not recive any error feedback assigning values to non-writable properties.

In script mode, any assignment to a non-writable property, a getter-only property, a non-existing property, a non-existing object, will throw an error.

---

## What is an IIFE? [^6]

An IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined. The name IIFE is promoted by Ben Alman in [his blog](https://web.archive.org/web/20171201033208/http://benalman.com/news/2010/11/immediately-invoked-function-expression/#iife).

```
(function () {
    // ...
})();

(() => {
    // ...
})();

(async () => {
    // ...
})();
```

It is a design pattern which is also known as a [Self-Executing Anonymous Function](https://developer.mozilla.org/en-US/docs/Glossary/Self-Executing_Anonymous_Function) and contains two major parts:

1. The first is the anonymous function with lexical scope enclossed within the [Grouping Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Grouping) `()`. This prevents accessing variables within the IIFE idiom as well as polluting the global scope.

2. The second part creates the immediately invoked function expression `()` through which the JavaScript engine will directly interpret the function.

### Use cases

#### Avoid polluting the global namespace

Because our application could include many functions and global variables from different source files, it's important to limit the number of global variables. If we have some initiation code that we don't need to use again, we could use the IIFE pattern. As we will not reuse the code again, using IIFE in this case is better than using a function declaration or a function expression.

```
(() => {
    // some initiation code
    let firstVariable;
    let secondVariable;
})();

// firstVariable and secondVariable will be discarded after the function is executed.
```

#### Execute an async function

An [`async`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/async_function) IIFE allows you ti use [`await`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await) and [`for-await`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for-await...of) even in older browsers and JavaScript runtimes that have no [top-level await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await#top_level_await):

```
const getFileStream = async (url) => {
    // implementation
};

(async () => {
    const stream = await
    getFileStream('https://domain.name/path/file.ext');
    for await (const chunk of stream) {
        console.log({ chunk });
    }
})();
```

#### The module pattern

We would also use IIFE to create private and public variables and methods. For a more sophisticated use of the module pattern and other use of IIFE, you could see the Learning JavaScript Design Patterns by Addy Osmani.

```
const makeWithdraw = (balance) => ((copyBalance) => {
    let balance = copyBalance; // this variable is private
    const doBadThings = () => {
        console.log('I will do bad things with your money');
    };
    doBadThings();
    return {
        withdraw(amount) {
            if(balance >= amount) {
                balance -= amount;
                return balance;
            }
            return 'Insufficient money';
        },
    };
})(balance);

const firstAccount = makeWithdraw(100);
// "I will do bad things with your money"
console.log(firstAccount.balance);
// undefined
console.log(firstAccount.withdraw(20));
// 80
console.log(firstAccount.withdraw(30));
// 50
console.log(firstAccount.doBadThings);
// undefined; this method is private
const secondAccount = makeWithdraw(20);
// "I will do bad things with your money"
console.log(secondAccount.withdraw(30));
// "Insufficient money"
console.log(secondAccount.withdraw(20));
// 0
```

#### For loop with var before ES6

We could see the following use of IIFE in some old code, before the introduction of the statements **let** and **const** in **ES6** and the block scope. With the statement **var**, we have only function scopes and the global scope. Suppose we want to create 2 buttons with the texts Button 0 and Button 1 and when we click them, we would like them to alert 0 and 1. The following code doesn't work:

```
for (var i = 0; i < 2; i++) {
    const button =
    document.createElement('button');
    button.innerText = `Button ${i}`;
    button.onclick = function() {
        console.log(i);
    };
    document.body.appendChild(button);
}

console.log(i); // 2
```

When clicked, both Button 0 and Button 1 alert 2 because `i` is global, with the last value 2. To fix this problem before ES6, we could use the IIFE pattern:

```
for (var i = 0; i < 2; i++) {
    const button = document.createElement('button');
    button.innerText = `Button ${i}`;
    button.onclick = (function(copyOfI) {
        return () => {
            console.log(copyOfI);
        };
    })(i);
    document.body.appendChild(button);
}

console.log(i); // 2
```

When clicked, Buttons 0 and 1 alert 0 and 1. The variable `i` is globally defined. Using the statement **let**, we could simply do:

```
for(let i = 0; i < 2; i++) {
    const button = document.createElement("button");
    button.innerText = `Button ${i}`;
    button.onclick = function() {
        console.log(i);
    };
    document.body.appendChild(button);
}

console.log(i); // Uncaught ReferenceError: i is not defined.
```

When clicked, these buttons alert 0 and 1.

---

## What's your coding style?

---

## Dot vs bracket notation?

---

## How do you write clean code with Javascript?

---

[^1]: [mdn web docs](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)
[^2]: [30 Seconds of Code](https://www.30secondsofcode.org/articles/s/javascript-sync-async)
[^3]: [GeeksforGeeks](https://www.geeksforgeeks.org/advantages-and-disadvantages-of-javascript/)
[^4]: [medium](https://medium.com/edge-coders/function-scopes-and-block-scopes-in-javascript-25bbd7f293d7#:~:text=In%20a%20browser%20environment%2C%20the,controlled%20by%20the%20global%20object.&text=Block%20scopes%20are%20what%20you,for%20statements%2C%20and%20the%20like.)
[^5]: [w3schools](https://www.w3schools.com/js/js_strict.asp#:~:text=The%20%22use%20strict%22%20Directive&text=The%20purpose%20of%20%22use%20strict,for%20example%2C%20use%20undeclared%20variables.&text=The%20numbers%20in%20the%20table,that%20fully%20supports%20the%20directive.)
[^6]: [mdn web docs](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)
