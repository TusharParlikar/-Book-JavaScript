# Chapters 38 & 39: ES6 Modules + Asynchronous Code

---

# Chapter 38: ES6 Modules

## Overview
ES6 modules allow you to organize code into separate files, export functionality, and import it where needed.

**Timestamp:** [07:34:19]

---

## 38.1 What are Modules?

**Timestamp:** [07:34:25]

**Modules:**
- Separate JavaScript files
- Export variables, functions, classes
- Import them into other files
- Improve code organization
- Avoid global scope pollution
- Enable code reusability

---

## 38.2 Module Setup

**Timestamp:** [07:34:50]

### HTML Setup

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ES6 Modules</title>
</head>
<body>
    <!-- type="module" is REQUIRED -->
    <script type="module" src="index.js"></script>
</body>
</html>
```

⚠️ **Important:** Must use `type="module"` attribute!

**Timestamp:** [07:35:10]

---

## 38.3 Named Exports

**Timestamp:** [07:35:30]

### mathUtils.js

```javascript
// Export individual items
export const PI = 3.14159;

export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}

export function multiply(a, b) {
    return a * b;
}

export function divide(a, b) {
    if (b === 0) {
        throw new Error("Cannot divide by zero");
    }
    return a / b;
}
```

**Timestamp:** [07:36:15]

---

## 38.4 Named Imports

**Timestamp:** [07:36:40]

### index.js

```javascript
// Import specific items
import { PI, add, subtract } from './mathUtils.js';

console.log(PI); // 3.14159
console.log(add(5, 3)); // 8
console.log(subtract(10, 4)); // 6
```

⚠️ **Important:** Include `.js` extension!

---

## 38.5 Import All with Wildcard

**Timestamp:** [07:37:25]

```javascript
// Import everything as an object
import * as MathUtils from './mathUtils.js';

console.log(MathUtils.PI); // 3.14159
console.log(MathUtils.add(5, 3)); // 8
console.log(MathUtils.multiply(4, 2)); // 8
console.log(MathUtils.divide(10, 2)); // 5
```

**Timestamp:** [07:37:50]

---

## 38.6 Export After Declaration

**Timestamp:** [07:38:10]

### userUtils.js

```javascript
// Declare first
const username = "John";

function getUser() {
    return { name: username, id: 123 };
}

function setUser(name) {
    console.log(`User set to: ${name}`);
}

// Export at the end
export { username, getUser, setUser };
```

---

## 38.7 Import with Aliases

**Timestamp:** [07:38:50]

```javascript
// Rename imports to avoid conflicts
import { add as addNumbers, multiply as multiplyNumbers } from './mathUtils.js';

console.log(addNumbers(5, 3)); // 8
console.log(multiplyNumbers(4, 2)); // 8
```

---

## 38.8 Default Exports

**Timestamp:** [07:39:35]

### calculator.js

```javascript
// Only ONE default export per file
export default class Calculator {
    add(a, b) {
        return a + b;
    }
    
    subtract(a, b) {
        return a - b;
    }
    
    multiply(a, b) {
        return a * b;
    }
    
    divide(a, b) {
        return a / b;
    }
}
```

**Timestamp:** [07:40:10]

---

## 38.9 Importing Default Exports

**Timestamp:** [07:40:25]

```javascript
// Import default export (no curly braces)
import Calculator from './calculator.js';

const calc = new Calculator();
console.log(calc.add(5, 3)); // 8
console.log(calc.multiply(4, 2)); // 8
```

Can name it whatever you want:

```javascript
import MyCalculator from './calculator.js';
import Calc from './calculator.js';
```

---

## 38.10 Mixing Default and Named Exports

**Timestamp:** [07:41:05]

### shapes.js

```javascript
// Default export
export default class Circle {
    constructor(radius) {
        this.radius = radius;
    }
    
    getArea() {
        return Math.PI * this.radius ** 2;
    }
}

// Named exports
export const PI = 3.14159;

export function getCircumference(radius) {
    return 2 * PI * radius;
}
```

### Importing Both

```javascript
// Import default and named together
import Circle, { PI, getCircumference } from './shapes.js';

const circle = new Circle(5);
console.log(circle.getArea()); // 78.54
console.log(getCircumference(5)); // 31.42
console.log(PI); // 3.14159
```

**Timestamp:** [07:42:20]

---

## 38.11 Practical Example: User Module

**Timestamp:** [07:42:50]

### user.js

```javascript
// Default export
export default class User {
    constructor(name, email) {
        this.name = name;
        this.email = email;
    }
    
    displayInfo() {
        console.log(`${this.name} (${this.email})`);
    }
}

// Named exports
export function validateEmail(email) {
    return email.includes("@");
}

export function formatUsername(name) {
    return name.trim().toLowerCase();
}
```

### main.js

```javascript
import User, { validateEmail, formatUsername } from './user.js';

const email = "john@example.com";

