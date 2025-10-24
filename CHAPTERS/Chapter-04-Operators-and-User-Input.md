# Chapter 4: Operators & User Input

## Overview
Operators are symbols that perform operations on values and variables. In this chapter, you'll learn about arithmetic operators for mathematical calculations and how to accept user input to make your programs interactive.

---

## 4.1 Arithmetic Operators

Arithmetic operators perform mathematical calculations on numeric values.

**Timestamp:** [00:25:28]

### Operands and Operators

- **Operands**: Values that operators work on
- **Operators**: Symbols that perform operations

```javascript
let x = 5 + 3;  // 5 and 3 are operands, + is the operator
```

**Timestamp:** [00:25:28]

---

## 4.2 Basic Arithmetic Operators

**Timestamp:** [00:26:16]

### Addition (+)
```javascript
let sum = 5 + 3;  // 8
```

### Subtraction (-)
```javascript
let difference = 10 - 4;  // 6
```

### Multiplication (*)
```javascript
let product = 6 * 7;  // 42
```

### Division (/)
```javascript
let quotient = 20 / 4;  // 5
```

---

## 4.3 Exponentiation Operator (**)

The exponentiation operator raises a number to a power.

**Timestamp:** [00:27:09]

```javascript
let result = 2 ** 3;  // 2³ = 8
let square = 5 ** 2;  // 5² = 25
let cube = 3 ** 3;    // 3³ = 27
```

---

## 4.4 Modulus Operator (%)

The modulus operator returns the **remainder** of a division operation.

**Timestamp:** [00:27:46]

```javascript
let remainder = 10 % 3;  // 1 (10 ÷ 3 = 3 remainder 1)
let result = 15 % 4;     // 3 (15 ÷ 4 = 3 remainder 3)
```

### Common Use Cases:

#### Check if Number is Even or Odd
```javascript
let number = 8;

if (number % 2 === 0) {
    console.log("Even");
} else {
    console.log("Odd");
}
```

#### Check Divisibility
```javascript
let num = 15;
if (num % 5 === 0) {
    console.log("Divisible by 5");
}
```

---

## 4.5 Augmented Assignment Operators

These operators combine an arithmetic operation with assignment, providing a shorthand notation.

**Timestamp:** [00:28:55]

### Addition Assignment (+=)
```javascript
let x = 10;
x += 5;  // Same as: x = x + 5 (result: 15)
```

### Subtraction Assignment (-=)
```javascript
let x = 10;
x -= 3;  // Same as: x = x - 3 (result: 7)
```

### Multiplication Assignment (*=)
```javascript
let x = 5;
x *= 2;  // Same as: x = x * 2 (result: 10)
```

### Division Assignment (/=)
```javascript
let x = 20;
x /= 4;  // Same as: x = x / 4 (result: 5)
```

### Exponentiation Assignment (**=)
```javascript
let x = 2;
x **= 3;  // Same as: x = x ** 3 (result: 8)
```

### Modulus Assignment (%=)
```javascript
let x = 10;
x %= 3;  // Same as: x = x % 3 (result: 1)
```

---

## 4.6 Increment and Decrement Operators

**Timestamp:** [00:30:19]

### Increment (++)
Increases a value by 1.

```javascript
let count = 0;
count++;  // count is now 1
count++;  // count is now 2
```

### Decrement (--)
Decreases a value by 1.

```javascript
let count = 5;
count--;  // count is now 4
count--;  // count is now 3
```

### Prefix vs Postfix

#### Postfix (count++)
```javascript
let x = 5;
let y = x++;  // y = 5, then x becomes 6
console.log(y);  // 5
console.log(x);  // 6
```

#### Prefix (++count)
```javascript
let x = 5;
let y = ++x;  // x becomes 6 first, then y = 6
console.log(y);  // 6
console.log(x);  // 6
```

---

## 4.7 Operator Precedence

When multiple operators are in an expression, they follow a specific order of operations (like PEMDAS in math).

**Timestamp:** [00:30:47]

### Order (Highest to Lowest):
1. **Parentheses** `()`
2. **Exponents** `**`
3. **Multiplication/Division/Modulus** `*` `/` `%`
4. **Addition/Subtraction** `+` `-`

### Examples:

```javascript
let result = 5 + 3 * 2;  // 11 (not 16)
// Multiplication first: 3 * 2 = 6, then 5 + 6 = 11

let result = (5 + 3) * 2;  // 16
// Parentheses first: 5 + 3 = 8, then 8 * 2 = 16

let result = 10 + 5 ** 2;  // 35
// Exponent first: 5 ** 2 = 25, then 10 + 25 = 35

let result = 20 / 4 + 3 * 2;  // 11
// 20 / 4 = 5, 3 * 2 = 6, then 5 + 6 = 11
```

---

## 4.8 Accepting User Input

Making your programs interactive by accepting user input.

**Timestamp:** [00:33:48]

---

## 4.9 Method 1: window.prompt() (Easy Way)

The `window.prompt()` method displays a dialog box that prompts the user for input.

**Timestamp:** [00:34:08]

### Syntax
```javascript
let userInput = window.prompt("Enter your name:");
```

### Example:
```javascript
let username = window.prompt("What's your name?");
console.log(`Hello, ${username}!`);
```

### Characteristics:
- **Quick and easy** for testing
- **Returns a string** (even if user enters numbers)
- **Blocking** - stops code execution until user responds
- **Not professional** for production websites

---

## 4.10 Method 2: HTML Text Box (Professional Way)

Using HTML input elements is the standard, professional way to accept user input.

**Timestamp:** [00:33:57], [00:35:26]

### HTML Setup

