# Chapters 6 & 7: Counter Program Project + Math Object & Random Numbers

---

# Chapter 6: Counter Program Project

## Overview
Build your first interactive JavaScript project - a counter with increment, decrement, and reset functionality.

**Timestamp:** [00:52:33]

---

## 6.1 Project Goal

Create a counter display with three interactive buttons:
- **Decrease** button (-)
- **Reset** button (0)
- **Increase** button (+)

---

## 6.2 HTML Structure

Create the layout for the counter and buttons:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Counter Program</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Counter Display -->
    <label id="countLabel">0</label>
    
    <!-- Button Container -->
    <div id="buttonContainer">
        <button class="buttons" id="decreaseBtn">Decrease</button>
        <button class="buttons" id="resetBtn">Reset</button>
        <button class="buttons" id="increaseBtn">Increase</button>
    </div>
    
    <script src="index.js"></script>
</body>
</html>
```

**Timestamps:** [00:53:04], [00:53:26], [00:54:24]

### HTML Elements Explained:
- `<label id="countLabel">` - Displays the current count value
- `<div id="buttonContainer">` - Container to organize buttons
- Three `<button>` elements with:
  - Common class `"buttons"` for shared styling
  - Unique IDs for individual JavaScript control

---

## 6.3 CSS Styling

Create an attractive, centered layout with hover effects:

```css
/* Counter Display Styling */
#countLabel {
    display: block;
    text-align: center;
    font-size: 100px;
    font-family: Arial, sans-serif;
    margin: 50px 0;
}

/* Button Container */
#buttonContainer {
    text-align: center;
}

/* Button Styling */
.buttons {
    padding: 25px 50px;
    font-size: 30px;
    color: white;
    background-color: hsl(200, 100%, 50%);
    border-radius: 10px;
    border: none;
    cursor: pointer;
    margin: 10px;
    transition: background-color 0.3s ease;
}

/* Button Hover Effect */
.buttons:hover {
    background-color: hsl(200, 100%, 40%);
}
```

**Timestamps:** [00:54:52], [00:55:48], [00:56:15], [00:57:47]

### CSS Properties Explained:
- `display: block` - Makes label take full width
- `text-align: center` - Centers content
- `font-size: 100px` - Large, visible counter
- `cursor: pointer` - Shows hand cursor on hover
- `transition` - Smooth color change animation
- `hsl()` - HSL color format (Hue, Saturation, Lightness)

---

## 6.4 JavaScript Functionality

Add interactivity to make the counter work:

```javascript
// Get element references (use const because we won't reassign them)
const decreaseBtn = document.getElementById("decreaseBtn");
const resetBtn = document.getElementById("resetBtn");
const increaseBtn = document.getElementById("increaseBtn");
const countLabel = document.getElementById("countLabel");

// Counter variable (use let because the value will change)
let count = 0;

// Increase button functionality
increaseBtn.onclick = function() {
    count++;  // Increment count by 1
    countLabel.textContent = count;  // Update display
};

// Decrease button functionality
decreaseBtn.onclick = function() {
    count--;  // Decrement count by 1
    countLabel.textContent = count;  // Update display
};

// Reset button functionality
resetBtn.onclick = function() {
    count = 0;  // Reset to zero
    countLabel.textContent = count;  // Update display
};
```

**Timestamps:** [00:58:25], [00:59:34], [00:59:47], [01:00:05], [01:00:53], [01:01:21]

---

## 6.5 Key Concepts

### const vs let
- **`const`** for element references - They won't be reassigned
- **`let`** for the counter variable - It will change

**Timestamp:** [00:59:47], [00:59:34]

### Event Handlers
Using `.onclick` to attach functions to button clicks

### DOM Manipulation
Using `.textContent` to update what's displayed on the page

---

## 6.6 How It Works

1. **Initial State**: Counter starts at 0
2. **User Clicks Increase**: 
   - `count` variable increments by 1
   - Display updates to show new value
3. **User Clicks Decrease**:
   - `count` variable decrements by 1
   - Display updates to show new value
4. **User Clicks Reset**:
   - `count` variable resets to 0
   - Display updates to show 0

---

## 6.7 Enhancements (Optional)

You can add these features to improve your counter:

### Limit Counter Range
```javascript
increaseBtn.onclick = function() {
    if (count < 100) {  // Maximum limit
        count++;
        countLabel.textContent = count;
    }
};

