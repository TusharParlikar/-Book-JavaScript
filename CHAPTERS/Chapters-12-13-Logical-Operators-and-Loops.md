# Chapters 12 & 13: Logical Operators & Loops

---

# Chapter 12: Logical Operators & Strict Equality

## Overview
Logical operators allow you to combine or manipulate boolean values in conditions. This chapter also covers the important difference between loose and strict equality.

**Timestamp:** [02:17:02]

---

## 12.1 What are Logical Operators?

**Timestamp:** [02:17:10]

Logical operators work with boolean values (`true`/`false`) to create more complex conditions.

**Three Main Operators:**
- `&&` - AND
- `||` - OR
- `!` - NOT

---

## 12.2 The AND (&&) Operator

**Timestamp:** [02:18:57]

Returns `true` only if **BOTH** operands are `true`.

```javascript
console.log(true && true);    // true
console.log(true && false);   // false
console.log(false && true);   // false
console.log(false && false);  // false
```

### Practical Example: Temperature Range Check

**Timestamp:** [02:18:47]

```javascript
let temp = 25;

if (temp > 0 && temp <= 30) {
    console.log("The weather is good");
}

// Both conditions must be true:
// temp > 0 (true) AND temp <= 30 (true) = true
```

### Multiple AND Conditions

```javascript
let age = 25;
let hasLicense = true;
let hasInsurance = true;

if (age >= 18 && hasLicense && hasInsurance) {
    console.log("You can drive");
}
```

---

## 12.3 The OR (||) Operator

**Timestamp:** [02:19:55]

Returns `true` if **AT LEAST ONE** operand is `true`.

```javascript
console.log(true || true);    // true
console.log(true || false);   // true
console.log(false || true);   // true
console.log(false || false);  // false
```

### Practical Example: Bad Weather Check

**Timestamp:** [02:20:26]

```javascript
let temp = -5;

if (temp <= 0 || temp > 30) {
    console.log("The weather is bad");
}

// Either condition being true makes it true:
// temp <= 0 (true) OR temp > 30 (false) = true
```

### Multiple OR Conditions

```javascript
let day = "Saturday";

if (day === "Saturday" || day === "Sunday") {
    console.log("It's the weekend!");
}
```

---

## 12.4 The NOT (!) Operator

**Timestamp:** [02:21:03]

Inverts a boolean value: `true` becomes `false`, `false` becomes `true`.

```javascript
console.log(!true);   // false
console.log(!false);  // true

let online = false;
console.log(!online); // true
```

### Practical Example: Check if NOT Sunny

**Timestamp:** [02:21:47]

```javascript
let isSunny = false;

if (!isSunny) {
    console.log("It's cloudy");
}

// !isSunny means "if NOT sunny"
// !false = true, so the code runs
```

### NOT with Comparisons

```javascript
let age = 15;

if (!(age >= 18)) {
    console.log("You are a minor");
}
// Same as: if (age < 18)
```

---

## 12.5 Combining Logical Operators

You can combine multiple logical operators:

```javascript
let age = 25;
let citizen = true;
let criminal = false;

if (age >= 18 && citizen && !criminal) {
    console.log("You can vote");
}
```

### Complex Condition Example

```javascript
let temp = 25;
let isRaining = false;
let isWindy = true;

if ((temp >= 20 && temp <= 30) && !isRaining && !isWindy) {
    console.log("Perfect weather for a picnic!");
} else {
    console.log("Stay inside");
}
```

---

## 12.6 Operator Precedence with Logical Operators

Order of operations:
1. `!` (NOT) - Highest priority
2. `&&` (AND)
3. `||` (OR) - Lowest priority

```javascript
let result = true || false && false;
// && evaluated first: false && false = false
// Then ||: true || false = true
console.log(result); // true

// Use parentheses for clarity
let result = (true || false) && false;
console.log(result); // false
```

---

## 12.7 Short-Circuit Evaluation

Logical operators use "short-circuit" evaluation:

### AND (&&) Short-Circuit
```javascript
// If first is false, second isn't checked
let result = false && expensiveFunction();
// expensiveFunction() never runs!

// Practical use
let user = null;
let name = user && user.name; // Doesn't error, returns null
```

### OR (||) Short-Circuit
```javascript
// If first is true, second isn't checked
let result = true || expensiveFunction();
// expensiveFunction() never runs!

// Default values
let username = userInput || "Guest";
```

---

## 12.8 Equality Operators

**Timestamp:** [02:22:47]

### Assignment vs Comparison

**Timestamp:** [02:22:54]

```javascript
let x = 5;      // = is assignment
let y = x == 5; // == is comparison
```

---

## 12.9 Loose Equality (==)

**Timestamp:** [02:23:00]

Compares values with **type coercion** (converts types if different).

```javascript
console.log(5 == "5");     // true (string converted to number)
console.log(1 == true);    // true (true converted to 1)
console.log(0 == false);   // true (false converted to 0)
console.log(null == undefined); // true
```

**Problem:** Can lead to unexpected results!

---

## 12.10 Strict Equality (===)

**Timestamp:** [02:23:06]

Compares values **AND data types**. No type coercion.

```javascript
console.log(5 === "5");    // false (different types)
console.log(1 === true);   // false (different types)
console.log(0 === false);  // false (different types)
console.log(null === undefined); // false

console.log(5 === 5);      // true (same type and value)
console.log("hi" === "hi"); // true
```

**Recommended:** Always use `===` for clarity and safety!

**Timestamp:** [02:26:27]

---

## 12.11 Inequality Operators

### Loose Inequality (!=)

**Timestamp:** [02:25:09]

```javascript
console.log(5 != "5");     // false (values are equal after coercion)
console.log(5 != 6);       // true
```

### Strict Inequality (!==)

**Timestamp:** [02:25:46]

```javascript
console.log(5 !== "5");    // true (different types)
console.log(5 !== 5);      // false (same type and value)
console.log(5 !== 6);      // true
```

---

## 12.12 Practical Examples

### Example 1: Login Validation
```javascript
let username = "admin";
let password = "12345";

if (username === "admin" && password === "12345") {
    console.log("Login successful");
} else {
    console.log("Invalid credentials");
}
```

### Example 2: Age and License Check
```javascript
let age = 20;
let hasLicense = true;

if (age >= 18 && hasLicense) {
    console.log("You can rent a car");
} else if (age >= 18 && !hasLicense) {
    console.log("You need a license first");
} else {
    console.log("You're too young");
}
```

### Example 3: Weekend or Holiday
```javascript
let day = "Saturday";
let isHoliday = false;

if (day === "Saturday" || day === "Sunday" || isHoliday) {
    console.log("No work today!");
} else {
    console.log("It's a work day");
}
```

### Example 4: Temperature Range with Warnings
```javascript
let temp = -5;

if (temp < -20) {
    console.log("Extreme cold warning!");
} else if (temp >= -20 && temp < 0) {
    console.log("It's freezing");
} else if (temp >= 0 && temp <= 25) {
    console.log("Pleasant weather");
} else if (temp > 25 && temp <= 35) {
    console.log("It's hot");
} else {
    console.log("Extreme heat warning!");
}
```

---

## Summary - Chapter 12

✅ **Logical Operators**: `&&` (AND), `||` (OR), `!` (NOT)  
✅ **AND (&&)** - Both conditions must be true  
✅ **OR (||)** - At least one condition must be true  
✅ **NOT (!)** - Inverts boolean value  
✅ **Loose Equality (==)** - Allows type coercion  
✅ **Strict Equality (===)** - No type coercion (recommended)  
✅ **Inequality**: `!=` (loose), `!==` (strict)  
✅ Short-circuit evaluation for efficiency  

---

# Chapter 13: Loops - While & For

## Overview
Loops allow you to repeat code multiple times. This chapter covers while loops, do-while loops, and for loops.

---

## 13.1 While Loops