```html
<body>
    <label for="myText">Enter your name:</label>
    <input type="text" id="myText">
    <button id="myButton">Submit</button>
    <p id="myH1"></p>
    
    <script src="index.js"></script>
</body>
```

**Timestamp:** [00:35:56]

---

## 4.11 Understanding HTML Input Elements

### Label Element
```html
<label for="myText">Enter your name:</label>
```
- `for` attribute connects to input's `id`
- Improves accessibility
- Clicking label focuses the input

### Input Element
```html
<input type="text" id="myText">
```
- `type="text"` - Single-line text input
- `id` - Unique identifier for JavaScript

### Button Element
```html
<button id="myButton">Submit</button>
```
- Triggers an action when clicked
- Can be styled with CSS

---

## 4.12 Handling Button Clicks with JavaScript

**Timestamp:** [00:36:35]

### Step 1: Get References to Elements
```javascript
let myButton = document.getElementById("myButton");
let myText = document.getElementById("myText");
let myH1 = document.getElementById("myH1");
```

### Step 2: Add Click Event Handler
**Timestamp:** [00:36:56]

```javascript
myButton.onclick = function() {
    // Code to run when button is clicked
};
```

### Step 3: Get Input Value
**Timestamp:** [00:37:46]

```javascript
myButton.onclick = function() {
    let username = myText.value;  // Gets the text box value
    console.log(username);
};
```

### Step 4: Update HTML Content
**Timestamp:** [00:38:11]

```javascript
myButton.onclick = function() {
    let username = myText.value;
    myH1.textContent = `Hello, ${username}!`;
};
```

---

## 4.13 Complete Examples

### Example 1: Name Greeter

**HTML:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Name Greeter</title>
</head>
<body>
    <h1>Welcome!</h1>
    <label for="nameInput">Enter your name:</label>
    <input type="text" id="nameInput">
    <button id="submitBtn">Submit</button>
    <p id="greeting"></p>
    
    <script src="index.js"></script>
</body>
</html>
```

**JavaScript:**
```javascript
let submitBtn = document.getElementById("submitBtn");
let nameInput = document.getElementById("nameInput");
let greeting = document.getElementById("greeting");

submitBtn.onclick = function() {
    let username = nameInput.value;
    greeting.textContent = `Hello, ${username}! Welcome to our website.`;
};
```

---

### Example 2: Simple Calculator

**HTML:**
```html
<body>
    <h1>Simple Calculator</h1>
    
    <label for="num1">First Number:</label>
    <input type="number" id="num1"><br><br>
    
    <label for="num2">Second Number:</label>
    <input type="number" id="num2"><br><br>
    
    <button id="addBtn">Add</button>
    <button id="subtractBtn">Subtract</button>
    <button id="multiplyBtn">Multiply</button>
    <button id="divideBtn">Divide</button>
    
    <p id="result"></p>
    
    <script src="index.js"></script>
</body>
```

**JavaScript:**
```javascript
let num1 = document.getElementById("num1");
let num2 = document.getElementById("num2");
let result = document.getElementById("result");

document.getElementById("addBtn").onclick = function() {
    let sum = Number(num1.value) + Number(num2.value);
    result.textContent = `Result: ${sum}`;
};

document.getElementById("subtractBtn").onclick = function() {
    let difference = Number(num1.value) - Number(num2.value);
    result.textContent = `Result: ${difference}`;
};

document.getElementById("multiplyBtn").onclick = function() {
    let product = Number(num1.value) * Number(num2.value);
    result.textContent = `Result: ${product}`;
};

document.getElementById("divideBtn").onclick = function() {
    let quotient = Number(num1.value) / Number(num2.value);
    result.textContent = `Result: ${quotient}`;
};
```

**Note:** We use `Number()` to convert string input to numbers for arithmetic operations.

---

## Summary

In this chapter, you learned:

✅ Arithmetic operators: `+`, `-`, `*`, `/`, `**`, `%`  
✅ Augmented assignment: `+=`, `-=`, `*=`, `/=`, `**=`, `%=`  
✅ Increment/Decrement: `++`, `--`  
✅ Operator precedence (PEMDAS)  
✅ Two methods for user input:
  - `window.prompt()` for simple testing
  - HTML text boxes for professional applications  
✅ How to handle button clicks with `.onclick`  
✅ How to get input values with `.value`  

---

## Practice Exercises

### Exercise 1: Basic Math
Create variables and perform all arithmetic operations on them.

### Exercise 2: Age Calculator
Create an input for birth year and calculate the user's age.

### Exercise 3: Temperature Calculator
Accept a temperature and perform a calculation (like adding 273.15 to convert Celsius to Kelvin).

### Exercise 4: Even/Odd Checker
Create an input that accepts a number and tells the user if it's even or odd using the modulus operator.

---

## Quick Reference

### Arithmetic Operators
```javascript
+   // Addition
-   // Subtraction
*   // Multiplication
/   // Division
**  // Exponentiation
%   // Modulus (remainder)
```

### Augmented Assignment
```javascript
x += 5;   // x = x + 5
x -= 3;   // x = x - 3
x *= 2;   // x = x * 2
x /= 4;   // x = x / 4
```

### Increment/Decrement
```javascript
count++;  // Increment by 1
count--;  // Decrement by 1
```

### User Input
```javascript
// Method 1: Prompt
let name = window.prompt("Enter name:");

// Method 2: HTML Input
let input = document.getElementById("inputId");
let value = input.value;
```

---

**Continue to Chapter 5: Type Conversion & Constants**

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Chapter 3: Variables](Chapter-03-Variables.md) | [📑 Index](../README.md) | [Chapter 5: Type Conversion ▶️](Chapter-05-Type-Conversion-and-Constants.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapter-4-operators--user-input)**

Made with ❤️ for JavaScript learners

</div>