decreaseBtn.onclick = function() {
    if (count > -100) {  // Minimum limit
        count--;
        countLabel.textContent = count;
    }
};
```

### Color Change Based on Value
```javascript
function updateDisplay() {
    countLabel.textContent = count;
    
    if (count > 0) {
        countLabel.style.color = "green";
    } else if (count < 0) {
        countLabel.style.color = "red";
    } else {
        countLabel.style.color = "black";
    }
}

increaseBtn.onclick = function() {
    count++;
    updateDisplay();
};
```

### Step Size Option
```javascript
let step = 1;  // Change this to increment by different amounts

increaseBtn.onclick = function() {
    count += step;
    countLabel.textContent = count;
};
```

---

## Summary - Chapter 6

✅ Created a complete interactive counter program  
✅ Used HTML structure with IDs and classes  
✅ Applied CSS styling with hover effects  
✅ Implemented JavaScript event handlers  
✅ Practiced const vs let usage  
✅ Updated DOM elements dynamically  

---

# Chapter 7: Math Object & Random Numbers

## Overview
The Math object is a built-in JavaScript object that provides mathematical properties and methods for performing calculations and generating random numbers.

**Timestamp:** [01:01:45]

---

## 7.1 What is the Math Object?

The Math object contains:
- **Properties** - Mathematical constants (like π and e)
- **Methods** - Functions for calculations

**Timestamp:** [01:01:53]

```javascript
// Math is a built-in object - no need to create it
console.log(Math);  // Outputs the Math object
```

---

## 7.2 Math Object Properties

### Mathematical Constants

```javascript
console.log(Math.PI);  // 3.141592653589793
console.log(Math.E);   // 2.718281828459045 (Euler's number)
```

**Timestamp:** [01:01:54]

### Usage Example
```javascript
// Calculate circle circumference
let radius = 5;
let circumference = 2 * Math.PI * radius;
console.log(circumference);  // 31.41592653589793
```

---

## 7.3 Rounding Methods

### Math.round() - Round to Nearest Integer

**Timestamp:** [01:02:47]

```javascript
let x = 3.7;
console.log(Math.round(x));  // 4

let y = 3.4;
console.log(Math.round(y));  // 3

let z = 3.5;
console.log(Math.round(z));  // 4 (rounds up at .5)
```

### Math.floor() - Round Down

**Timestamp:** [01:03:16]

```javascript
let x = 3.9;
console.log(Math.floor(x));  // 3 (always rounds down)

let y = -3.1;
console.log(Math.floor(y));  // -4 (down on number line)
```

### Math.ceil() - Round Up

**Timestamp:** [01:03:34]

```javascript
let x = 3.1;
console.log(Math.ceil(x));  // 4 (always rounds up)

let y = -3.9;
console.log(Math.ceil(y));  // -3 (up on number line)
```

### Math.trunc() - Remove Decimal Part

**Timestamp:** [01:03:53]

```javascript
let x = 3.9;
console.log(Math.trunc(x));  // 3

let y = -3.9;
console.log(Math.trunc(y));  // -3 (just removes decimals)
```

---

## 7.4 Power and Root Methods

### Math.pow() - Exponentiation

**Timestamp:** [01:04:04]

```javascript
Math.pow(base, exponent)

console.log(Math.pow(2, 3));   // 8 (2³)
console.log(Math.pow(5, 2));   // 25 (5²)
console.log(Math.pow(2, 10));  // 1024

// Modern alternative: ** operator
console.log(2 ** 3);  // 8
```

### Math.sqrt() - Square Root

**Timestamp:** [01:04:23]

```javascript
console.log(Math.sqrt(16));   // 4
console.log(Math.sqrt(25));   // 5
console.log(Math.sqrt(2));    // 1.4142135623730951
```

### Math.log() - Natural Logarithm

**Timestamp:** [01:04:36]

```javascript
console.log(Math.log(1));     // 0
console.log(Math.log(Math.E)); // 1
console.log(Math.log(10));    // 2.302585092994046
```

---

## 7.5 Trigonometric Methods

**Timestamp:** [01:04:52]

**Important:** These methods use **radians**, not degrees!

```javascript
// Sine
console.log(Math.sin(Math.PI / 2));  // 1
console.log(Math.sin(0));             // 0

// Cosine
console.log(Math.cos(0));             // 1
console.log(Math.cos(Math.PI));       // -1

// Tangent
console.log(Math.tan(Math.PI / 4));   // 1
```

### Converting Degrees to Radians
```javascript
function toRadians(degrees) {
    return degrees * (Math.PI / 180);
}

