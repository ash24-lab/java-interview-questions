
# Top 20 JavaScript Interview Questions and Answers for Freshers

## 1. What is JavaScript?

JavaScript is a high-level programming language primarily used to make web pages interactive and dynamic.

It is one of the core technologies of web development:

- HTML – Creates the structure of a webpage.
- CSS – Styles the webpage.
- JavaScript – Adds functionality and interactivity.

Example:

```javascript
let name = "Ashfaq";
console.log("Hello " + name);
```

JavaScript can also be used for backend development using Node.js.

---

## 2. Difference between var, let and const?

In JavaScript, `var`, `let`, and `const` are used to declare variables.

| Feature | var | let | const |
|---|---|---|---|
| Scope | Function | Block | Block |
| Redeclaration | Allowed | Not allowed | Not allowed |
| Reassignment | Allowed | Allowed | Not allowed |
| Hoisting | Yes | Yes | Yes |
| Initialization | Optional | Optional | Required |

Example:

```javascript
var a = 10;
var a = 20;

let b = 10;
b = 20;

const c = 10;
// c = 20; // Error
```

**Interview Tip:** I prefer using `let` and `const` because they provide block scope and help avoid unexpected errors. I use `const` when reassignment is not required and `let` when reassignment is required.

---

## 3. What are JavaScript data types?

JavaScript has two main categories of data types:

1. Primitive data types.
2. Non-primitive (reference) data types.

### Primitive Data Types

There are 7 primitive data types:

1. String – `"Hello"`
2. Number – `100`, `10.5`
3. Boolean – `true`, `false`
4. Undefined – `undefined`
5. Null – `null`
6. BigInt – `123456789n`
7. Symbol – `Symbol("id")`

### Non-Primitive Data Types

- Object
- Array
- Function

Example:

```javascript
let name = "Ashfaq";
let age = 22;
let isStudent = true;

let person = {
    name: "Ashfaq",
    age: 22
};

let numbers = [10, 20, 30];
```

---

## 4. Difference between == and ===?

Both operators are used to compare values in JavaScript.

- `==` – Loose equality operator. It compares values after performing type conversion when necessary.
- `===` – Strict equality operator. It compares both value and data type without type conversion.

Example:

```javascript
console.log(10 == "10");  // true
console.log(10 === "10"); // false
```

**Interview Tip:** I prefer using `===` because it avoids unexpected type conversions.

---

## 5. What is hoisting?

Hoisting is a JavaScript mechanism in which variable and function declarations are processed before the code executes.

Example with var:

```javascript
console.log(a);

var a = 10;
```

Output:

```text
undefined
```

Example with let:

```javascript
console.log(a);

let a = 10;
```

Output:

```text
ReferenceError
```

**Important Points:**

- `var` declarations are hoisted and initialized with `undefined`.
- `let` and `const` are hoisted but cannot be accessed before initialization because of the Temporal Dead Zone (TDZ).
- Function declarations can be called before their declaration.

---

## 6. What is a closure?

A closure is a combination of a function and its surrounding lexical environment.

It allows an inner function to access variables from its outer function even after the outer function has finished executing.

Example:

```javascript
function outer() {
    let count = 0;

    function inner() {
        count++;
        console.log(count);
    }

    return inner;
}

let result = outer();

result();
result();
result();
```

Output:

```text
1
2
3
```

**Real-world Uses:**

- Data privacy.
- Maintaining state.
- Creating function factories.
- Event handlers.

---

## 7. What is the this keyword?

The `this` keyword in JavaScript refers to the object associated with the current function call.

Its value depends on how a function is called.

Example:

```javascript
const person = {
    name: "Ashfaq",

    greet: function() {
        console.log(this.name);
    }
};

person.greet();
```

Output:

```text
Ashfaq
```

Here, `this` refers to the `person` object because the function is called using `person.greet()`.

**Important Points:**

- In an object method, `this` generally refers to the object before the dot.
- In a regular function, `this` depends on the calling context.
- In an arrow function, `this` is inherited from the surrounding lexical scope.

---

## 8. What is an arrow function?

An arrow function is a shorter way of writing a function in JavaScript.

It was introduced in ES6 (ECMAScript 2015).

It uses the `=>` symbol.

Normal Function:

```javascript
function add(a, b) {
    return a + b;
}
```

Arrow Function:

```javascript
const add = (a, b) => {
    return a + b;
};
```

Shorter Syntax:

```javascript
const add = (a, b) => a + b;

console.log(add(10, 20));
```

Output:

```text
30
```

Arrow functions are commonly used in callbacks, array methods, and React development.

---

## 9. Difference between normal functions and arrow functions?

| Feature | Normal Function | Arrow Function |
|---|---|---|
| Syntax | function keyword | => |
| this | Depends on how it is called | Lexical this |
| Arguments object | Available | Not available |
| Constructor | Can be used with new | Cannot be used with new |
| Hoisting | Function declarations are hoisted | Depends on variable declaration |

Normal Function:

```javascript
function greet() {
    console.log("Hello");
}
```

Arrow Function:

```javascript
const greet = () => {
    console.log("Hello");
};
```

**Interview Tip:** Arrow functions are useful for shorter syntax and lexical `this`, whereas normal functions are useful when we need dynamic `this` or constructor functionality.

---

## 10. What is a callback function?

A callback function is a function that is passed as an argument to another function and is executed later by that function.

Example:

```javascript
function greet(name, callback) {
    console.log("Hello " + name);

    callback();
}

function message() {
    console.log("Welcome!");
}

greet("Ashfaq", message);
```

Output:

```text
Hello Ashfaq
Welcome!
```

**Real-world Uses:**

- Event handling.
- Asynchronous operations.
- Array methods like `map()` and `filter()`.

---

## 11. What is a Promise?

A Promise is an object in JavaScript that represents the eventual completion or failure of an asynchronous operation.

A Promise has three states:

1. Pending – Initial state.
2. Fulfilled – Operation completed successfully.
3. Rejected – Operation failed.

Example:

```javascript
let promise = new Promise((resolve, reject) => {

    let success = true;

    if (success) {
        resolve("Operation successful");
    } else {
        reject("Operation failed");
    }

});

promise
    .then(result => console.log(result))
    .catch(error => console.log(error));
```

Output:

```text
Operation successful
```

**Important Methods:**

- `then()` – Handles successful completion.
- `catch()` – Handles errors.
- `finally()` – Executes after the Promise settles, regardless of outcome.

---

## 12. What is async/await?

Async and await are keywords in JavaScript used to handle asynchronous operations.

They make asynchronous code easier to read and understand compared to traditional Promise chaining.

- `async` makes a function return a Promise.
- `await` waits for a Promise to settle and returns its fulfilled value or throws its rejection reason.

Example:

```javascript
function getData() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Data received");
        }, 2000);
    });
}

async function displayData() {
    let result = await getData();

    console.log(result);
}

displayData();
```

Output after 2 seconds:

```text
Data received
```

**Error Handling:**

```javascript
async function getData() {
    try {
        let response = await fetch(
            "https://jsonplaceholder.typicode.com/users"
        );

        let data = await response.json();

        console.log(data);

    } catch (error) {
        console.log(error);
    }
}
```

**Interview Tip:** Async/await is built on top of Promises and makes asynchronous code look more like synchronous code.

---

## 13. What is the DOM?

DOM stands for Document Object Model.

It is a programming interface that represents an HTML document as a tree structure of objects.

JavaScript uses the DOM to access, modify, add, and delete HTML elements and their content.

Example HTML:

```html
<h1 id="heading">Hello</h1>
```

JavaScript:

```javascript
let element = document.getElementById("heading");

element.innerHTML = "Welcome to JavaScript";
```

Output on webpage:

```text
Welcome to JavaScript
```

**Common DOM Methods:**

| Method | Purpose |
|---|---|
| getElementById() | Select element by ID |
| getElementsByClassName() | Select elements by class |
| getElementsByTagName() | Select elements by tag |
| querySelector() | Select first matching element |
| querySelectorAll() | Select all matching elements |
| createElement() | Create an HTML element |

---

## 14. What is event bubbling?

Event bubbling is a process in JavaScript where an event starts from the target element and propagates upward through its parent elements.

Example:

```html
<div id="parent">
    <button id="child">Click Me</button>
</div>
```

```javascript
document.getElementById("parent").addEventListener(
    "click",
    function() {
        console.log("Parent clicked");
    }
);

document.getElementById("child").addEventListener(
    "click",
    function() {
        console.log("Button clicked");
    }
);
```

Output when clicking the button:

```text
Button clicked
Parent clicked
```

**How to stop event bubbling?**

We can use:

```javascript
event.stopPropagation();
```

---

## 15. Difference between null and undefined?

Both represent the absence of a meaningful value, but they have different meanings.

- `undefined` means a variable has been declared but has not been assigned a value.
- `null` represents an intentional absence of a value.

Example:

```javascript
let a;

let b = null;

console.log(a);
console.log(b);
```

Output:

```text
undefined
null
```

Additional Difference:

```javascript
console.log(typeof a);
console.log(typeof b);
```

Output:

```text
undefined
object
```

Note: `typeof null` returning `"object"` is a historical JavaScript behavior.

---

## 16. What are map(), filter() and reduce()?

These are JavaScript array methods used to process array elements.

### 1. map()

The `map()` method creates a new array by applying a function to every element of the original array.

Example:

```javascript
let numbers = [1, 2, 3, 4];

let result = numbers.map(num => num * 2);

console.log(result);
```

Output:

```text
[2, 4, 6, 8]
```

### 2. filter()

The `filter()` method creates a new array containing elements that satisfy a given condition.

Example:

```javascript
let numbers = [1, 2, 3, 4, 5];

let result = numbers.filter(num => num > 2);

console.log(result);
```

Output:

```text
[3, 4, 5]
```

### 3. reduce()

The `reduce()` method reduces all array elements into a single accumulated value.

Example:

```javascript
let numbers = [1, 2, 3, 4];

let result = numbers.reduce(
    (total, num) => total + num, 0
);

console.log(result);
```

