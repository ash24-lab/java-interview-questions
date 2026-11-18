# React.js Interview Questions and Answers for Freshers

## 1. What is React.js?

**Answer:**

React.js is an open-source JavaScript library developed by Facebook (now Meta) for building user interfaces, especially single-page applications (SPAs).

It allows developers to create reusable UI components and efficiently update the user interface using the Virtual DOM.

**Key points:**
- Developed by Facebook (Meta).
- Used for building user interfaces.
- Component-based architecture.
- Supports reusable components.
- Uses Virtual DOM for efficient UI updates.

## 2. What are components?

**Answer:**

Components are the building blocks of a React application. They are independent and reusable pieces of UI.

Each component can contain its own logic, structure, and styling.

**Example:**

```jsx
function Welcome() {
  return <h1>Welcome to React</h1>;
}

function App() {
  return (
    <div>
      <Welcome />
      <Welcome />
    </div>
  );
}
```

Here, `Welcome` is a reusable component.

**Types of components:**
1. Functional components.
2. Class components.

## 3. Difference between functional and class components?

**Answer:**

Functional components are JavaScript functions that return JSX, whereas class components are ES6 classes that extend `React.Component` and use a render method to return JSX.

| Functional Components | Class Components |
|---|---|
| Created using functions. | Created using ES6 classes. |
| Use Hooks for state and lifecycle features. | Use lifecycle methods. |
| Do not use `this` to access props or state. | Use `this` to access props and state. |
| Less code and easier to understand. | Usually require more code. |
| Preferred in modern React development. | Common in older React applications. |

**Functional component:**

```jsx
function Welcome() {
  return <h1>Hello World</h1>;
}
```

**Class component:**

```jsx
import React, { Component } from "react";

class Welcome extends Component {
  render() {
    return <h1>Hello World</h1>;
  }
}
```

## 4. What are props?

**Answer:**

Props stand for properties. They are used to pass data from a parent component to a child component.

Props are read-only, which means a child component should not directly modify the props received from its parent.

**Example:**

```jsx
function Student(props) {
  return <h1>Hello {props.name}</h1>;
}

function App() {
  return <Student name="Ashfaq" />;
}
```

**Output:**
```
Hello Ashfaq
```

Here, `name` is a prop passed from the parent component to the child component.

## 5. What is state?

**Answer:**

State is an object or value used to store data that can change over time in a React component.

When the state changes using the appropriate state setter, React schedules a re-render to update the UI.

**Example:**

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}
```

Here:
- `count` stores the current value.
- `setCount` updates the state.
- `useState(0)` initializes the state with 0.

## 6. Difference between props and state?

**Answer:**

Props and state are both used to manage data in React, but they have different purposes.

| Props | State |
|---|---|
| Used to pass data between components. | Used to manage a component's data. |
| Received from the parent component. | Managed by the component itself. |
| Read-only for the receiving component. | Updated using a state setter. |
| Changes when the parent provides new props. | Changes when its setter is called. |
| Used for communication between components. | Used for managing dynamic data. |

**Example:**
- Props: Passing a student's name from the parent to the child.
- State: Updating a counter when a button is clicked.

## 7. What is the Virtual DOM?

**Answer:**

The Virtual DOM is a lightweight, in-memory representation of the real DOM.

When the state or props change, React creates an updated UI representation, compares it with the previous one, and determines what needs to change in the real DOM.

This process helps React update the UI efficiently.

**Key points:**
- Virtual DOM is a representation of the real DOM.
- It helps React calculate UI changes.
- React uses reconciliation to update the real DOM.

## 8. What is JSX?

**Answer:**

JSX stands for JavaScript XML. It is a syntax extension for JavaScript that allows us to write HTML-like code inside JavaScript.

React uses JSX to describe what the user interface should look like.

**Example:**

```jsx
function App() {
  const name = "Ashfaq";

  return (
    <div>
      <h1>Hello {name}</h1>
    </div>
  );
}
```

**Output:**
```
Hello Ashfaq
```

**Advantages of JSX:**
- Makes code easier to read.
- Allows JavaScript expressions inside UI.
- Makes UI development easier.
- Supports reusable components.

## 9. What are React Hooks?

**Answer:**

Hooks are special functions introduced in React 16.8 that allow functional components to use state and other React features without writing class components.

**Common React Hooks:**

| Hook | Purpose |
|---|---|
| `useState` | Manages state. |
| `useEffect` | Handles side effects. |
| `useMemo` | Memoizes calculated values. |
| `useCallback` | Memoizes functions. |
| `useRef` | Stores mutable references. |
| `useContext` | Accesses context values. |

**Important:** Hooks should generally be called at the top level of React function components or custom Hooks, not inside loops, conditions, or nested functions.

## 10. What is useState?

**Answer:**

`useState` is a React Hook used to add and manage state in functional components.

It returns an array containing the current state value and a function to update that value.

**Syntax:**

```jsx
const [state, setState] = useState(initialValue);
```

**Example:**

```jsx
import { useState } from "react";