**Timestamp:** [02:26:42]

While loops repeat code **while** a condition is `true`.

**Timestamp:** [02:26:46]

### Basic Syntax

```javascript
while (condition) {
    // Code to repeat
}
```

### Example: Count to 10

```javascript
let count = 1;

while (count <= 10) {
    console.log(count);
    count++;
}
```

---

## 13.2 Infinite Loops (DANGER!)

**Timestamp:** [02:27:16]

If the condition never becomes `false`, the loop runs forever!

```javascript
// DON'T RUN THIS!
let count = 1;
while (count <= 10) {
    console.log(count);
    // Forgot to increment! Infinite loop!
}
```

**Solution:** Always ensure the condition will eventually be false.

**Timestamp:** [02:28:16]

---

## 13.3 User Input Validation with While

**Timestamp:** [02:28:21]

```javascript
let username = "";

while (username === "" || username === null) {
    username = window.prompt("Enter your name:");
}

console.log(`Hello ${username}!`);
```

This keeps asking until the user provides valid input.

---

## 13.4 Do-While Loops

**Timestamp:** [02:30:03]

Do-while loops execute code **at least once**, then check the condition.

### Syntax

**Timestamp:** [02:30:03]

```javascript
do {
    // Code executes first
} while (condition);
```

### Difference from While

**Timestamp:** [02:30:16]

```javascript
// While loop - might not run at all
let num = 10;
while (num < 5) {
    console.log(num); // Never runs
}

// Do-while - runs at least once
do {
    console.log(num); // Runs once, prints 10
} while (num < 5);
```

---

## 13.5 Practical Do-While Example

**Timestamp:** [02:30:31], [02:31:09]

```javascript
let username;
let password;
let loggedIn = false;

do {
    username = window.prompt("Enter username:");
    password = window.prompt("Enter password:");
    
    if (username === "admin" && password === "1234") {
        loggedIn = true;
        console.log("Login successful!");
    } else {
        console.log("Invalid credentials. Try again.");
    }
} while (!loggedIn);

console.log("Welcome!");
```

---

## 13.6 For Loops

**Timestamp:** [02:34:54]

For loops repeat code a **specific number of times**.

**Timestamp:** [02:34:54]

### Syntax

**Timestamp:** [02:35:16]

```javascript
for (initialization; condition; finalExpression) {
    // Code to repeat
}
```

### Components:

**Timestamp:** [02:35:22], [02:35:46], [02:36:04]

1. **Initialization** - Runs once before loop starts
2. **Condition** - Checked before each iteration
3. **Final Expression** - Runs after each iteration

---

## 13.7 Basic For Loop Examples

### Count 1 to 10

**Timestamp:** [02:37:08]

```javascript
for (let i = 1; i <= 10; i++) {
    console.log(i);
}
// Output: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
```

### Count Down

**Timestamp:** [02:37:45]

```javascript
for (let i = 10; i >= 1; i--) {
    console.log(i);
}
// Output: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

---

## 13.8 Changing the Step Size

**Timestamp:** [02:37:22]

### Count by 2s

```javascript
for (let i = 0; i <= 20; i += 2) {
    console.log(i);
}
// Output: 0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20
```

### Count Down by 3s

```javascript
for (let i = 30; i >= 0; i -= 3) {
    console.log(i);
}
// Output: 30, 27, 24, 21, 18, 15, 12, 9, 6, 3, 0
```

---

## 13.9 The Continue Statement

**Timestamp:** [02:38:34]

`continue` skips the rest of the current iteration and moves to the next.

```javascript
for (let i = 1; i <= 10; i++) {
    if (i === 5) {
        continue; // Skip 5
    }
    console.log(i);
}
// Output: 1, 2, 3, 4, 6, 7, 8, 9, 10 (no 5!)
```

### Skip Even Numbers

```javascript
for (let i = 1; i <= 20; i++) {
    if (i % 2 === 0) {
        continue; // Skip even numbers
    }
    console.log(i); // Only odd numbers print
}
```

---

## 13.10 The Break Statement

**Timestamp:** [02:39:53]

`break` exits the loop entirely.

```javascript
for (let i = 1; i <= 10; i++) {
    if (i === 5) {
        break; // Stop loop at 5
    }
    console.log(i);
}
// Output: 1, 2, 3, 4 (stops before 5)
```

### Search and Stop

```javascript
let found = false;

