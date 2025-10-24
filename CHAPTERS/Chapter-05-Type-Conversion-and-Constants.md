# Chapter 5: Type Conversion & Constants

## Overview
Learn how to convert data between different types and use constants to protect important values from accidental changes.

**Timestamps:** [00:39:11], [00:44:52]

---

## 5.1 Type Conversion

Type conversion is the process of changing a value from one data type to another.

**Timestamp:** [00:39:11]

### Why Convert Types?

User input from text boxes comes as **strings**, even if the user enters numbers:

```javascript
let age = document.getElementById("ageInput").value;  // "25" (string!)
age = age + 1;  // "251" (string concatenation, not 26)
```

---

## 5.2 Converting to Number

Use the `Number()` function to convert strings to numbers:

**Timestamp:** [00:40:26]

```javascript
let age = "25";
console.log(typeof age);  // "string"

age = Number(age);
console.log(typeof age);  // "number"
console.log(age + 1);     // 26 (correct math)
```

### Invalid Conversions Result in NaN

**Timestamp:** [00:41:35]

```javascript
let text = "pizza";
let result = Number(text);
console.log(result);  // NaN (Not a Number)
```

---

## 5.3 Converting to String

Use the `String()` function:

**Timestamp:** [00:41:56]

```javascript
let number = 123;
let text = String(number);
console.log(typeof text);  // "string"
```

---

## 5.4 Converting to Boolean

Use the `Boolean()` function:

**Timestamp:** [00:42:09]

### Truthy Values (convert to true):
- Non-empty strings: `Boolean("hello")` → `true`
- Non-zero numbers: `Boolean(42)` → `true`

**Timestamp:** [00:42:56]

### Falsy Values (convert to false):
- Empty strings: `Boolean("")` → `false`
- Zero: `Boolean(0)` → `false`
- undefined: `Boolean(undefined)` → `false`
- null: `Boolean(null)` → `false`

**Timestamp:** [00:43:35]

### Practical Use - Checking Empty Input

**Timestamp:** [00:43:48]

```javascript
let username = document.getElementById("usernameInput").value;

if (Boolean(username)) {
    console.log("Username entered");
} else {
    console.log("Please enter a username");
}

// Simplified (values are automatically converted):
if (username) {
    console.log("Username entered");
}
```

---

## 5.5 Constants (const)

**Timestamp:** [00:44:52]

Constants are variables that **cannot be changed** after they're assigned a value.

### Why Use Constants?

**Problem with `let`:**

**Timestamp:** [00:44:55]

```javascript
let PI = 3.14159;
let radius = 5;
let circumference = 2 * PI * radius;

// Later in code...
PI = 420.69;  // Oops! Accidental reassignment
// Now all calculations are wrong!
```

**Timestamp:** [00:46:36]

### Solution: Use `const`

**Timestamp:** [00:47:12]

```javascript
const PI = 3.14159;  // Protected constant
let radius = 5;
let circumference = 2 * PI * radius;

PI = 420.69;  // TypeError: Assignment to constant variable
```

**Timestamp:** [00:47:56]

---

## 5.6 Naming Convention for Constants

Use **UPPERCASE** for constants that hold primitive values (numbers, strings, booleans):

**Timestamp:** [00:47:20], [00:47:31]

```javascript
const PI = 3.14159;
const TAX_RATE = 0.07;
const MAX_USERS = 100;
const COMPANY_NAME = "TechCorp";
```

---

## 5.7 Practical Example: Circle Calculator

**Timestamp:** [00:48:22]

### HTML
```html
<body>
    <h1>Circle Calculator</h1>
    <label>Radius:</label>
    <input type="number" id="radiusInput">
    <button id="calculateBtn">Calculate</button>
    <p id="result"></p>
    
    <script src="index.js"></script>
</body>
```

### JavaScript
```javascript
const PI = 3.14159;  // Constant - cannot change

let radiusInput = document.getElementById("radiusInput");
let calculateBtn = document.getElementById("calculateBtn");
let result = document.getElementById("result");

calculateBtn.onclick = function() {
    let radius = Number(radiusInput.value);  // Convert to number
    let circumference = 2 * PI * radius;
    
    result.textContent = `Circumference: ${circumference.toFixed(2)}`;
};
```

---

## Summary

✅ **Type Conversion** - Converting between data types  
✅ `Number()` - Convert to number  
✅ `String()` - Convert to string  
✅ `Boolean()` - Convert to boolean  
✅ **Constants** - Use `const` for values that shouldn't change  
✅ **Naming** - UPPERCASE for primitive constants  
✅ **Security** - Constants prevent accidental reassignment  

---

## Practice Exercises

1. Create an age calculator that properly converts string input to numbers
2. Make a program that checks if input is empty using Boolean conversion
3. Create a constant for tax rate and calculate prices with tax
4. Build a circle calculator with area and circumference

---

## Quick Reference

```javascript
// Type Conversion
let num = Number("123");      // String to Number
let str = String(456);        // Number to String
let bool = Boolean("hello");  // To Boolean

// Constants
const PI = 3.14159;           // Cannot reassign
const MAX_SIZE = 100;
```

---

**Next: Chapter 6 - Counter Program Project**
