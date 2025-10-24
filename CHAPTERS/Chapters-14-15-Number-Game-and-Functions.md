# Chapters 14 & 15: Number Guessing Game + Functions

---

# Chapter 14: Number Guessing Game Project

## Overview
Build a complete number guessing game that combines loops, conditionals, user input, and random numbers.

**Timestamp:** [02:40:38]

---

## 14.1 Project Goal

Create a game where:
- Computer generates a random number
- Player guesses the number
- Game provides feedback ("too high" or "too low")
- Counts number of attempts
- Validates user input

---

## 14.2 Setup Variables

**Timestamp:** [02:40:49], [02:41:11], [02:43:06]

```javascript
// Define the range
const minNum = 1;
const maxNum = 100;

// Generate the answer
const answer = Math.floor(Math.random() * (maxNum - minNum + 1)) + minNum;

// Game state variables
let attempts = 0;
let guess;
let running = true;
```

---

## 14.3 Main Game Loop

**Timestamp:** [02:43:35]

```javascript
while (running) {
    // Game logic here
}
```

---

## 14.4 Get User Input

**Timestamp:** [02:44:09]

```javascript
while (running) {
    guess = window.prompt(`Guess a number between ${minNum} and ${maxNum}:`);
    
    // Convert to number
    guess = Number(guess);
}
```

**Timestamp:** [02:44:59]

---

## 14.5 Input Validation

### Check for NaN

**Timestamp:** [02:45:42]

```javascript
if (isNaN(guess)) {
    window.alert("Please enter a valid number!");
    continue; // Skip rest and ask again
}
```

### Check Range

**Timestamp:** [02:46:15], [02:45:54]

```javascript
if (guess < minNum || guess > maxNum) {
    window.alert(`Please enter a number between ${minNum} and ${maxNum}!`);
    continue;
}
```

---

## 14.6 Process Valid Guess

**Timestamp:** [02:47:01], [02:47:13], [02:47:31], [02:47:45]

```javascript
// Increment attempts
attempts++;

// Check guess
if (guess < answer) {
    window.alert("Too low! Try again.");
} else if (guess > answer) {
    window.alert("Too high! Try again.");
} else {
    window.alert(`Correct! The answer was ${answer}. It took you ${attempts} attempts.`);
    running = false; // End game
}
```

---

## 14.7 Complete Game Code

```javascript
// Game setup
const minNum = 1;
const maxNum = 100;
const answer = Math.floor(Math.random() * (maxNum - minNum + 1)) + minNum;

let attempts = 0;
let guess;
let running = true;

// Main game loop
while (running) {
    // Get user input
    guess = window.prompt(`Guess a number between ${minNum} and ${maxNum}:`);
    guess = Number(guess);
    
    // Validate input - check for NaN
    if (isNaN(guess)) {
        window.alert("Please enter a valid number!");
        continue;
    }
    
    // Validate input - check range
    if (guess < minNum || guess > maxNum) {
        window.alert(`Please enter a number between ${minNum} and ${maxNum}!`);
        continue;
    }
    
    // Process valid guess
    attempts++;
    
    if (guess < answer) {
        window.alert("Too low! Try again.");
    } else if (guess > answer) {
        window.alert("Too high! Try again.");
    } else {
        window.alert(`Correct! The answer was ${answer}.\nIt took you ${attempts} attempts.`);
        running = false;
    }
}

console.log("Game Over!");
```

---

## 14.8 Enhancements

### Add Difficulty Levels

```javascript
let difficulty = window.prompt("Choose difficulty: easy, medium, hard");
let minNum, maxNum;

switch(difficulty.toLowerCase()) {
    case "easy":
        minNum = 1;
        maxNum = 50;
        break;
    case "medium":
        minNum = 1;
        maxNum = 100;
        break;
    case "hard":
        minNum = 1;
        maxNum = 1000;
        break;
    default:
        minNum = 1;
        maxNum = 100;
}
```

### Add Maximum Attempts

```javascript
const maxAttempts = 10;
let attempts = 0;

while (running && attempts < maxAttempts) {
    // Game logic
    
    if (attempts === maxAttempts) {
        window.alert(`Game Over! The answer was ${answer}.`);
        running = false;
    }
}
```

### Keep Score

```javascript
let score = 100;

while (running) {
    // ... game logic
    
    if (guess !== answer) {
        score -= 10; // Lose points for wrong guess
    }
}

console.log(`Final score: ${score}`);
```

---

## Summary - Chapter 14

✅ Combined multiple concepts: loops, conditionals, random numbers  
✅ Input validation (NaN check, range check)  
✅ User feedback system  
✅ Attempt counting  
✅ Game state management  

