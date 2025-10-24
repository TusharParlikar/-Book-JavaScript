# Chapter 3: Variables

## Overview
Variables are fundamental building blocks in programming. They act as containers that store data values, allowing you to save, retrieve, and manipulate information throughout your program. In this chapter, you'll learn what variables are, how to create them, and the different types of data they can hold.

---

## 3.1 What Are Variables?

**Variables** are containers for storing data values. Think of them as labeled boxes where you can put information and retrieve it later.

**Timestamp:** [00:12:38]

### Analogy:
Imagine variables like labeled storage boxes:
- The label is the **variable name**
- The contents are the **value**
- You can open the box (read), replace contents (update), or create new boxes (declare)

---

## 3.2 Creating Variables

Creating a variable involves two steps: **declaration** and **assignment**.

**Timestamp:** [00:12:49]

### Step 1: Declaration

Use the `let` keyword to declare (create) a variable:

```javascript
let age;
let price;
let gpa;
```

- `let` - Keyword that declares a variable
- `age` - The variable name (identifier)

### Step 2: Assignment

Use the `=` operator to assign (give) a value:

```javascript
age = 25;
price = 10.99;
gpa = 3.8;
```

- `=` - Assignment operator (not "equals")
- `25` - The value being stored

### Combined Declaration and Assignment

You can declare and assign in one line:

```javascript
let age = 25;
let price = 10.99;
let gpa = 3.8;
```

This is more concise and commonly used.

**Timestamp:** [00:13:58]

---

## 3.3 Variable Naming Rules

When creating variables, you must follow these rules:

### Required Rules (Must Follow):
1. **Cannot start with a number**
   ```javascript
   let 1age = 25;  // Error
   let age1 = 25;  // OK
   ```

2. **Cannot contain spaces**
   ```javascript
   let first name = "John";  // Error
   let firstName = "John";   // OK (camelCase)
   let first_name = "John";  // OK (snake_case)
   ```

3. **Cannot use reserved keywords**
   ```javascript
   let let = 5;      // Error (let is a keyword)
   let class = "A";  // Error (class is a keyword)
   ```

4. **Case sensitive**
   ```javascript
   let age = 25;
   let Age = 30;  // Different variable!
   ```

### Best Practices (Should Follow):

1. **Use descriptive names**
   ```javascript
   let x = 25;          // Bad - what does x mean?
   let userAge = 25;    // Good - clear meaning
   ```

2. **Use camelCase convention**
   ```javascript
   let firstName = "John";
   let lastName = "Doe";
   let phoneNumber = "555-1234";
   ```

3. **Start with a lowercase letter**
   ```javascript
   let name = "John";  // Good
   let Name = "John";  // Avoid (looks like a class)
   ```

4. **Use meaningful names**
   ```javascript
   let temp = 72;              // Bad - temp what?
   let temperatureInFahrenheit = 72;  // Good
   ```

**Timestamp:** [00:13:06]

---

## 3.4 Data Types in JavaScript

JavaScript variables can hold different types of data. Let's explore the three fundamental data types.

---

## 3.5 Numbers

Numbers can be integers (whole numbers) or decimals (floating-point numbers).

**Timestamp:** [00:14:25]

### Declaring Number Variables

```javascript
let age = 25;           // Integer
let price = 10.99;      // Decimal
let gpa = 3.75;         // Decimal
let temperature = -5;   // Negative number
```

### Using Numbers in Output

```javascript
let age = 25;
console.log("You are " + age + " years old");  // Concatenation
console.log(`You are ${age} years old`);       // Template literal
```

**Timestamp:** [00:15:28]

---

## 3.6 Template Literals