function App() {
  const [name, setName] = useState("Ashfaq");

  return (
    <div>
      <h1>{name}</h1>

      <button onClick={() => setName("React")}>
        Change Name
      </button>
    </div>
  );
}
```

Here:
- `name` is the current state.
- `setName` updates the state.
- `"Ashfaq"` is the initial value.

## 11. What is useEffect?

**Answer:**

`useEffect` is a React Hook used to perform side effects in functional components.

Side effects are operations that interact with something outside the component's rendering process.

**Common uses:**
- Fetching data from APIs.
- Setting up subscriptions.
- Managing timers.
- Updating document-related information.
- Synchronizing with external systems.

**Example:**

```jsx
import { useEffect } from "react";

function App() {
  useEffect(() => {
    console.log("Component mounted");
  }, []);

  return <h1>Hello React</h1>;
}
```

Here, the empty dependency array means the Effect runs after the component initially mounts (once per mount, subject to React development Strict Mode behavior).

## 12. What is useMemo?

**Answer:**

`useMemo` is a React Hook used to memoize the result of an expensive calculation.

It helps avoid recalculating a value unnecessarily when the dependencies have not changed.

**Example:**

```jsx
import { useMemo, useState } from "react";

function App() {
  const [number, setNumber] = useState(5);

  const result = useMemo(() => {
    console.log("Calculating...");
    return number * number;
  }, [number]);

  return (
    <div>
      <h1>{result}</h1>

      <button onClick={() => setNumber(number + 1)}>
        Increase
      </button>
    </div>
  );
}
```

Here:
- `useMemo` stores the calculated result.
- The calculation runs again when `number` changes.
- It avoids unnecessary recalculations when dependencies remain unchanged.

**Important:** `useMemo` is a performance optimization, not a requirement for every calculation.

## 13. What is conditional rendering?

**Answer:**

Conditional rendering means displaying different UI elements based on a condition.

In React, we can use JavaScript conditions such as `if`, ternary operators, and logical AND (`&&`) for conditional rendering.

**Example using ternary operator:**

```jsx
function App() {
  const isLoggedIn = true;

  return (
    <div>
      {isLoggedIn ? (
        <h1>Welcome User</h1>
      ) : (
        <h1>Please Login</h1>
      )}
    </div>
  );
}
```

**Output:**
```
Welcome User
```

## 14. What is React Router?

**Answer:**

React Router is a routing library used in React applications to navigate between different pages or views without reloading the entire webpage.

It is commonly used to build single-page applications.

**Example:**

```jsx
import {
  BrowserRouter,
  Routes,
  Route
} from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<h1>Home Page</h1>} />
        <Route path="/about" element={<h1>About Page</h1>} />
        <Route path="/contact" element={<h1>Contact Page</h1>} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

**Here:**
- `/` displays the Home page.
- `/about` displays the About page.
- `/contact` displays the Contact page.

## 15. What is the purpose of the dependency array in useEffect?

**Answer:**

The dependency array in `useEffect` determines when the Effect should run again.

There are three common cases:

**1. Empty dependency array `[]`**

```jsx
useEffect(() => {
  console.log("Executed");
}, []);
```

Runs after the initial mount.

**2. With dependencies**

```jsx
useEffect(() => {
  console.log("Count changed");
}, [count]);
```

Runs after the initial mount and again when `count` changes.

**3. Without dependency array**

```jsx
useEffect(() => {
  console.log("Executed");
});
```

Runs after every committed render.

**Interview tip:** Remember these three cases because interviewers frequently ask about them.

## 16. What are controlled and uncontrolled components?

**Answer:**

Controlled and uncontrolled components are two ways of managing form input data in React.

| Controlled Components | Uncontrolled Components |
|---|---|
| Input value is controlled by React state. | Input value is managed by the DOM. |
| Uses `useState`. | Commonly uses `useRef`. |
| Uses the `value` prop. | Commonly uses `defaultValue`. |
| Changes are handled using `onChange`. | Value can be accessed using a ref. |
| Provides more control over form data. | Useful for simpler form handling. |

**Controlled component example:**