for (let i = 1; i <= 100; i++) {
    if (i === 42) {
        console.log("Found it!");
        found = true;
        break;
    }
}

if (!found) {
    console.log("Not found");
}
```

---

## 13.11 Nested Loops

Loops inside loops for multi-dimensional operations:

```javascript
// Multiplication table
for (let i = 1; i <= 5; i++) {
    for (let j = 1; j <= 5; j++) {
        console.log(`${i} x ${j} = ${i * j}`);
    }
}
```

### Pattern Printing

```javascript
for (let i = 1; i <= 5; i++) {
    let row = "";
    for (let j = 1; j <= i; j++) {
        row += "*";
    }
    console.log(row);
}
// Output:
// *
// **
// ***
// ****
// *****
```

---

## 13.12 Practical Loop Examples

### Example 1: Sum of Numbers

```javascript
let sum = 0;

for (let i = 1; i <= 100; i++) {
    sum += i;
}

console.log(`Sum: ${sum}`); // 5050
```

### Example 2: Factorial

```javascript
let num = 5;
let factorial = 1;

for (let i = 1; i <= num; i++) {
    factorial *= i;
}

console.log(`${num}! = ${factorial}`); // 120
```

### Example 3: FizzBuzz

```javascript
for (let i = 1; i <= 30; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    } else if (i % 3 === 0) {
        console.log("Fizz");
    } else if (i % 5 === 0) {
        console.log("Buzz");
    } else {
        console.log(i);
    }
}
```

### Example 4: Password Attempts

```javascript
let password = "secret123";
let attempts = 3;

for (let i = 1; i <= attempts; i++) {
    let guess = window.prompt(`Enter password (Attempt ${i}/${attempts}):`);
    
    if (guess === password) {
        console.log("Access granted!");
        break;
    } else if (i === attempts) {
        console.log("Access denied. No attempts remaining.");
    } else {
        console.log(`Wrong password. ${attempts - i} attempts remaining.`);
    }
}
```

---

## 13.13 Choosing the Right Loop

### Use While Loop When:
- Don't know how many iterations needed
- Based on user input or condition
- Need to validate input

### Use Do-While When:
- Must execute at least once
- Menu systems
- Input validation

### Use For Loop When:
- Know exact number of iterations
- Counting or iterating over ranges
- Array traversal (covered later)

---

## Summary - Chapter 13

✅ **While Loop** - Repeats while condition is true  
✅ **Do-While Loop** - Executes at least once  
✅ **For Loop** - Repeats specific number of times  
✅ **Infinite Loops** - Avoid with proper conditions  
✅ **Continue** - Skip current iteration  
✅ **Break** - Exit loop entirely  
✅ Nested loops for complex patterns  
✅ Choose loop type based on situation  

---

## Practice Exercises

### Exercise 1: Even Numbers
Use a for loop to print all even numbers from 0 to 50.

### Exercise 2: Password Validator
Create a while loop that keeps asking for a password until it meets requirements (length >= 8).

### Exercise 3: Countdown Timer
Create a countdown from 10 to 1 using a for loop, then print "Blast off!".

### Exercise 4: Sum Calculator
Ask user for a number and calculate the sum of all numbers from 1 to that number.

---

## Quick Reference

```javascript
// While Loop
while (condition) {
    // code
}

// Do-While Loop
do {
    // code
} while (condition);

// For Loop
for (let i = 0; i < 10; i++) {
    // code
}

// Continue - skip iteration
continue;

// Break - exit loop
break;
```

---

**Next: Chapters 14 & 15 - Number Guessing Game + Functions**
