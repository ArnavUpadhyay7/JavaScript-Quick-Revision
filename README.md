# JavaScript Quick Revision

* **Execution Context** - JavaScript executes code in two phases:

  → **Memory Phase (Creation Phase)**
  Variables are stored in memory.
  `var` is initialized with `undefined`, and functions store their complete code in memory.

  → **Code Phase (Execution Phase)**
  Code runs line by line, variables get actual values, and function calls create a new execution context inside the call stack.

---

* **Call Stack** - A stack where function execution contexts are stored when functions are called and removed after execution is completed.

---

* **Web APIs** - Features provided by the browser like `setTimeout`, `fetch`, DOM events, etc. They work outside the JavaScript engine.

---

* **Callback Queue** - Completed async tasks like `setTimeout` callbacks are pushed here and wait for execution.

---

* **Microtask Queue** - Promise callbacks (`.then`, `catch`, `finally`) are pushed here.
  It has higher priority than the callback queue.

---

* **Event Loop** - Checks whether the call stack is empty.
  First pushes tasks from the microtask queue into the stack, then processes the callback queue.

---

* **Starvation of Callback Queue** - If microtasks keep creating more microtasks continuously, tasks waiting in the callback queue may never get a chance to execute.

---

* **`var` vs `let` vs `const`**

  * `var` → can be re-declared and updated
  * `let` → cannot be re-declared but can be updated
  * `const` → cannot be re-declared or updated

---

* **Hoisting** - Variables and functions are moved to memory before execution starts.

  * `var` is hoisted and initialized with `undefined`
  * `let` and `const` are hoisted too, but cannot be accessed before declaration

---

* **Temporal Dead Zone (TDZ)** - The time between entering a scope and declaring a `let` or `const` variable.
  Accessing the variable during this time throws a ReferenceError.

---

* **Lexical Environment** - Combination of:

  * Local variables/functions inside the current scope
  * Reference to its parent scope

---

* **Scope Chaining** - If JavaScript cannot find a variable in the current scope, it searches in the parent scope chain.

---

* **Closures** - A function bundled together with access to its lexical environment, even after the parent function has finished execution.

---

* **First-Class Functions** - Functions are treated like normal values in JavaScript.
  They can be stored in variables, passed as arguments, and returned from functions.

---

* **Higher-Order Functions** - Functions that take other functions as arguments or return functions.

---

* **Callback Functions** - Functions passed into another function to be executed later.

```js
const fn = () => console.log("hi");

setTimeout(fn, 1000);
```

Here:

* `setTimeout` → Higher-order function
* `fn` → Callback function

---

* JavaScript supports first-class functions → which enables higher-order functions → which use callback functions.

---

* **Callback Hell** - Deep nesting of callbacks when async tasks depend on each other, making code difficult to read and maintain.

---

* **Inversion of Control** - In callback-based code, we hand over control of our function execution to another function/library.

---

* **Promise** - An object representing the eventual success or failure of an asynchronous operation.

---

* **Async/Await** - Cleaner syntax for handling promises.

  * `async` functions always return a Promise
  * `await` pauses execution until the Promise resolves

---

* **Debouncing** - Delays function execution until the user stops triggering the event for a certain time.

  Example:

  * Search input suggestions

---

* **Throttling** - Limits a function to run only once within a fixed time interval.

  Example:

  * Scroll events

---

# Important JavaScript Topics

* **`this` Keyword** - Refers to the object that is calling the function.

```js
const user = {
  name: "Arnav",
  greet() {
    console.log(this.name);
  }
};

user.greet();
```

Here, `this` refers to `user`.

---

* **`map()`** - Creates a new array by transforming each element.

```js
const nums = [1, 2, 3];

const doubled = nums.map(n => n * 2);
```

---

* **`filter()`** - Creates a new array containing only elements that pass a condition.

```js
const nums = [1, 2, 3, 4];

const even = nums.filter(n => n % 2 === 0);
```

---

* **`reduce()`** - Reduces an array into a single value.

```js
const nums = [1, 2, 3];

const sum = nums.reduce((acc, curr) => acc + curr, 0);
```

---

* **Shallow Copy vs Deep Copy**

  * **Shallow Copy** → Copies only the first level. Nested objects still share references.
  * **Deep Copy** → Completely independent copy including nested objects.

---

* **Event Bubbling** - Event moves from child element to parent element.

---

* **Event Capturing** - Event moves from parent element to child element.

---

* **Prototype / Prototypal Inheritance** - Objects in JavaScript can inherit properties and methods from other objects through prototypes.

---

* **`localStorage` vs `sessionStorage` vs Cookies**

| Feature            | localStorage | sessionStorage   | Cookies          |
| ------------------ | ------------ | ---------------- | ---------------- |
| Storage Limit      | ~5MB         | ~5MB             | ~4KB             |
| Expiry             | Permanent    | Until tab closes | Can expire       |
| Accessible From    | Browser      | Browser tab only | Browser + Server |
| Sent with Requests | No           | No               | Yes              |

---
