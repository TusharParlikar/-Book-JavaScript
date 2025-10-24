# Chapters 16 & 17: Variable Scope + Temperature Conversion Project

---

# Chapter 16: Variable Scope

## Overview
Variable scope determines where a variable is recognized and accessible in your code.

**Timestamp:** [03:00:32]

---

## 16.1 What is Scope?

**Timestamp:** [03:00:32]

**Scope** = Where a variable is recognized and accessible

Two main types:
1. **Local Scope** (inside functions)
2. **Global Scope** (outside all functions)

---

## 16.2 Local Scope

**Timestamp:** [03:00:44], [03:00:56]

Variables declared inside a function:
- Only accessible **within** that function
- Not accessible outside the function
- Exist only while the function executes

### Example

```javascript
function function1() {
    let x = 1; // Local to function1
    console.log(x); // Works! (1)
}

function function2() {
    let x = 2; // Different local variable
    console.log(x); // Works! (2)
}

function1();
function2();

console.log(x); // Error! x is not defined globally
```

**Timestamp:** [03:01:25]

---

## 16.3 Global Scope

**Timestamp:** [03:01:45]

Variables declared outside all functions:
- Accessible **anywhere** in the file
- Accessible from all functions
- Exist for the entire program lifetime

### Example

```javascript
let x = 3; // Global variable

function function1() {
    console.log(x); // Accesses global x (3)
}

function function2() {
    console.log(x); // Also accesses global x (3)
}

function1();
function2();
console.log(x); // Works! (3)
```

---

## 16.4 Local vs Global Priority

**Timestamp:** [03:02:00]

When both exist, **local scope takes priority**:

```javascript
let x = 3; // Global

function function1() {
    let x = 1; // Local (shadows the global)
    console.log(x); // Uses local x (1)
}

function function2() {
    let x = 2; // Different local
    console.log(x); // Uses local x (2)
}

function1();
function2();
console.log(x); // Uses global x (3)
```

---

## 16.5 Practical Example

**Timestamp:** [03:02:38]

```javascript
// Global scope
let userName = "Alice";

function greetUser() {
    // Local scope
    let greeting = "Hello";
    console.log(`${greeting}, ${userName}!`);
    // Can access both local (greeting) and global (userName)
}

greetUser(); // Hello, Alice!
console.log(greeting); // Error! greeting is local
```

---

## 16.6 Scope Best Practices

### ✅ Do:
- Declare variables in the smallest scope needed
- Use local variables when possible
- Use descriptive names to avoid confusion
- Minimize global variables

### ❌ Avoid:
- Excessive global variables (pollutes global scope)
- Shadowing variables unnecessarily
- Relying on global state in functions

---

## 16.7 Block Scope (let & const)

Variables declared with `let` and `const` are also block-scoped:

```javascript
if (true) {
    let x = 1;
    const y = 2;
    console.log(x, y); // 1, 2
}

console.log(x, y); // Error! Not accessible outside block
```

---

## 16.8 Function Scope (var)

`var` is function-scoped (not block-scoped):

```javascript
if (true) {
    var x = 1;
}

console.log(x); // 1 (var is accessible!)

function test() {
    var y = 2;
}

console.log(y); // Error! var is function-scoped
```

**Note:** Prefer `let` and `const` over `var`.

---

## Summary - Chapter 16

✅ **Scope** - Where variables are accessible  
✅ **Local Scope** - Inside functions only  
✅ **Global Scope** - Accessible everywhere  
✅ **Local takes priority** over global  
✅ Minimize global variables  
✅ Use `let`/`const` for block scope  

---

# Chapter 17: Temperature Conversion Project

## Overview
Build a program that converts temperatures between Celsius and Fahrenheit.

**Timestamp:** [03:03:10]

---

## 17.1 Project Goal

Create a temperature converter with:
- Radio buttons to select conversion type
- Text input for temperature value
- Submit button to perform conversion
- Display result

**Timestamp:** [03:03:10]

---

## 17.2 HTML Structure