console.log(Math.sin(toRadians(90)));  // 1
```

---

## 7.6 Absolute Value and Sign

### Math.abs() - Absolute Value

**Timestamp:** [01:05:24]

```javascript
console.log(Math.abs(-5));    // 5
console.log(Math.abs(5));     // 5
console.log(Math.abs(-3.7));  // 3.7

// Useful for finding distance
let difference = Math.abs(10 - 25);  // 15
```

### Math.sign() - Get Sign of Number

**Timestamp:** [01:05:52]

```javascript
console.log(Math.sign(-10));  // -1 (negative)
console.log(Math.sign(0));    // 0  (zero)
console.log(Math.sign(5));    // 1  (positive)

// Useful for determining direction
let direction = Math.sign(-5);  // -1 means moving left/down
```

---

## 7.7 Max and Min Methods

### Math.max() - Find Maximum

**Timestamp:** [01:06:12]

```javascript
console.log(Math.max(10, 5, 20, 15));  // 20
console.log(Math.max(3, 7, 2, 9, 1));  // 9

// With variables
let a = 50, b = 30, c = 70;
console.log(Math.max(a, b, c));  // 70
```

### Math.min() - Find Minimum

**Timestamp:** [01:06:45]

```javascript
console.log(Math.min(10, 5, 20, 15));  // 5
console.log(Math.min(3, 7, 2, 9, 1));  // 1

// Finding smallest price
let price1 = 29.99;
let price2 = 19.99;
let price3 = 39.99;
let cheapest = Math.min(price1, price2, price3);  // 19.99
```

---

## 7.8 Random Number Generation

### Math.random() - Basic Random

**Timestamp:** [01:07:24], [01:07:35]

```javascript
let random = Math.random();
console.log(random);
// Returns a decimal between 0 (inclusive) and 1 (exclusive)
// Examples: 0.7482991, 0.2341567, 0.9876543
```

**Important:** 
- Minimum: 0 (can be 0)
- Maximum: 0.999999... (never exactly 1)

---

## 7.9 Generating Random Integers

### Random Integer from 1 to 6 (Dice Roll)

**Timestamp:** [01:08:15], [01:08:30], [01:08:54]

```javascript
let dice = Math.floor(Math.random() * 6) + 1;

// Breaking it down:
// Math.random()           → 0 to 0.999...
// Math.random() * 6       → 0 to 5.999...
// Math.floor(...) 6)      → 0 to 5 (integer)
// ... + 1                 → 1 to 6
```

### Step-by-Step Example
```javascript
// Step 1: Generate random decimal
let step1 = Math.random();        // e.g., 0.7234

// Step 2: Multiply by 6
let step2 = step1 * 6;            // e.g., 4.3404

// Step 3: Round down
let step3 = Math.floor(step2);    // e.g., 4

// Step 4: Add 1
let dice = step3 + 1;             // e.g., 5

// All in one line:
let dice = Math.floor(Math.random() * 6) + 1;
```

---

## 7.10 Random Integer in Range (Min to Max)

**Timestamp:** [01:09:23]

### Formula
```javascript
Math.floor(Math.random() * (max - min + 1)) + min
```

### Function for Reusability
```javascript
function getRandomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

// Examples:
let dice = getRandomInt(1, 6);         // 1 to 6
let age = getRandomInt(18, 65);        // 18 to 65
let score = getRandomInt(0, 100);      // 0 to 100
let temperature = getRandomInt(-10, 35); // -10 to 35
```

### Why the Formula Works
```javascript
// For range 10 to 20:
let min = 10;
let max = 20;

// max - min + 1 = 20 - 10 + 1 = 11 (number of values)
// Math.random() * 11 gives 0 to 10.999...
// Math.floor() gives 0 to 10
// + min gives 10 to 20 ✓
```

---

## 7.11 Project: Random Number Generator

**Timestamp:** [01:10:23]

Build a program that rolls multiple dice when a button is clicked.

### HTML Setup

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Random Number Generator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Dice Roller</h1>
    <button id="myButton">Roll Dice</button>
    <br><br>
    <label class="myLabels" id="label1">-</label>
    <label class="myLabels" id="label2">-</label>
    <label class="myLabels" id="label3">-</label>
    
    <script src="index.js"></script>
</body>
</html>
```

**Timestamp:** [01:10:23], [01:10:43]

### CSS Styling

