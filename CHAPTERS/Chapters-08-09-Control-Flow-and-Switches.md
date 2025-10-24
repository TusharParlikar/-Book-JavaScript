# Chapters 8 & 9: Control Flow - If Statements & Ternary/Switch Statements

---

# Chapter 8: Control Flow - If Statements & Checked Property

## Overview
Control flow allows your program to make decisions and execute different code based on conditions. This chapter covers if statements and working with checkboxes and radio buttons.

**Timestamp:** [01:16:02]

---

## 8.1 What are If Statements?

If statements execute code **only if** a condition is true or false.

**Timestamp:** [01:16:02]

```javascript
if (condition) {
    // This code runs if condition is true
}
```

---

## 8.2 Basic If Statement Syntax

**Timestamp:** [01:16:23]

```javascript
let age = 18;

if (age >= 18) {
    console.log("You are an adult");
}
```

### How It Works:
1. Evaluate the condition (`age >= 18`)
2. If `true`, execute the code block
3. If `false`, skip the code block

---

## 8.3 Comparison Operators

**Timestamp:** [01:16:29]

Used to compare values and create conditions:

```javascript
// Greater than
if (age > 18) { }

// Less than
if (age < 18) { }

// Greater than or equal to
if (age >= 18) { }

// Less than or equal to
if (age <= 18) { }

// Equal to (loose equality)
if (age == 18) { }

// Strict equal to (recommended)
if (age === 18) { }
```

### Examples:
```javascript
let temperature = 25;

if (temperature > 30) {
    console.log("It's hot!");
}

if (temperature < 0) {
    console.log("It's freezing!");
}

let score = 100;

if (score >= 90) {
    console.log("Excellent!");
}
```

---

## 8.4 The Else Clause

**Timestamp:** [01:17:16]

Execute alternative code when the condition is false:

```javascript
let age = 15;

if (age >= 18) {
    console.log("You are an adult");
} else {
    console.log("You are a minor");
}
```

### Flow:
- If condition is `true` → First block runs
- If condition is `false` → Else block runs

---

## 8.5 Using Boolean Variables

**Timestamp:** [01:18:54]

You can use boolean variables directly in conditions:

```javascript
let online = true;

// Good - direct usage
if (online) {
    console.log("You are online");
} else {
    console.log("You are offline");
}

// Unnecessary - don't do this
if (online === true) {  // Redundant
    console.log("You are online");
}
```

### More Examples:
```javascript
let isStudent = false;
let hasPaid = true;
let isAdmin = false;

if (isStudent) {
    console.log("Student discount applied");
}

if (hasPaid) {
    console.log("Access granted");
}

if (!isAdmin) {  // NOT operator
    console.log("You don't have admin privileges");
}
```

---

## 8.6 Nested If Statements

**Timestamp:** [01:20:01]

You can place if statements inside other if statements:

```javascript
let age = 25;
let hasLicense = true;

if (age >= 18) {
    console.log("You are old enough");
    
    if (hasLicense) {
        console.log("You can drive!");
    } else {
        console.log("You need a license");
    }
} else {
    console.log("You are too young to drive");
}
```

---

## 8.7 Else If Clause

**Timestamp:** [01:22:59]

Check multiple conditions in sequence:

```javascript
let age = 65;

if (age >= 65) {
    console.log("Senior citizen");
} else if (age >= 18) {
    console.log("Adult");
} else if (age >= 13) {
    console.log("Teenager");
} else {
    console.log("Child");
}
```

### How It Works:
1. Check first condition
2. If false, check next else if
3. If false, check next else if
4. Continue until one is true or reach else
5. Only ONE block executes

---

## 8.8 Order Matters!

**Timestamp:** [01:25:04]

The order of conditions is crucial:

```javascript
// WRONG - Will always say "Adult" for anyone 18+
let age = 70;

if (age >= 18) {
    console.log("Adult");  // This runs first!
} else if (age >= 65) {
    console.log("Senior");  // Never reached!
}

// CORRECT - Check more specific conditions first
if (age >= 65) {
    console.log("Senior");  // Runs for 65+
} else if (age >= 18) {
    console.log("Adult");   // Runs for 18-64
}
```

**Rule:** Put most specific conditions first!

---

## 8.9 Equality Comparison

**Timestamp:** [01:26:08]

```javascript
let age = 18;

// Loose equality (==) - allows type coercion
if (age == "18") {  // true (string "18" converts to number)
    console.log("Exactly 18");
}

// Strict equality (===) - recommended (covered more in Chapter 12)
if (age === "18") {  // false (different types)
    console.log("This won't run");
}

if (age === 18) {  // true (same type and value)
    console.log("Exactly 18");
}
```

---

## 8.10 Practical Example: Age Checker Form

**Timestamp:** [01:27:07]

### HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Age Checker</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Age Verification</h1>
    
    <label for="ageInput">Enter your age:</label>
    <input type="number" id="ageInput">
    <button id="submitBtn">Submit</button>
    
    <p id="resultElement"></p>
    
    <script src="index.js"></script>
</body>
</html>
```

### JavaScript

**Timestamp:** [01:29:46], [01:30:13]

```javascript
const submitBtn = document.getElementById("submitBtn");
const ageInput = document.getElementById("ageInput");
const resultElement = document.getElementById("resultElement");

submitBtn.onclick = function() {
    // Get and convert input to number
    let age = Number(ageInput.value);
    
    // Check different age ranges
    if (age >= 100) {
        resultElement.textContent = "You are too old to enter!";
    } else if (age >= 65) {
        resultElement.textContent = "You are a senior citizen";
    } else if (age >= 18) {
        resultElement.textContent = "You are an adult. Welcome!";
    } else if (age < 0) {
        resultElement.textContent = "Invalid age. Please enter a positive number.";
    } else if (age == 0) {
        resultElement.textContent = "You can't be 0 years old!";
    } else {
        resultElement.textContent = "You are a minor. Access denied.";
    }
};
```

---

## 8.11 The Checked Property

**Timestamp:** [01:31:51]

The `.checked` property determines if a checkbox or radio button is selected.

**Timestamp:** [01:32:00], [01:32:08]

### Returns:
- `true` if checked/selected
- `false` if not checked

---

## 8.12 Working with Checkboxes

**Timestamp:** [01:32:21]

### HTML Setup

```html
<input type="checkbox" id="myCheckbox">
<label for="myCheckbox">Subscribe to newsletter</label>

<button id="submitBtn">Submit</button>
<p id="result"></p>
```

### JavaScript

```javascript
const myCheckbox = document.getElementById("myCheckbox");
const submitBtn = document.getElementById("submitBtn");
const result = document.getElementById("result");

submitBtn.onclick = function() {
    if (myCheckbox.checked) {
        result.textContent = "You are subscribed!";
    } else {
        result.textContent = "You are NOT subscribed";
    }
};
```

---

## 8.13 Working with Radio Buttons

**Timestamp:** [01:33:16]

Radio buttons allow users to select ONE option from a group.

### HTML Setup

```html
<h3>Select Payment Method:</h3>

<input type="radio" id="visaBtn" name="paymentMethod">
<label for="visaBtn">Visa</label><br>

<input type="radio" id="mastercardBtn" name="paymentMethod">
<label for="mastercardBtn">Mastercard</label><br>

<input type="radio" id="paypalBtn" name="paymentMethod">
<label for="paypalBtn">PayPal</label><br><br>

<button id="submitBtn">Submit</button>
<p id="result"></p>
```

**Key Point:** The `name` attribute must be THE SAME for all radio buttons in a group. This ensures only one can be selected at a time.

---

## 8.14 Radio Button JavaScript

**Timestamp:** [01:36:40], [01:38:15], [01:38:34], [01:38:59], [01:39:52]

```javascript
const visaBtn = document.getElementById("visaBtn");
const mastercardBtn = document.getElementById("mastercardBtn");
const paypalBtn = document.getElementById("paypalBtn");
const submitBtn = document.getElementById("submitBtn");
const result = document.getElementById("result");