if (validateEmail(email)) {
    const username = formatUsername("  John Doe  ");
    const user = new User(username, email);
    user.displayInfo(); // "john doe (john@example.com)"
}
```

---

## 38.12 Module Benefits

**Timestamp:** [07:43:40]

✅ **Code Organization:** Separate concerns into files  
✅ **Reusability:** Import same module multiple times  
✅ **Maintainability:** Easier to find and fix code  
✅ **Namespace Management:** Avoid global variables  
✅ **Lazy Loading:** Load modules when needed  
✅ **Dependency Management:** Clear import/export relationships  

---

## Summary - Chapter 38

✅ Modules organize code into separate files  
✅ Use `type="module"` in HTML  
✅ **Named exports:** `export { name }`  
✅ **Named imports:** `import { name } from './file.js'`  
✅ **Default export:** `export default`  
✅ **Import all:** `import * as Name from './file.js'`  
✅ Can mix default and named exports  
✅ Use aliases to avoid name conflicts  

---

# Chapter 39: Asynchronous Code

## Overview
Understand synchronous vs asynchronous code execution, and why async is important for JavaScript.

**Timestamp:** [07:38:40]

---

## 39.1 Synchronous Code

**Timestamp:** [07:38:48]

**Synchronous = Sequential**
- Code executes line by line
- Each line waits for previous to finish
- Blocking execution

### Example

```javascript
console.log("Start");

// This takes 3 seconds
for (let i = 0; i < 3000000000; i++) {
    // Blocking operation
}

console.log("End");

// Output:
// "Start"
// ... 3 second delay ...
// "End"
```

**Problem:** Page freezes during long operations!

**Timestamp:** [07:39:15]

---

## 39.2 The Problem with Synchronous Code

**Timestamp:** [07:39:32]

```javascript
console.log("Task 1");

// Simulate slow operation (3 seconds)
function slowTask() {
    const start = Date.now();
    while (Date.now() - start < 3000) {
        // Blocks for 3 seconds
    }
    console.log("Task 2 (slow)");
}

slowTask();

console.log("Task 3");

// Output:
// "Task 1" (immediately)
// ... 3 second freeze ...
// "Task 2 (slow)"
// "Task 3"
```

❌ **Browser is unresponsive for 3 seconds!**

---

## 39.3 Asynchronous Code

**Timestamp:** [07:40:05]

**Asynchronous = Non-blocking**
- Code doesn't wait for long operations
- Other code continues executing
- Better user experience

### Example

```javascript
console.log("Start");

// Asynchronous - doesn't block
setTimeout(() => {
    console.log("After 3 seconds");
}, 3000);

console.log("End");

// Output:
// "Start" (immediately)
// "End" (immediately)
// "After 3 seconds" (after 3 seconds)
```

✅ **Page remains responsive!**

**Timestamp:** [07:40:45]

---

## 39.4 Visualizing Execution Order

**Timestamp:** [07:41:10]

### Synchronous

```javascript
console.log("1");
console.log("2");
console.log("3");

// Output: 1, 2, 3 (in order)
```

### Asynchronous

```javascript
console.log("1");

setTimeout(() => {
    console.log("2");
}, 0); // Even with 0ms delay!

console.log("3");

// Output: 1, 3, 2 (not in order!)
```

**Why?** Async operations go to task queue.

---

## 39.5 Real-World Examples

**Timestamp:** [07:41:50]

### Example 1: Loading Data

```javascript
console.log("Loading user data...");

// Simulate API call (asynchronous)
setTimeout(() => {
    console.log("User data loaded!");
    const user = { name: "John", age: 30 };
    console.log(user);
}, 2000);

console.log("Showing loading spinner...");

// Output:
// "Loading user data..."
// "Showing loading spinner..."
// ... 2 seconds later ...
// "User data loaded!"
// { name: "John", age: 30 }
```

**Timestamp:** [07:42:30]

### Example 2: Multiple Async Operations

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Timeout 1 (2s)");
}, 2000);

setTimeout(() => {
    console.log("Timeout 2 (1s)");
}, 1000);

setTimeout(() => {
    console.log("Timeout 3 (3s)");
}, 3000);

console.log("End");

// Output:
// "Start"
// "End"
// "Timeout 2 (1s)" (after 1s)
// "Timeout 1 (2s)" (after 2s)
// "Timeout 3 (3s)" (after 3s)
```

---

## 39.6 Common Async Operations

**Timestamp:** [07:43:15]

### Operations That Are Async

✅ `setTimeout()` / `setInterval()`  
✅ Fetching data from APIs  
✅ Reading files  
✅ Database queries  
✅ User interactions (clicks, keyboard)  
✅ Loading images  
✅ Animations  

### Operations That Are Sync

❌ Variable assignments  
❌ Math calculations  
❌ Console.log  
❌ Most array methods  
❌ Object manipulation  

---

