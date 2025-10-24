# Chapters 40 & 41: Error Handling + Calculator Project

---

# Chapter 40: Error Handling

## Overview
Learn how to handle errors gracefully in JavaScript using try, catch, finally, and throw statements.

**Timestamp:** [07:45:03]

---

## 40.1 What is Error Handling?

**Timestamp:** [07:45:10]

**Error Handling:**
- Mechanism to handle runtime errors
- Prevents program from crashing
- Provides fallback behavior
- Improves user experience

**Without error handling:**
```javascript
console.log("Start");
console.lag("This will crash"); // Typo!
console.log("This never runs");

// ❌ Program stops completely
```

**With error handling:**
```javascript
console.log("Start");
try {
    console.lag("This will crash"); // Typo!
} catch(error) {
    console.log("Error caught!");
}
console.log("Program continues");

// ✅ Program continues running
```

---

## 40.2 try...catch Statement

**Timestamp:** [07:45:50]

### Syntax

```javascript
try {
    // Code that might throw an error
} catch(error) {
    // Code to handle the error
}
```

### Example

```javascript
try {
    console.log("Before error");
    console.lag("This has a typo"); // Error!
    console.log("After error"); // Never runs
} catch(error) {
    console.log("Something went wrong!");
}

// Output:
// "Before error"
// "Something went wrong!"
```

**Timestamp:** [07:46:25]

---

## 40.3 The Error Object

**Timestamp:** [07:46:45]

The `error` parameter contains information:

```javascript
try {
    console.lag("Error here");
} catch(error) {
    console.log(error); // Full error object
    console.log(error.name); // "ReferenceError"
    console.log(error.message); // "console.lag is not a function"
    console.log(error.stack); // Stack trace
}
```

**Timestamp:** [07:47:15]

---

## 40.4 finally Block

**Timestamp:** [07:47:40]

`finally` **always** executes (error or not):

```javascript
try {
    console.log("Trying...");
    // Some code
} catch(error) {
    console.log("Error!");
} finally {
    console.log("This ALWAYS runs");
}
```

### Practical Use Case

```javascript
function readFile() {
    let file;
    try {
        file = openFile("data.txt");
        // Read file
    } catch(error) {
        console.log("Error reading file");
    } finally {
        // Always close file, even if error
        if (file) {
            file.close();
        }
    }
}
```

**Timestamp:** [07:48:20]

---

## 40.5 throw Statement

**Timestamp:** [07:48:50]

Create and throw custom errors:

```javascript
function divide(a, b) {
    if (b === 0) {
        throw new Error("Cannot divide by zero!");
    }
    return a / b;
}

try {
    console.log(divide(10, 2)); // 5
    console.log(divide(10, 0)); // Throws error!
} catch(error) {
    console.log(error.message); // "Cannot divide by zero!"
}
```

**Timestamp:** [07:49:30]

---

## 40.6 Different Error Types

**Timestamp:** [07:50:05]

### ReferenceError

```javascript
try {
    console.log(nonExistentVariable);
} catch(error) {
    console.log(error.name); // "ReferenceError"
}
```

### TypeError

```javascript
try {
    null.toString();
} catch(error) {
    console.log(error.name); // "TypeError"
}
```

### RangeError

```javascript
try {
    const arr = new Array(-1); // Invalid array length
} catch(error) {
    console.log(error.name); // "RangeError"
}
```

### SyntaxError

```javascript
try {
    eval("10 +++ 5"); // Invalid syntax
} catch(error) {
    console.log(error.name); // "SyntaxError"
}
```

---

## 40.7 Custom Error Messages

**Timestamp:** [07:51:10]

```javascript
function checkAge(age) {
    if (age < 0) {
        throw new Error("Age cannot be negative!");
    }
    if (age > 150) {
        throw new Error("Age is unrealistic!");
    }
    if (typeof age !== "number") {
        throw new Error("Age must be a number!");
    }
    return "Age is valid";
}

try {
    console.log(checkAge(25)); // "Age is valid"
    console.log(checkAge(-5)); // Throws error
} catch(error) {
    console.log(`Error: ${error.message}`);
}
```

**Timestamp:** [07:52:00]

---

## 40.8 Nested try...catch

**Timestamp:** [07:52:30]