submitBtn.onclick = function() {
    if (visaBtn.checked) {
        result.textContent = "You selected Visa";
    } else if (mastercardBtn.checked) {
        result.textContent = "You selected Mastercard";
    } else if (paypalBtn.checked) {
        result.textContent = "You selected PayPal";
    } else {
        result.textContent = "Please select a payment method";
    }
};
```

---

## 8.15 Complete Form Example

Combining checkboxes and radio buttons:

### HTML
```html
<h2>Order Form</h2>

<!-- Checkbox -->
<input type="checkbox" id="subscribeBox">
<label for="subscribeBox">Subscribe to newsletter</label><br><br>

<!-- Radio Buttons -->
<h3>Shipping Method:</h3>
<input type="radio" id="standardBtn" name="shipping">
<label for="standardBtn">Standard ($5)</label><br>

<input type="radio" id="expressBtn" name="shipping">
<label for="expressBtn">Express ($10)</label><br><br>

<button id="submitBtn">Submit Order</button>
<p id="result"></p>
```

### JavaScript
```javascript
const subscribeBox = document.getElementById("subscribeBox");
const standardBtn = document.getElementById("standardBtn");
const expressBtn = document.getElementById("expressBtn");
const submitBtn = document.getElementById("submitBtn");
const result = document.getElementById("result");

submitBtn.onclick = function() {
    let message = "";
    
    // Check subscription
    if (subscribeBox.checked) {
        message += "✓ Newsletter subscription active\n";
    } else {
        message += "✗ Not subscribed to newsletter\n";
    }
    
    // Check shipping
    if (standardBtn.checked) {
        message += "Shipping: Standard ($5)";
    } else if (expressBtn.checked) {
        message += "Shipping: Express ($10)";
    } else {
        message += "Please select a shipping method!";
    }
    
    result.textContent = message;
};
```

---

## Summary - Chapter 8

✅ If statements execute code based on conditions  
✅ Comparison operators: `>`, `<`, `>=`, `<=`, `==`, `===`  
✅ Else clause for alternative code  
✅ Else if for multiple conditions  
✅ Order of conditions matters  
✅ Boolean variables can be used directly  
✅ `.checked` property for checkboxes and radio buttons  
✅ Radio buttons use same `name` attribute for grouping  

---

# Chapter 9: Ternary Operator & Switch Statements

## Overview
Learn two more ways to write conditional logic: the ternary operator for simple if/else statements and switch statements for multiple conditions.

---

## 9.1 The Ternary Operator

**Timestamp:** [01:42:07]

The ternary operator is a shortcut for simple if/else statements.

**Timestamp:** [01:42:13]

### Syntax

**Timestamp:** [01:42:20]

```javascript
condition ? expressionIfTrue : expressionIfFalse
```

### Breaking It Down:
- `condition` - What to check
- `?` - Question mark separator
- `expressionIfTrue` - Value/code if true
- `:` - Colon separator
- `expressionIfFalse` - Value/code if false

---

## 9.2 Ternary vs If/Else

### Traditional If/Else:
```javascript
let age = 21;
let message;

if (age >= 18) {
    message = "You're an adult";
} else {
    message = "You're a minor";
}

