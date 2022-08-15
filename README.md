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
- Though some HTML editors support debugging, it's not as efficient as other editors like C/C++ editors. Hence difficult for the deve;oper to detect the matter.
- This continuous conversions take longer in conversion of number to an integer. This increases the time needed to run the script and reduces its speed.

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
[^2]: [30 Seconds of Code](https://www.30secondsofcode.org/articles/s/javascript-sync-async)
[^3]: [GeeksforGeeks](https://www.geeksforgeeks.org/advantages-and-disadvantages-of-javascript/)