```javascript
try {
    console.log("Outer try");
    
    try {
        console.log("Inner try");
        throw new Error("Inner error");
    } catch(error) {
        console.log("Inner catch:", error.message);
        throw new Error("Re-throwing from inner");
    }
    
} catch(error) {
    console.log("Outer catch:", error.message);
}

// Output:
// "Outer try"
// "Inner try"
// "Inner catch: Inner error"
// "Outer catch: Re-throwing from inner"
```

---

## 40.9 Practical Examples

### Example 1: User Input Validation

```javascript
function validateUsername(username) {
    try {
        if (username.length < 3) {
            throw new Error("Username too short (min 3 characters)");
        }
        if (username.length > 20) {
            throw new Error("Username too long (max 20 characters)");
        }
        if (!/^[a-zA-Z0-9]+$/.test(username)) {
            throw new Error("Username can only contain letters and numbers");
        }
        
        return "Username is valid!";
        
    } catch(error) {
        return `Invalid username: ${error.message}`;
    }
}

console.log(validateUsername("ab")); // Too short
console.log(validateUsername("john123")); // Valid
console.log(validateUsername("john@123")); // Invalid characters
```

**Timestamp:** [07:53:40]

### Example 2: Safe JSON Parsing

```javascript
function safeJSONParse(jsonString) {
    try {
        return JSON.parse(jsonString);
    } catch(error) {
        console.log("Invalid JSON:", error.message);
        return null;
    }
}

const result1 = safeJSONParse('{"name": "John"}');
console.log(result1); // { name: "John" }

const result2 = safeJSONParse('invalid json');
console.log(result2); // null
```

### Example 3: API Call with Error Handling

```javascript
function fetchUserData(userId) {
    try {
        if (!userId) {
            throw new Error("User ID is required");
        }
        
        if (typeof userId !== "number") {
            throw new Error("User ID must be a number");
        }
        
        // Simulate API call
        console.log(`Fetching data for user ${userId}...`);
        
        // Simulate success
        return { id: userId, name: "John Doe" };
        
    } catch(error) {
        console.error(`Error fetching user: ${error.message}`);
        return null;
        
    } finally {
        console.log("Cleanup: Closing connection");
    }
}

const user1 = fetchUserData(123);
console.log(user1);

const user2 = fetchUserData("abc"); // Error
console.log(user2);
```

**Timestamp:** [07:55:10]

---

## Summary - Chapter 40

✅ **try:** Execute code that might fail  
✅ **catch:** Handle errors  
✅ **finally:** Always executes (cleanup)  
✅ **throw:** Create custom errors  
✅ Error object has name, message, stack  
✅ Multiple error types: Reference, Type, Range, Syntax  
✅ Improves program stability  

---

# Chapter 41: Calculator Project

## Overview
Build a functional calculator using HTML, CSS, and JavaScript with error handling.

**Timestamp:** [07:56:16]

---

## 41.1 Project Setup

**Timestamp:** [07:56:25]

### HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="calculator">
        <input type="text" id="display" disabled>
        
        <div id="keys">
            <button class="operator" data-key="clear">C</button>
            <button class="operator" data-key="delete">←</button>
            <button class="operator" data-key="/">/</button>
            <button class="operator" data-key="*">×</button>
            
            <button data-key="7">7</button>
            <button data-key="8">8</button>
            <button data-key="9">9</button>
            <button class="operator" data-key="-">-</button>
            
            <button data-key="4">4</button>
            <button data-key="5">5</button>
            <button data-key="6">6</button>
            <button class="operator" data-key="+">+</button>
            
            <button data-key="1">1</button>
            <button data-key="2">2</button>
            <button data-key="3">3</button>
            <button class="equal" data-key="=" id="equals">=</button>
            
            <button class="zero" data-key="0">0</button>
            <button data-key=".">.</button>
        </div>
    </div>
    
    <script src="index.js"></script>