```jsx
import { useState } from "react";

function App() {
  const [name, setName] = useState("");

  return (
    <input
      type="text"
      value={name}
      onChange={(e) => setName(e.target.value)}
    />
  );
}
```

**Uncontrolled component example:**

```jsx
import { useRef } from "react";

function App() {
  const nameRef = useRef();

  function handleSubmit() {
    alert(nameRef.current.value);
  }

  return (
    <div>
      <input type="text" ref={nameRef} />
      <button onClick={handleSubmit}>Submit</button>
    </div>
  );
}
```

## 17. How do you call a REST API in React?

**Answer:**

We can call REST APIs in React using the Fetch API or Axios.

We commonly use `useEffect` to fetch data when a component mounts and `useState` to store the API response.

**Example using Fetch API:**

```jsx
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(response => response.json())
      .then(data => setUsers(data))
      .catch(error => console.log(error));
  }, []);

  return (
    <div>
      <h1>Users</h1>

      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </div>
  );
}

export default App;
```

**Steps:**
1. Call the API using `fetch()`.
2. Convert the response into JSON.
3. Store the data using `useState`.
4. Display the data using `map()`.
5. Handle errors using `catch()`.

## 18. What is the Fetch API?

**Answer:**

The Fetch API is a built-in JavaScript API used to make HTTP requests and communicate with servers.

It returns a Promise and supports HTTP methods such as GET, POST, PUT, PATCH, and DELETE.

**Example:**

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log(error));
```

**Advantages:**
- Built into modern browsers.
- Supports asynchronous requests.
- Uses Promises.
- Supports different HTTP methods.

**Important interview point:** Fetch does not automatically reject its Promise for HTTP error status codes like 404 or 500. We should check `response.ok`.

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
  .then(response => {
    if (!response.ok) {
      throw new Error("API request failed");
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.log(error));
```

## 19. How do you pass data from parent to child?

**Answer:**

In React, we pass data from a parent component to a child component using props.

**Example:**

```jsx
function Child(props) {
  return <h1>Hello {props.name}</h1>;
}

function Parent() {
  return (
    <div>
      <Child name="Ashfaq" />
    </div>
  );
}

export default Parent;
```

Here:
- `Parent` is the parent component.
- `Child` is the child component.
- `name` is the prop.
- The parent passes data to the child using props.

**Important:** For child-to-parent communication, we can pass a callback function from the parent to the child.

## 20. What is the purpose of keys in React lists?

**Answer:**

Keys are special attributes used to uniquely identify elements in a list.

They help React identify which items have been added, removed, or updated when rendering lists.

**Example:**

```jsx
function App() {
  const students = [
    { id: 1, name: "Ashfaq" },
    { id: 2, name: "Rahul" },
    { id: 3, name: "John" }
  ];

  return (
    <div>
      {students.map(student => (
        <h1 key={student.id}>
          {student.name}
        </h1>
      ))}
    </div>
  );
}
```

**Why are keys important?**
- Help React identify list items.
- Improve reconciliation.
- Help React update lists correctly.
- Avoid unnecessary DOM operations.

**Important:** We should use unique and stable IDs as keys instead of array indexes whenever possible.

---

# Additional Important React Concepts

| Topic | What you should know |
|---|---|
| React Fragment | Groups elements without adding an extra DOM element. |
| React.memo | Helps prevent unnecessary re-renders when props are unchanged. |
| useCallback | Memoizes function references. |
| useRef | Stores mutable values and accesses DOM elements. |
| useContext | Shares data across components without passing props through every level. |
| Prop Drilling | Passing props through multiple component levels. |
| Lifting State Up | Moving shared state to a common parent. |
| Event Handling | Handling events such as click, change, and submit. |
| Lists and Keys | Rendering arrays using `map()`. |
| SPA | Single Page Application. |

# Practical React Coding Questions

1. Create a counter application using `useState`.
2. Create a login form using controlled components.
3. Fetch users from an API and display them.
4. Display a list of students using `map()`.
5. Implement conditional rendering for login and logout.
6. Create parent and child components and pass data using props.
7. Create a search filter for a list of users.
8. Create a simple Todo application.
9. Use `useEffect` to display data when a component mounts.
10. Create a React Router application with Home, About, and Contact pages.

# Interview Preparation Advice

Since you are preparing as a fresher with Java, Spring Boot, and React.js, focus on these practical concepts:

1. How React communicates with Spring Boot REST APIs.
2. How to handle login and registration forms.
3. How to display backend data in React.
4. How to handle API errors.
5. How to pass data between components.
6. How to manage state using Hooks.

**Tip:** Understand the concepts and practice writing the code yourself rather than memorizing every answer.