console.log(message);
```

### Ternary Operator:
**Timestamp:** [01:42:43]

```javascript
let age = 21;
let message = age >= 18 ? "You're an adult" : "You're a minor";
console.log(message);
```

**Benefit:** One line instead of five!

---

## 9.3 Ternary Operator Examples

### Example 1: Age Status

**Timestamp:** [01:42:43]

```javascript
let age = 25;
let status = age >= 18 ? "Adult" : "Minor";
console.log(status);  // "Adult"
```

### Example 2: Time-Based Greeting

**Timestamp:** [01:44:37]

```javascript
let time = 14;  // 2 PM (24-hour format)
let greeting = time < 12 ? "Good morning" : "Good afternoon";
console.log(greeting);  // "Good afternoon"
```

### Example 3: Student Status

**Timestamp:** [01:45:39]

```javascript
let isStudent = true;
let message = isStudent ? "You are a student" : "You are NOT a student";
console.log(message);  // "You are a student"
```

### Example 4: Purchase Discount

**Timestamp:** [01:46:35]

```javascript
let purchaseAmount = 125;
let discount = purchaseAmount >= 100 ? 10 : 0;
console.log(`Discount: ${discount}%`);  // "Discount: 10%"

// Calculate total
let total = purchaseAmount * (1 - discount / 100);
console.log(`Total: $${total}`);  // "Total: $112.5"
```

---

## 9.4 Direct Usage in Output

```javascript
let age = 20;
console.log(`You are ${age >= 18 ? "an adult" : "a minor"}`);

let score = 85;
document.getElementById("result").textContent = 
    `Grade: ${score >= 90 ? "A" : score >= 80 ? "B" : "C"}`;
```

**Note:** Nested ternaries can get confusing - use sparingly!

---

## 9.5 When to Use Ternary Operator

### ✅ Use When:
- Simple if/else logic
- Assigning a value based on condition
- One-line decisions
- Improving code readability

### ❌ Avoid When:
- Multiple conditions (use if/else if)
- Complex logic
- Multiple statements needed
- Nested ternaries (gets confusing)

---

## 9.6 Switch Statements

**Timestamp:** [01:48:50]

Switch statements are an efficient replacement for many else if statements. They compare a value against multiple possible matches.

**Timestamp:** [01:48:50], [01:49:50]

---

## 9.7 Switch Statement Syntax

**Timestamp:** [01:49:39]

```javascript
switch (expression) {
    case value1:
        // Code for value1
        break;
    case value2:
        // Code for value2
        break;
    case value3:
        // Code for value3
        break;
    default:
        // Code if no match
}
```

---

## 9.8 Switch vs Multiple If/Else

### Using Multiple If/Else:
```javascript
let day = 3;
let dayName;

if (day === 1) {
    dayName = "Monday";
} else if (day === 2) {
    dayName = "Tuesday";
} else if (day === 3) {
    dayName = "Wednesday";
} else if (day === 4) {
    dayName = "Thursday";
} else if (day === 5) {
    dayName = "Friday";
} else if (day === 6) {
    dayName = "Saturday";
} else if (day === 7) {
    dayName = "Sunday";
} else {
    dayName = "Invalid day";
}
```

### Using Switch Statement:

**Timestamp:** [01:49:03]

```javascript
let day = 3;
let dayName;

switch (day) {
    case 1:
        dayName = "Monday";
        break;
    case 2:
        dayName = "Tuesday";
        break;
    case 3:
        dayName = "Wednesday";
        break;
    case 4:
        dayName = "Thursday";
        break;
    case 5:
        dayName = "Friday";
        break;
    case 6:
        dayName = "Saturday";
        break;
    case 7:
        dayName = "Sunday";
        break;
    default:
        dayName = "Invalid day";
}

console.log(dayName);  // "Wednesday"
```

**Cleaner and easier to read!**

---

## 9.9 The Break Statement

**Timestamp:** [01:50:28]

The `break` statement exits the switch after a match is found.

### Without Break (WRONG):

**Timestamp:** [01:52:19]

```javascript
let day = 1;

switch (day) {
    case 1:
        console.log("Monday");
    case 2:
        console.log("Tuesday");
    case 3:
        console.log("Wednesday");
}

// Output:
// Monday
// Tuesday
// Wednesday
// All three run! (fall-through)
```

### With Break (CORRECT):
```javascript
let day = 1;

switch (day) {
    case 1:
        console.log("Monday");
        break;  // Stops here!
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");
        break;
}