**Timestamp:** [03:03:24], [03:03:31]

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Temperature Converter</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Temperature Converter</h1>
    
    <div id="converter">
        <!-- Radio buttons for conversion type -->
        <label>
            <input type="radio" name="unit" id="toFahrenheit" checked>
            Celsius to Fahrenheit
        </label>
        <br>
        <label>
            <input type="radio" name="unit" id="toCelsius">
            Fahrenheit to Celsius
        </label>
        <br><br>
        
        <!-- Temperature input -->
        <label>Enter Temperature:</label>
        <input type="number" id="textBox">
        <br><br>
        
        <!-- Submit button -->
        <button id="submitBtn">Submit</button>
        <br><br>
        
        <!-- Result display -->
        <p id="result"></p>
    </div>
    
    <script src="index.js"></script>
</body>
</html>
```

**Timestamp:** [03:04:02], [03:04:34], [03:04:50], [03:05:02], [03:05:31], [03:05:39]

---

## 17.3 CSS Styling (Optional)

```css
body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    margin: 0;
}

h1 {
    color: #333;
}

#converter {
    background: white;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

label {
    font-size: 16px;
    margin: 10px 0;
}

input[type="number"] {
    padding: 10px;
    font-size: 16px;
    border: 2px solid #ddd;
    border-radius: 5px;
    width: 200px;
}

button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

#result {
    font-size: 20px;
    font-weight: bold;
    color: #28a745;
}
```

---

## 17.4 JavaScript - Get HTML Elements

**Timestamp:** [03:05:51], [03:06:08], [03:06:21], [03:06:33], [03:06:42]

```javascript
// Get references to HTML elements
const textBox = document.getElementById("textBox");
const toFahrenheit = document.getElementById("toFahrenheit");
const toCelsius = document.getElementById("toCelsius");
const result = document.getElementById("result");
const submitBtn = document.getElementById("submitBtn");
```

---

## 17.5 JavaScript - Add Event Listener

**Timestamp:** [03:06:57], [03:07:03]

```javascript
// Add click event to submit button
submitBtn.addEventListener("click", convert);
```

Alternative using `onclick` in HTML:
```html
<button onclick="convert()">Submit</button>
```

---

## 17.6 JavaScript - Convert Function

**Timestamp:** [03:07:17]

```javascript
function convert() {
    // Get the input value
    let temp = Number(textBox.value);
    
    // Check which radio button is selected
    if (toFahrenheit.checked) {
        // Convert Celsius to Fahrenheit
        temp = temp * 9 / 5 + 32;
        result.textContent = temp.toFixed(1) + "°F";
    } else if (toCelsius.checked) {
        // Convert Fahrenheit to Celsius
        temp = (temp - 32) * 5 / 9;
        result.textContent = temp.toFixed(1) + "°C";
    } else {
        // No radio button selected
        result.textContent = "Please select a conversion type";
    }
}
```

**Timestamp:** [03:07:22], [03:07:38], [03:08:06], [03:08:47], [03:09:22], [03:09:45]

---

## 17.7 Step-by-Step Explanation

### Step 1: Get Input Value

**Timestamp:** [03:07:22], [03:07:38]

```javascript
let temp = Number(textBox.value);
```

- Get value from text input
- Convert to number using `Number()`

### Step 2: Check Celsius to Fahrenheit

**Timestamp:** [03:08:06]

```javascript
if (toFahrenheit.checked) {
    temp = temp * 9 / 5 + 32;
    result.textContent = temp.toFixed(1) + "°F";
}
```

**Formula:** `F = C × (9/5) + 32`

**Timestamp:** [03:08:20]

### Step 3: Check Fahrenheit to Celsius

**Timestamp:** [03:08:47], [03:09:03]

```javascript
else if (toCelsius.checked) {
    temp = (temp - 32) * 5 / 9;
    result.textContent = temp.toFixed(1) + "°C";
}
```

**Formula:** `C = (F - 32) × (5/9)`

**Timestamp:** [03:09:22]

### Step 4: Handle No Selection

**Timestamp:** [03:09:45]

```javascript
else {
    result.textContent = "Please select a conversion type";
}
```

---

## 17.8 Complete JavaScript Code

```javascript
// Get HTML elements
const textBox = document.getElementById("textBox");
const toFahrenheit = document.getElementById("toFahrenheit");
const toCelsius = document.getElementById("toCelsius");
const result = document.getElementById("result");
const submitBtn = document.getElementById("submitBtn");

// Add event listener
submitBtn.addEventListener("click", convert);