</body>
</html>
```

**Timestamp:** [07:57:40]

---

## 41.2 CSS Styling

**Timestamp:** [07:58:15]

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

#calculator {
    background: rgba(255, 255, 255, 0.1);
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
    backdrop-filter: blur(10px);
}

#display {
    width: 100%;
    height: 80px;
    font-size: 36px;
    text-align: right;
    padding: 20px;
    margin-bottom: 20px;
    border: none;
    border-radius: 10px;
    background: rgba(255, 255, 255, 0.9);
    color: #333;
    font-weight: bold;
}

#keys {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

button {
    height: 70px;
    font-size: 24px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-weight: bold;
    transition: all 0.3s ease;
    background: rgba(255, 255, 255, 0.9);
    color: #333;
}

button:hover {
    background: rgba(255, 255, 255, 1);
    transform: scale(1.05);
}

button:active {
    transform: scale(0.95);
}

.operator {
    background: #ff9500;
    color: white;
}

.operator:hover {
    background: #cc7700;
}

.equal {
    background: #4CAF50;
    color: white;
    grid-row: span 2;
}

.equal:hover {
    background: #45a049;
}

.zero {
    grid-column: span 2;
}
```

**Timestamp:** [08:00:30]

---

## 41.3 JavaScript - Basic Structure

**Timestamp:** [08:01:15]

```javascript
const display = document.getElementById("display");
const buttons = document.querySelectorAll("button");

let currentInput = "";
let previousInput = "";
let operator = "";

// Add click listeners to all buttons
buttons.forEach(button => {
    button.addEventListener("click", () => {
        const key = button.dataset.key;
        handleInput(key);
    });
});
```

**Timestamp:** [08:02:00]

---

## 41.4 Handle Input Function

**Timestamp:** [08:02:30]

```javascript
function handleInput(key) {
    if (key >= "0" && key <= "9" || key === ".") {
        // Number or decimal
        appendNumber(key);
    } else if (key === "+" || key === "-" || key === "*" || key === "/") {
        // Operator
        setOperator(key);
    } else if (key === "=") {
        // Calculate
        calculate();
    } else if (key === "clear") {
        // Clear all
        clearDisplay();
    } else if (key === "delete") {
        // Delete last character
        deleteLast();
    }
}
```

---

## 41.5 Append Number Function

**Timestamp:** [08:03:15]

```javascript
function appendNumber(number) {
    // Prevent multiple decimal points
    if (number === "." && currentInput.includes(".")) {
        return;
    }
    
    currentInput += number;
    display.value = currentInput;
}
```

**Timestamp:** [08:03:50]

---

## 41.6 Set Operator Function

**Timestamp:** [08:04:20]

```javascript
function setOperator(op) {
    if (currentInput === "") return;
    
    if (previousInput !== "") {
        calculate();
    }
    
    operator = op;
    previousInput = currentInput;
    currentInput = "";
}
```

---

## 41.7 Calculate Function

**Timestamp:** [08:05:05]

```javascript
function calculate() {
    if (previousInput === "" || currentInput === "" || operator === "") {
        return;
    }
    
    let result;
    const prev = parseFloat(previousInput);
    const current = parseFloat(currentInput);
    
    switch(operator) {
        case "+":
            result = prev + current;
            break;
        case "-":
            result = prev - current;
            break;
        case "*":
            result = prev * current;
            break;
        case "/":
            if (current === 0) {
                display.value = "Error";
                resetCalculator();
                return;
            }
            result = prev / current;
            break;
        default:
            return;
    }
    
    currentInput = result.toString();
    operator = "";
    previousInput = "";
    display.value = result;
}
```

**Timestamp:** [08:06:40]

---

## 41.8 Clear and Delete Functions

**Timestamp:** [08:07:10]

```javascript
function clearDisplay() {
    currentInput = "";
    previousInput = "";
    operator = "";
    display.value = "";
}

function deleteLast() {
    currentInput = currentInput.slice(0, -1);
    display.value = currentInput;
}

function resetCalculator() {
    setTimeout(() => {
        clearDisplay();
    }, 1500);
}
```

---

## 41.9 Complete Code with Error Handling

**Timestamp:** [08:07:50]