// Output:
// Monday
// Only one runs!
```

---

## 9.10 The Default Case

**Timestamp:** [01:51:36]

The `default` case runs if no other cases match (like `else`):

```javascript
let day = 10;

switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    default:
        console.log("Not a valid day number");  // This runs
}
```

**Note:** `default` doesn't need a `break` if it's last, but it's good practice.

---

## 9.11 Switch with Conditions (Advanced)

**Timestamp:** [01:53:13]

You can use `switch (true)` to evaluate conditions:

```javascript
let testScore = 85;
let grade;

switch (true) {
    case testScore >= 90:
        grade = "A";
        break;
    case testScore >= 80:
        grade = "B";
        break;
    case testScore >= 70:
        grade = "C";
        break;
    case testScore >= 60:
        grade = "D";
        break;
    default:
        grade = "F";
}

console.log(`Grade: ${grade}`);  // "Grade: B"
```

---

## 9.12 Practical Examples

### Example 1: Month Days Calculator
```javascript
let month = 2;
let days;

switch (month) {
    case 1: case 3: case 5: case 7: case 8: case 10: case 12:
        days = 31;
        break;
    case 4: case 6: case 9: case 11:
        days = 30;
        break;
    case 2:
        days = 28;  // or 29 for leap year
        break;
    default:
        days = "Invalid month";
}

console.log(`Days in month: ${days}`);
```

### Example 2: Calculator
```javascript
let num1 = 10;
let num2 = 5;
let operator = "+";
let result;

switch (operator) {
    case "+":
        result = num1 + num2;
        break;
    case "-":
        result = num1 - num2;
        break;
    case "*":
        result = num1 * num2;
        break;
    case "/":
        result = num1 / num2;
        break;
    default:
        result = "Invalid operator";
}

console.log(`Result: ${result}`);  // "Result: 15"
```

### Example 3: Grade with Message
```javascript
let grade = "B";

switch (grade) {
    case "A":
        console.log("Excellent work!");
        console.log("You got the highest grade!");
        break;
    case "B":
        console.log("Great job!");
        console.log("Keep it up!");
        break;
    case "C":
        console.log("Good effort");
        break;
    case "D":
        console.log("You passed");
        break;
    case "F":
        console.log("You failed");
        console.log("Please try again");
        break;
    default:
        console.log("Invalid grade");
}
```

---

## 9.13 When to Use Switch vs If/Else

### Use Switch When:
✅ Comparing ONE variable against many values  
✅ Values are specific and known  
✅ Need clean, readable code for many options  

### Use If/Else When:
✅ Complex conditions with multiple variables  
✅ Range checking (`age >= 18`)  
✅ Boolean logic (`&&`, `||`)  

---

## Summary - Chapter 9

✅ **Ternary Operator** - Shortcut for simple if/else  
✅ Syntax: `condition ? ifTrue : ifFalse`  
✅ **Switch Statements** - Efficient for multiple specific values  
✅ `break` - Exits switch after match  
✅ `default` - Runs if no cases match  
✅ `switch (true)` - Can evaluate conditions  
✅ Multiple cases can share code  

---

## Practice Exercises

### Exercise 1: Traffic Light
Use a switch to display messages for "red", "yellow", "green" lights.

### Exercise 2: Season Checker
Create a ternary that checks if a month number is in summer (6-8) or not.

### Exercise 3: Grade Calculator
Use switch with conditions to assign letter grades based on numeric scores.

### Exercise 4: Menu System
Create a switch statement for a restaurant menu with different food options.

---

## Quick Reference

```javascript
// Ternary Operator
let result = condition ? valueIfTrue : valueIfFalse;

// Switch Statement
switch (value) {
    case option1:
        // code
        break;
    case option2:
        // code
        break;
    default:
        // code
}

// Switch with Conditions
switch (true) {
    case condition1:
        // code
        break;
    case condition2:
        // code
        break;
}
```

---

**Next: Chapters 10 & 11 - String Methods/Slicing & Method Chaining**