// Conversion function
function convert() {
    let temp = Number(textBox.value);
    
    if (toFahrenheit.checked) {
        // C to F
        temp = temp * 9 / 5 + 32;
        result.textContent = temp.toFixed(1) + "°F";
    } else if (toCelsius.checked) {
        // F to C
        temp = (temp - 32) * 5 / 9;
        result.textContent = temp.toFixed(1) + "°C";
    } else {
        result.textContent = "Please select a conversion type";
    }
}
```

---

## 17.9 Input Validation

Add validation to handle empty or invalid inputs:

```javascript
function convert() {
    let temp = textBox.value;
    
    // Check if input is empty
    if (temp === "") {
        result.textContent = "Please enter a temperature";
        return;
    }
    
    // Convert to number
    temp = Number(temp);
    
    // Check if input is a valid number
    if (isNaN(temp)) {
        result.textContent = "Please enter a valid number";
        return;
    }
    
    // Perform conversion
    if (toFahrenheit.checked) {
        temp = temp * 9 / 5 + 32;
        result.textContent = temp.toFixed(1) + "°F";
    } else if (toCelsius.checked) {
        temp = (temp - 32) * 5 / 9;
        result.textContent = temp.toFixed(1) + "°C";
    } else {
        result.textContent = "Please select a conversion type";
    }
}
```

---

## 17.10 Enhancements

### Add Clear Button

```html
<button id="clearBtn">Clear</button>
```

```javascript
const clearBtn = document.getElementById("clearBtn");
clearBtn.addEventListener("click", () => {
    textBox.value = "";
    result.textContent = "";
});
```

### Add Keyboard Support (Enter Key)

```javascript
textBox.addEventListener("keypress", (event) => {
    if (event.key === "Enter") {
        convert();
    }
});
```

### Add Temperature Ranges

```javascript
function convert() {
    let temp = Number(textBox.value);
    
    // Validate reasonable temperature range
    if (toFahrenheit.checked && (temp < -273.15 || temp > 1000)) {
        result.textContent = "Temperature out of reasonable range";
        return;
    }
    
    if (toCelsius.checked && (temp < -459.67 || temp > 1832)) {
        result.textContent = "Temperature out of reasonable range";
        return;
    }
    
    // ... rest of conversion logic
}
```

### Add Real-time Conversion

```javascript
textBox.addEventListener("input", convert);
toFahrenheit.addEventListener("change", convert);
toCelsius.addEventListener("change", convert);
```

---

## 17.11 Conversion Formulas Reference

### Celsius to Fahrenheit
```
F = C × (9/5) + 32
or
F = C × 1.8 + 32
```

**Examples:**
- 0°C = 32°F
- 100°C = 212°F
- -40°C = -40°F

### Fahrenheit to Celsius
```
C = (F - 32) × (5/9)
or
C = (F - 32) / 1.8
```

**Examples:**
- 32°F = 0°C
- 212°F = 100°C
- -40°F = -40°C

---

## 17.12 Key Programming Concepts Used

1. **DOM Manipulation:** `getElementById()`, `.value`, `.textContent`
2. **Event Handling:** `addEventListener("click")`
3. **Radio Buttons:** `.checked` property
4. **Conditionals:** `if...else if...else`
5. **Type Conversion:** `Number()`
6. **Number Formatting:** `.toFixed(1)`
7. **Mathematical Operations:** Arithmetic operators
8. **Input Validation:** Checking for empty/invalid values

---

## Summary - Chapter 17

✅ Built complete temperature converter  
✅ Used radio buttons for conversion type  
✅ Applied conversion formulas  
✅ Used `.checked` property  
✅ Formatted output with `.toFixed()`  
✅ Added event listeners  
✅ Input validation techniques  

---

## Practice Exercises

### Exercise 1: Kelvin Conversion
Add a third radio button to convert to/from Kelvin.
- C to K: `K = C + 273.15`
- K to C: `C = K - 273.15`

### Exercise 2: All-in-One Converter
Display all three temperature scales at once.

### Exercise 3: Distance Converter
Create similar converter for miles/kilometers.

### Exercise 4: Weight Converter
Create converter for pounds/kilograms.

---

## Quick Reference

```javascript
// Celsius to Fahrenheit
F = C * 9/5 + 32;

// Fahrenheit to Celsius
C = (F - 32) * 5/9;

// Check radio button
if (radioButton.checked) {
    // do something
}

// Format number to 1 decimal place
temp.toFixed(1);

// Get input value
let value = textBox.value;

// Display result
result.textContent = "Result";
```

---

**Next: Chapters 18 & 19 - Arrays + Spread/Rest Operators**