```css
body {
    text-align: center;
    font-family: Arial, sans-serif;
}

h1 {
    font-size: 48px;
    margin: 20px;
}

#myButton {
    padding: 20px 40px;
    font-size: 24px;
    background-color: hsl(200, 100%, 50%);
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: background-color 0.3s;
}

#myButton:hover {
    background-color: hsl(200, 100%, 40%);
}

.myLabels {
    display: inline-block;
    width: 100px;
    height: 100px;
    font-size: 72px;
    font-weight: bold;
    border: 3px solid black;
    border-radius: 10px;
    margin: 10px;
    line-height: 100px;
    background-color: white;
}
```

### JavaScript Implementation

**Timestamp:** [01:12:02], [01:12:24], [01:12:45], [01:12:52], [01:13:01], [01:13:23]

```javascript
// Get element references
const myButton = document.getElementById("myButton");
const label1 = document.getElementById("label1");
const label2 = document.getElementById("label2");
const label3 = document.getElementById("label3");

// Set dice range
const min = 1;
const max = 6;

// Variables to store random numbers
let randomNum1;
let randomNum2;
let randomNum3;

// Button click handler
myButton.onclick = function() {
    // Generate three random numbers
    randomNum1 = Math.floor(Math.random() * (max - min + 1)) + min;
    randomNum2 = Math.floor(Math.random() * (max - min + 1)) + min;
    randomNum3 = Math.floor(Math.random() * (max - min + 1)) + min;
    
    // Update label displays
    label1.textContent = randomNum1;
    label2.textContent = randomNum2;
    label3.textContent = randomNum3;
};
```

**Timestamp:** [01:14:01]

---

## 7.12 Practical Examples

### Example 1: Random Color Generator
```javascript
function getRandomColor() {
    let r = Math.floor(Math.random() * 256);  // 0-255
    let g = Math.floor(Math.random() * 256);
    let b = Math.floor(Math.random() * 256);
    return `rgb(${r}, ${g}, ${b})`;
}

document.body.style.backgroundColor = getRandomColor();
```

### Example 2: Random Array Element
```javascript
let fruits = ["Apple", "Banana", "Orange", "Mango", "Grape"];
let randomIndex = Math.floor(Math.random() * fruits.length);
let randomFruit = fruits[randomIndex];
console.log(randomFruit);
```

### Example 3: Coin Flip
```javascript
function flipCoin() {
    return Math.random() < 0.5 ? "Heads" : "Tails";
}

console.log(flipCoin());
```

### Example 4: Random Password Character
```javascript
function getRandomChar() {
    let chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
    let randomIndex = Math.floor(Math.random() * chars.length);
    return chars[randomIndex];
}

console.log(getRandomChar());
```

---

## Summary - Chapter 7

✅ Math object properties: `Math.PI`, `Math.E`  
✅ Rounding: `round()`, `floor()`, `ceil()`, `trunc()`  
✅ Power/Root: `pow()`, `sqrt()`, `log()`  
✅ Trigonometry: `sin()`, `cos()`, `tan()`  
✅ Utilities: `abs()`, `sign()`, `max()`, `min()`  
✅ Random numbers: `Math.random()`  
✅ Random integers in range  
✅ Built a dice roller project  

---

## Practice Exercises

### Exercise 1: Temperature Converter
Use `Math.round()` to create a temperature converter that displays whole numbers.

### Exercise 2: Random Quote Generator
Create an array of quotes and display a random one each time a button is clicked.

### Exercise 3: Guessing Game Setup
Generate a random number between 1 and 100 for a guessing game.

### Exercise 4: Shape Calculator
Use `Math.PI` to calculate the area and circumference of circles with different radii.

---

## Quick Reference

```javascript
// Constants
Math.PI    // 3.14159...
Math.E     // 2.71828...

// Rounding
Math.round(x)  // Nearest integer
Math.floor(x)  // Round down
Math.ceil(x)   // Round up
Math.trunc(x)  // Remove decimals

// Calculations
Math.pow(base, exp)  // Exponentiation
Math.sqrt(x)         // Square root
Math.abs(x)          // Absolute value

// Comparisons
Math.max(a, b, c)    // Maximum value
Math.min(a, b, c)    // Minimum value

// Random
Math.random()        // 0 to 0.999...
// Random integer (min to max):
Math.floor(Math.random() * (max - min + 1)) + min
```

---

**Next: Chapters 8 & 9 - Control Flow (If Statements) & Ternary/Switch Statements**