Template literals use backticks (`` ` ``) and allow you to embed variables directly into strings using `${variableName}` syntax.

### Syntax

```javascript
let name = "John";
let age = 25;

// Template literal
console.log(`My name is ${name} and I am ${age} years old`);
```

### Benefits:
- More readable than concatenation
- Can include expressions: `${age + 1}`
- Supports multi-line strings
- No need for `+` operators

### Example with Multiple Variables

```javascript
let firstName = "John";
let age = 25;
let price = 10.99;
let gpa = 3.75;

console.log(`Name: ${firstName}`);
console.log(`Age: ${age}`);
console.log(`Price: $${price}`);
console.log(`GPA: ${gpa}`);
```

---

## 3.7 The typeof Operator

The `typeof` operator returns the data type of a value or variable.

**Timestamp:** [00:16:38]

### Syntax

```javascript
typeof value
typeof(value)  // Both work
```

### Example

```javascript
let age = 25;
let price = 10.99;

console.log(typeof age);    // "number"
console.log(typeof price);  // "number"
```

---

## 3.8 Strings

Strings are sequences of characters (text). They must be enclosed in quotes.

**Timestamp:** [00:17:02]

### Declaring String Variables

```javascript
let firstName = "John";
let favoriteFood = 'pizza';  // Single quotes work too
let email = "john@example.com";
```

### Quotes in Strings

You can use either single or double quotes, but they must match:

```javascript
let name = "John";     // OK
let name = 'John';     // OK
let name = "John';     // Error - quotes don't match
```

### When to Use Each:
```javascript
// Use single quotes if string contains double quotes
let message = 'He said "Hello"';

// Use double quotes if string contains single quotes
let message = "It's a beautiful day";

// Or use template literals
let message = `He said "Hello" and it's great!`;
```

### Strings Can Contain Numbers

```javascript
let phoneNumber = "555-1234";
let zipCode = "12345";
```

**Important:** These are strings, not numbers. You cannot perform math operations on them.

```javascript
let a = "5";
let b = "3";
console.log(a + b);  // "53" (concatenation, not 8)
```

**Timestamp:** [00:19:07]

---

## 3.9 Booleans

Booleans represent one of two values: `true` or `false`. They're used for yes/no, on/off situations.

**Timestamp:** [00:19:28]

### Declaring Boolean Variables

```javascript
let online = true;
let forSale = false;
let isStudent = true;
```

### Common Use Cases:

```javascript
// User status
let isLoggedIn = true;
let isAdmin = false;

// Item properties
let isAvailable = true;
let isOnSale = false;

// Feature flags
let hasPermission = true;
let isEnabled = false;
```

### Using Booleans

Booleans are typically used with conditional statements (covered later):

```javascript
let online = true;

if (online) {
    console.log("You are online");
} else {
    console.log("You are offline");
}
```

**Timestamp:** [00:21:34]

---

## 3.10 Displaying Variables on a Webpage

You can display variable values on your webpage using DOM manipulation.

**Timestamp:** [00:21:53]

### HTML Setup

```html
<body>
    <p>Name: <span id="nameDisplay"></span></p>
    <p>Age: <span id="ageDisplay"></span></p>
    <p>Student: <span id="studentDisplay"></span></p>
    
    <script src="index.js"></script>
</body>
```

### JavaScript

```javascript
// Declare variables
let firstName = "John";
let age = 25;
let isStudent = true;

// Select elements
let nameDisplay = document.getElementById("nameDisplay");
let ageDisplay = document.getElementById("ageDisplay");
let studentDisplay = document.getElementById("studentDisplay");

// Update text content
nameDisplay.textContent = firstName;
ageDisplay.textContent = age;
studentDisplay.textContent = isStudent;
```

---

## 3.11 Complete Example: User Profile

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>User Profile</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>User Profile</h1>
    <p>First Name: <span id="firstNameDisplay"></span></p>
    <p>Last Name: <span id="lastNameDisplay"></span></p>
    <p>Age: <span id="ageDisplay"></span></p>
    <p>Email: <span id="emailDisplay"></span></p>
    <p>Student: <span id="studentDisplay"></span></p>
    
    <script src="index.js"></script>
</body>
</html>
```

### JavaScript
```javascript
// Personal information
let firstName = "John";
let lastName = "Doe";
let age = 25;
let email = "john.doe@example.com";
let isStudent = true;

// Console output
console.log(`Name: ${firstName} ${lastName}`);
console.log(`Age: ${age}`);
console.log(`Email: ${email}`);
console.log(`Student: ${isStudent}`);
console.log(typeof firstName);  // "string"
console.log(typeof age);        // "number"
console.log(typeof isStudent);  // "boolean"

// Update webpage
document.getElementById("firstNameDisplay").textContent = firstName;
document.getElementById("lastNameDisplay").textContent = lastName;
document.getElementById("ageDisplay").textContent = age;
document.getElementById("emailDisplay").textContent = email;
document.getElementById("studentDisplay").textContent = isStudent;
```

---

## 3.12 Common Mistakes

### Mistake 1: Not Declaring Variables
```javascript
age = 25;  // Works, but bad practice (creates global variable)
let age = 25;  // Good - properly declared
```

### Mistake 2: Re-declaring with let
```javascript
let age = 25;
let age = 30;  // Error - cannot re-declare
age = 30;      // OK - reassignment without let
```

### Mistake 3: Using Undefined Variables
```javascript
console.log(name);  // Error if name was never declared
```

### Mistake 4: Wrong Data Type Assumptions
```javascript
let age = "25";  // String, not number!
console.log(typeof age);  // "string"
```

---

## Summary

In this chapter, you learned:

✅ What variables are (containers for data)  
✅ How to declare variables using `let`  
✅ How to assign values to variables  
✅ Variable naming rules and best practices  
✅ Three fundamental data types:
  - **Numbers** (integers and decimals)
  - **Strings** (text)
  - **Booleans** (true/false)  
✅ How to use template literals with `${}`  
✅ How to check data types with `typeof`  
✅ How to display variables on a webpage  

---

## Practice Exercises

### Exercise 1: Personal Info
Create variables for your personal information:
- Full name
- Age
- Favorite food
- Whether you're a student

### Exercise 2: Math Variables
Create variables for:
- A product price
- Quantity
- Calculate total (price * quantity)

### Exercise 3: Display Variables
Create an HTML page that displays at least 5 different variables.

### Exercise 4: Type Checking
Create variables of different types and use `typeof` to verify their types.

---

## Quick Reference

### Variable Declaration
```javascript
let variableName;              // Declaration
variableName = value;          // Assignment
let variableName = value;      // Declaration + Assignment
```

### Data Types
```javascript
let num = 25;                  // Number
let text = "Hello";            // String
let bool = true;               // Boolean
```

### Template Literals
```javascript
let name = "John";
console.log(`Hello ${name}`);  // Hello John
```

### Type Checking
```javascript
console.log(typeof value);     // Returns data type
```

---

## Next Steps

Now that you understand variables and data types, you're ready to learn about **operators** and how to accept **user input**. In the next chapter, you'll learn how to perform calculations and interact with users!

---

**Continue to Chapter 4: Operators & User Input**