---

# Chapter 15: Functions

## Overview
Functions are reusable blocks of code that perform specific tasks. They help organize code and avoid repetition.

**Timestamp:** [02:49:33]

---

## 15.1 What are Functions?

**Timestamp:** [02:49:33], [02:49:41]

Functions are:
- Reusable sections of code
- Declared once, used many times
- Help organize and structure programs
- Make code more maintainable

---

## 15.2 Function Declaration

**Timestamp:** [02:49:51]

```javascript
function functionName() {
    // Code to execute
}
```

### Example: Simple Greeting

```javascript
function sayHello() {
    console.log("Hello!");
}

// Call the function
sayHello(); // Output: Hello!
sayHello(); // Output: Hello!
sayHello(); // Output: Hello!
```

---

## 15.3 Calling Functions

**Timestamp:** [02:50:44]

To execute a function, write its name followed by parentheses:

```javascript
functionName();
```

### Multiple Calls

```javascript
function greet() {
    console.log("Welcome!");
}

greet(); // Welcome!
greet(); // Welcome!
greet(); // Welcome!
```

---

## 15.4 Function Parameters

**Timestamp:** [02:52:44]

**Parameters** are variables defined in the function declaration (placeholders).

```javascript
function functionName(parameter1, parameter2) {
    // Use parameters here
}
```

### Example with Parameters

```javascript
function greet(name) {
    console.log(`Hello, ${name}!`);
}

greet("John");  // Hello, John!
greet("Sarah"); // Hello, Sarah!
greet("Mike");  // Hello, Mike!
```

---

## 15.5 Function Arguments

**Timestamp:** [02:52:39]

**Arguments** are the actual values passed when calling the function.

```javascript
function add(x, y) {  // x and y are parameters
    console.log(x + y);
}

add(5, 3);  // 5 and 3 are arguments
```

---

## 15.6 Multiple Parameters

**Timestamp:** [02:51:35]

```javascript
function happyBirthday(username, age) {
    console.log(`Happy Birthday, ${username}!`);
    console.log(`You are ${age} years old!`);
}

happyBirthday("John", 25);
// Output:
// Happy Birthday, John!
// You are 25 years old!

happyBirthday("Sarah", 30);
// Output:
// Happy Birthday, Sarah!
// You are 30 years old!
```

---

## 15.7 Parameter Order Matters

**Timestamp:** [02:53:51]

```javascript
function introduce(firstName, lastName, age) {
    console.log(`My name is ${firstName} ${lastName} and I'm ${age} years old.`);
}

introduce("John", "Doe", 25);
// My name is John Doe and I'm 25 years old.

introduce("Doe", "John", 25);
// My name is Doe John and I'm 25 years old. (Wrong!)
```

---

## 15.8 The Return Statement

**Timestamp:** [02:54:13], [02:54:53]

The `return` keyword sends a value back from the function.

```javascript
function functionName() {
    return value;
}
```

### Example: Addition Function

**Timestamp:** [02:54:23]

```javascript
function add(x, y) {
    return x + y;
}

let sum = add(5, 3);
console.log(sum); // 8
```

**Timestamp:** [02:55:08], [02:55:14]

---

## 15.9 Using Returned Values

```javascript
function multiply(a, b) {
    return a * b;
}

// Store result
let result = multiply(4, 5);
console.log(result); // 20

// Use directly
console.log(multiply(3, 7)); // 21

// Use in calculations
let total = multiply(10, 2) + 5;
console.log(total); // 25
```

---

## 15.10 More Function Examples

### Arithmetic Functions

**Timestamp:** [02:56:02]

```javascript
function subtract(x, y) {
    return x - y;
}

function multiply(x, y) {
    return x * y;
}

function divide(x, y) {
    return x / y;
}

console.log(subtract(10, 3)); // 7
console.log(multiply(4, 5));  // 20
console.log(divide(20, 4));   // 5
```

---

## 15.11 Boolean Return Functions

### Example: Check Even Number

**Timestamp:** [02:57:07]

```javascript
// Using if/else
function isEven(number) {
    if (number % 2 === 0) {
        return true;
    } else {
        return false;
    }
}

// Using ternary (cleaner)
function isEven(number) {
    return number % 2 === 0;
}

console.log(isEven(4));  // true
console.log(isEven(7));  // false
```

---

## 15.12 String Return Functions

### Example: Email Validation

**Timestamp:** [02:59:07]

```javascript
// Using if/else
function isValidEmail(email) {
    if (email.includes("@")) {
        return true;
    } else {
        return false;
    }
}