## 39.7 The Event Loop

**Timestamp:** [07:43:55]

JavaScript has:
1. **Call Stack:** Executes synchronous code
2. **Task Queue:** Holds async callbacks
3. **Event Loop:** Moves tasks from queue to stack

### How It Works

```javascript
console.log("A"); // → Stack

setTimeout(() => {
    console.log("B"); // → Queue (waits)
}, 0);

console.log("C"); // → Stack

// Execution:
// 1. "A" runs from stack
// 2. setTimeout callback goes to queue
// 3. "C" runs from stack
// 4. Stack empty, "B" moves from queue to stack

// Output: A, C, B
```

**Timestamp:** [07:44:35]

---

## 39.8 Callback Functions

**Timestamp:** [07:45:03]

Most async operations use **callbacks**:

```javascript
function fetchData(callback) {
    console.log("Fetching data...");
    
    setTimeout(() => {
        const data = { name: "John", age: 30 };
        callback(data); // Call the callback with data
    }, 2000);
}

function displayData(data) {
    console.log("Data received:");
    console.log(data);
}

fetchData(displayData);

// Output:
// "Fetching data..."
// ... 2 seconds ...
// "Data received:"
// { name: "John", age: 30 }
```

---

## 39.9 Practical Comparison

**Timestamp:** [07:45:40]

### Synchronous (Blocking)

```javascript
console.log("Ordering food...");

// Blocks for 5 seconds
function cookFood() {
    const start = Date.now();
    while (Date.now() - start < 5000) {}
    return "Pizza";
}

const food = cookFood();
console.log(`Received: ${food}`);
console.log("Eating...");

// Output (after 5 second freeze):
// "Ordering food..."
// "Received: Pizza"
// "Eating..."
```

### Asynchronous (Non-blocking)

```javascript
console.log("Ordering food...");

function cookFood(callback) {
    setTimeout(() => {
        callback("Pizza");
    }, 5000);
}

cookFood((food) => {
    console.log(`Received: ${food}`);
    console.log("Eating...");
});

console.log("Doing other things while waiting...");

// Output (immediately):
// "Ordering food..."
// "Doing other things while waiting..."
// ... 5 seconds later ...
// "Received: Pizza"
// "Eating..."
```

---

## 39.10 Why Async is Important

**Timestamp:** [07:46:25]

### User Experience

✅ **Responsive UI:** Page doesn't freeze  
✅ **Better Performance:** Multiple operations at once  
✅ **Improved UX:** Loading indicators, smooth interactions  

### Real-World Scenario

```javascript
// Without async - BAD
console.log("Loading page...");
loadUserData(); // Blocks 2 seconds
loadPosts(); // Blocks 3 seconds
loadComments(); // Blocks 2 seconds
console.log("Page loaded!"); // 7 seconds later!

// With async - GOOD
console.log("Loading page...");
loadUserData(); // 2 seconds (async)
loadPosts(); // 3 seconds (async)
loadComments(); // 2 seconds (async)
console.log("Page loaded!"); // Immediately!
// Everything loads in parallel (3 seconds total)
```

---

## 39.11 Key Concepts

**Timestamp:** [07:47:10]

### Synchronous
- **Sequential execution**
- **Blocking**
- **Waits for completion**
- **Predictable order**

### Asynchronous
- **Parallel execution**
- **Non-blocking**
- **Continues without waiting**
- **Unpredictable order**

---

## Summary - Chapter 39

✅ **Synchronous:** Code runs line by line, blocking  
✅ **Asynchronous:** Code doesn't wait, non-blocking  
✅ Async improves user experience  
✅ Common async: setTimeout, fetch, events  
✅ Event loop manages async operations  
✅ Callbacks handle async results  
✅ Next: Promises and async/await for better async code  

---

## Practice Exercises

### Exercise 1: Module System
Create calculator module with export/import.

### Exercise 2: User Management
Build user module with CRUD operations.

### Exercise 3: Async vs Sync
Compare performance of sync vs async operations.

### Exercise 4: Callback Practice
Implement async data fetching with callbacks.

---

## Quick Reference

```javascript
// ES6 Modules

// Named Export
export const name = "value";
export function func() {}

// Named Import
import { name, func } from './file.js';

// Default Export
export default class MyClass {}

// Default Import
import MyClass from './file.js';

// Import All
import * as Utils from './file.js';

// Async Code

// Synchronous (blocking)
console.log("1");
console.log("2");
console.log("3");
// Output: 1, 2, 3

// Asynchronous (non-blocking)
console.log("1");
setTimeout(() => console.log("2"), 1000);
console.log("3");
// Output: 1, 3, 2

// Callback
function fetchData(callback) {
    setTimeout(() => {
        callback("data");
    }, 1000);
}

fetchData((data) => {
    console.log(data);
});
```

---

**Next: Chapters 40 & 41 - Error Handling + Calculator Project**