Output:

```text
10
```

**Difference:**

| Method | Purpose | Returns |
|---|---|---|
| map() | Transform elements | New array |
| filter() | Filter elements | New array |
| reduce() | Accumulate values | Single accumulated value |

---

## 17. What is destructuring?

Destructuring is an ES6 feature that allows us to extract values from arrays or properties from objects and store them in variables easily.

### Array Destructuring

```javascript
let numbers = [10, 20, 30];

let [a, b, c] = numbers;

console.log(a);
console.log(b);
console.log(c);
```

Output:

```text
10
20
30
```

### Object Destructuring

```javascript
let person = {
    name: "Ashfaq",
    age: 22
};

let { name, age } = person;

console.log(name);
console.log(age);
```

Output:

```text
Ashfaq
22
```

---

## 18. What is the spread operator?

The spread operator was introduced in ES6. It uses three dots (`...`) to expand elements of an array or properties of an object.

### Example 1: Copying an Array

```javascript
let arr1 = [10, 20, 30];

let arr2 = [...arr1];

console.log(arr2);
```

Output:

```text
[10, 20, 30]
```

### Example 2: Combining Arrays

```javascript
let a = [1, 2];
let b = [3, 4];

let result = [...a, ...b];

console.log(result);
```

Output:

```text
[1, 2, 3, 4]
```

### Example 3: Combining Objects

```javascript
let person = {
    name: "Ashfaq"
};

let details = {
    age: 22
};

let result = {...person, ...details};

console.log(result);
```

Output:

```text
{ name: "Ashfaq", age: 22 }
```

**Important:** Spread syntax creates a shallow copy, not a deep copy.

---

## 19. What is localStorage?

LocalStorage is a web storage mechanism that allows us to store key-value pairs in the browser.

The stored data remains available even after refreshing or closing the browser, until it is explicitly removed or cleared by the browser.

Example:

```javascript
// Store data
localStorage.setItem("username", "Ashfaq");

// Get data
let name = localStorage.getItem("username");

console.log(name);

// Remove specific data
localStorage.removeItem("username");

// Clear all data for the origin
localStorage.clear();
```

Output:

```text
Ashfaq
```

**Important Points:**

- Data is stored as strings.
- Data persists across browser sessions.
- It is specific to the website's origin.
- It is commonly used for storing user preferences and settings.

### How to store objects?

We use `JSON.stringify()` to convert objects into strings.

```javascript
let user = {
    name: "Ashfaq",
    age: 22
};

localStorage.setItem("user", JSON.stringify(user));
```

To retrieve the object:

```javascript
let data = JSON.parse(localStorage.getItem("user"));

console.log(data.name);
```

---

## 20. What is JSON?

JSON stands for JavaScript Object Notation.

It is a lightweight data-interchange format used to store and exchange data between applications, especially between frontend and backend systems.

JSON is language-independent, although its syntax is based on JavaScript object notation.

Example JSON:

```json
{
    "name": "Ashfaq",
    "age": 22,
    "city": "Chennai"
}
```

**Important JSON Methods:**

1. `JSON.stringify()` – Converts a JavaScript value into a JSON string.
2. `JSON.parse()` – Converts a valid JSON string into a JavaScript value.

Example:

```javascript
let person = {
    name: "Ashfaq",
    age: 22
};

// Object to JSON string
let jsonData = JSON.stringify(person);

console.log(jsonData);

// JSON string to object
let obj = JSON.parse(jsonData);

console.log(obj.name);
```

Output:

```text
{"name":"Ashfaq","age":22}
Ashfaq
```

---

# Quick Revision Table

| No. | Question | Key Point |
|---|---|---|
| 1 | JavaScript | Interactive web pages |
| 2 | var, let, const | Scope and reassignment |
| 3 | Data types | 7 primitive types |
| 4 | == vs === | Loose vs strict equality |
| 5 | Hoisting | Declarations processed before execution |
| 6 | Closure | Remembers outer scope |
| 7 | this | Depends on calling context |
| 8 | Arrow function | => syntax |
| 9 | Normal vs arrow | Dynamic vs lexical this |
| 10 | Callback | Function passed as argument |
| 11 | Promise | Pending, fulfilled, rejected |
| 12 | Async/await | Asynchronous programming |
| 13 | DOM | HTML document tree |
| 14 | Event bubbling | Child to parent |
| 15 | null vs undefined | Intentional vs unassigned |
| 16 | map/filter/reduce | Transform, filter, accumulate |
| 17 | Destructuring | Extract values |
| 18 | Spread | Expand elements/properties |
| 19 | localStorage | Persistent browser storage |
| 20 | JSON | Data exchange format |

---

# Interview Preparation Tips

1. Understand the concepts instead of memorizing answers.
2. Practice writing JavaScript programs every day.
3. Focus on closures, promises, callbacks, and array methods.
4. Understand the difference between normal and arrow functions.
5. Practice DOM manipulation and event handling.
6. Prepare output-based JavaScript questions.
7. Explain your answers confidently with examples.