```javascript
const display = document.getElementById("display");
const buttons = document.querySelectorAll("button");

let currentInput = "";
let previousInput = "";
let operator = "";

// Event listeners
buttons.forEach(button => {
    button.addEventListener("click", () => {
        const key = button.dataset.key;
        handleInput(key);
    });
});

// Handle keyboard input
document.addEventListener("keydown", (e) => {
    if (e.key >= "0" && e.key <= "9" || e.key === ".") {
        handleInput(e.key);
    } else if (e.key === "+" || e.key === "-" || e.key === "*" || e.key === "/") {
        handleInput(e.key);
    } else if (e.key === "Enter" || e.key === "=") {
        handleInput("=");
    } else if (e.key === "Backspace") {
        handleInput("delete");
    } else if (e.key === "Escape") {
        handleInput("clear");
    }
});

function handleInput(key) {
    try {
        if (key >= "0" && key <= "9" || key === ".") {
            appendNumber(key);
        } else if (key === "+" || key === "-" || key === "*" || key === "/") {
            setOperator(key);
        } else if (key === "=") {
            calculate();
        } else if (key === "clear") {
            clearDisplay();
        } else if (key === "delete") {
            deleteLast();
        }
    } catch(error) {
        display.value = "Error";
        console.error("Calculation error:", error);
        resetCalculator();
    }
}

function appendNumber(number) {
    if (number === "." && currentInput.includes(".")) {
        return;
    }
    
    if (currentInput.length >= 15) {
        return; // Limit input length
    }
    
    currentInput += number;
    display.value = currentInput;
}

function setOperator(op) {
    if (currentInput === "") return;
    
    if (previousInput !== "") {
        calculate();
    }
    
    operator = op;
    previousInput = currentInput;
    currentInput = "";
}

function calculate() {
    if (previousInput === "" || currentInput === "" || operator === "") {
        return;
    }
    
    try {
        let result;
        const prev = parseFloat(previousInput);
        const current = parseFloat(currentInput);
        
        if (isNaN(prev) || isNaN(current)) {
            throw new Error("Invalid number");
        }
        
        switch(operator) {
            case "+":
                result = prev + current;
                break;
            case "-":
                result = prev - current;
                break;
            case "*":
                result = prev * current;
                break;
            case "/":
                if (current === 0) {
                    throw new Error("Cannot divide by zero");
                }
                result = prev / current;
                break;
            default:
                throw new Error("Invalid operator");
        }
        
        // Round to avoid floating point errors
        result = Math.round(result * 100000000) / 100000000;
        
        currentInput = result.toString();
        operator = "";
        previousInput = "";
        display.value = result;
        
    } catch(error) {
        display.value = "Error";
        console.error("Calculation error:", error.message);
        resetCalculator();
    }
}

function clearDisplay() {
    currentInput = "";
    previousInput = "";
    operator = "";
    display.value = "";
}

function deleteLast() {
    currentInput = currentInput.slice(0, -1);
    display.value = currentInput;
}

function resetCalculator() {
    setTimeout(() => {
        clearDisplay();
    }, 1500);
}
```

**Timestamp:** [08:09:25]

---

## 41.10 Features Implemented

✅ Basic operations: +, -, ×, ÷  
✅ Decimal numbers  
✅ Clear button (C)  
✅ Delete button (←)  
✅ Keyboard support  
✅ Error handling (division by zero)  
✅ Input length limit  
✅ Floating point rounding  

---

## Summary - Chapter 41

✅ Built functional calculator with HTML/CSS/JS  
✅ Implemented basic arithmetic operations  
✅ Added error handling for edge cases  
✅ Division by zero protection  
✅ Keyboard and mouse input  
✅ Clean, modern UI design  
✅ Proper state management  

---

## Practice Exercises

### Exercise 1: Add Memory Functions
Implement M+, M-, MR, MC buttons.

### Exercise 2: Add History
Display calculation history.

### Exercise 3: Scientific Calculator
Add sqrt, pow, sin, cos, tan functions.

### Exercise 4: Theme Switcher
Add light/dark mode toggle.

---

## Quick Reference

```javascript
// Error Handling
try {
    // Risky code
} catch(error) {
    // Handle error
} finally {
    // Always runs
}

// Throw error
throw new Error("Custom message");

// Calculator Pattern
let currentInput = "";
let previousInput = "";
let operator = "";

function calculate() {
    const a = parseFloat(previousInput);
    const b = parseFloat(currentInput);
    let result;
    
    switch(operator) {
        case "+": result = a + b; break;
        case "-": result = a - b; break;
        case "*": result = a * b; break;
        case "/": 
            if (b === 0) throw new Error("Div by 0");
            result = a / b; 
            break;
    }
    
    return result;
}
```

---

**Next: Chapters 42 & 43 - DOM Introduction + DOM Selectors**