// Using ternary (cleaner)
function isValidEmail(email) {
    return email.includes("@");
}

console.log(isValidEmail("user@example.com")); // true
console.log(isValidEmail("invalid.email"));    // false
```

---

## 15.13 Functions with No Return

Functions without `return` return `undefined` by default:

```javascript
function sayHello(name) {
    console.log(`Hello, ${name}!`);
    // No return statement
}

let result = sayHello("John"); // Logs: Hello, John!
console.log(result);           // undefined
```

---

## 15.14 Default Parameters (ES6)

```javascript
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}

greet("John");  // Hello, John!
greet();        // Hello, Guest! (uses default)
```

---

## 15.15 Practical Function Examples

### Example 1: Temperature Converter

```javascript
function celsiusToFahrenheit(celsius) {
    return (celsius * 9/5) + 32;
}

function fahrenheitToCelsius(fahrenheit) {
    return (fahrenheit - 32) * 5/9;
}

console.log(celsiusToFahrenheit(0));   // 32
console.log(fahrenheitToCelsius(212)); // 100
```

### Example 2: Calculate Area

```javascript
function calculateCircleArea(radius) {
    return Math.PI * radius ** 2;
}

function calculateRectangleArea(width, height) {
    return width * height;
}

console.log(calculateCircleArea(5));        // 78.54
console.log(calculateRectangleArea(4, 6));  // 24
```

### Example 3: Find Maximum

```javascript
function findMax(a, b, c) {
    return Math.max(a, b, c);
}

console.log(findMax(10, 25, 15)); // 25
```

### Example 4: Generate Random Integer

```javascript
function getRandomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

console.log(getRandomInt(1, 6));   // Random 1-6
console.log(getRandomInt(1, 100)); // Random 1-100
```

---

## 15.16 Function Best Practices

### ✅ Do:
- Use descriptive function names (verbs)
- Keep functions small and focused
- Use parameters instead of global variables
- Return values when needed
- Add comments for complex logic

### ❌ Avoid:
- Functions that do too many things
- Overly long functions (> 20-30 lines)
- Modifying global variables
- Side effects when not needed
- Unclear or vague names

---

## 15.17 Common Function Patterns

### Pattern 1: Validation Function

```javascript
function isValidAge(age) {
    return age >= 0 && age <= 120;
}

if (isValidAge(userAge)) {
    console.log("Valid age");
}
```

### Pattern 2: Calculation Function

```javascript
function calculateDiscount(price, percentage) {
    return price * (percentage / 100);
}

let discount = calculateDiscount(100, 20); // $20
```

### Pattern 3: Format Function

```javascript
function formatCurrency(amount) {
    return `$${amount.toFixed(2)}`;
}

console.log(formatCurrency(10.5)); // $10.50
```

### Pattern 4: Utility Function

```javascript
function capitalize(text) {
    return text.charAt(0).toUpperCase() + text.slice(1).toLowerCase();
}

console.log(capitalize("hello")); // Hello
```

---

## Summary - Chapter 15

✅ **Functions** - Reusable blocks of code  
✅ **Declaration** - `function name() {}`  
✅ **Parameters** - Placeholders in declaration  
✅ **Arguments** - Actual values passed  
✅ **Return** - Send values back  
✅ Functions reduce code repetition  
✅ Make code organized and maintainable  
✅ Can return any data type  

---

## Practice Exercises

### Exercise 1: Power Function
Create a function that takes a base and exponent and returns the result.

### Exercise 2: Grade Calculator
Create a function that takes a score and returns a letter grade.

### Exercise 3: Palindrome Checker
Create a function that checks if a word reads the same backwards.

### Exercise 4: BMI Calculator
Create a function that calculates Body Mass Index from weight and height.

---

## Quick Reference

```javascript
// Function Declaration
function name(parameters) {
    // code
    return value;
}

// Function Call
name(arguments);

// With Return
function add(x, y) {
    return x + y;
}
let sum = add(5, 3);

// Without Return
function greet(name) {
    console.log(`Hello ${name}`);
}
greet("John");
```

---

**Next: Chapters 16 & 17 - Variable Scope + Temperature Conversion Project**

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Chapters 12-13: Logical Operators & Loops](Chapters-12-13-Logical-Operators-and-Loops.md) | [📑 Index](../README.md) | [Chapters 16-17: Variable Scope & Temperature ▶️](Chapters-16-17-Variable-Scope-and-Temperature-Conversion.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-14--15-number-guessing-game--functions)**

Made with ❤️ for JavaScript learners

</div>
