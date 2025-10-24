# Chapters 10 & 11: String Methods/Slicing & Method Chaining

---

# Chapter 10: String Methods & Slicing

## Overview
String methods allow you to manipulate and work with text data. This chapter covers essential string operations and slicing techniques.

**Timestamp:** [01:55:33]

---

## 10.1 What are String Methods?

String methods are built-in functions that allow you to manipulate and work with text (strings).

**Timestamp:** [01:55:40]

```javascript
let text = "Hello World";
// We can call various methods on this string
```

---

## 10.2 charAt() - Get Character at Index

Returns the character at a specific index position.

**Timestamp:** [01:56:02]

```javascript
let username = "BroCode";

console.log(username.charAt(0));  // "B" (first character)
console.log(username.charAt(3));  // "C"
console.log(username.charAt(6));  // "e" (last character)

// Index out of range returns empty string
console.log(username.charAt(10));  // ""
```

**Remember:** Strings are zero-indexed (start counting at 0)!

---

## 10.3 indexOf() - Find Position of Substring

Returns the index of the FIRST occurrence of a substring.

**Timestamp:** [01:57:14]

```javascript
let username = "BroCode";

console.log(username.indexOf("o"));     // 2 (first 'o')
console.log(username.indexOf("Code"));  // 3 (starts at index 3)
console.log(username.indexOf("xyz"));   // -1 (not found)
```

**Returns -1 if substring is not found**

---

## 10.4 lastIndexOf() - Find Last Position

Returns the index of the LAST occurrence of a substring.

**Timestamp:** [01:57:39]

```javascript
let username = "BroCode";

console.log(username.indexOf("o"));      // 2 (first 'o')
console.log(username.lastIndexOf("o"));  // 5 (last 'o')

let email = "user@test@example.com";
console.log(email.lastIndexOf("@"));     // 10 (last @ symbol)
```

---

## 10.5 length - Get String Length

Returns the number of characters in a string. **Note:** This is a PROPERTY, not a method (no parentheses).

**Timestamp:** [01:57:55]

```javascript
let username = "BroCode";
console.log(username.length);  // 7

let password = "Pass1234!";
console.log(password.length);  // 9

// Useful for validation
if (password.length >= 8) {
    console.log("Password is strong enough");
}
```

---

## 10.6 trim() - Remove Whitespace

Removes whitespace from the BEGINNING and END of a string.

**Timestamp:** [01:58:14]

```javascript
let username = "   BroCode   ";
console.log(username.length);        // 13

username = username.trim();
console.log(username);               // "BroCode"
console.log(username.length);        // 7

// Useful for cleaning user input
let userInput = "  hello@example.com  ";
userInput = userInput.trim();  // "hello@example.com"
```

---

## 10.7 toUpperCase() & toLowerCase()

Convert string to all uppercase or all lowercase.

**Timestamp:** [01:58:49], [01:58:59]

```javascript
let username = "BroCode";

console.log(username.toUpperCase());  // "BROCODE"
console.log(username.toLowerCase());  // "brocode"

// Original string unchanged
console.log(username);  // "BroCode"

// Case-insensitive comparison
let input = "YES";
if (input.toLowerCase() === "yes") {
    console.log("User confirmed");
}
```

---

## 10.8 repeat() - Repeat String

Repeats the string a specified number of times.

**Timestamp:** [01:59:09]

```javascript
let text = "Hello ";
console.log(text.repeat(3));  // "Hello Hello Hello "

let star = "⭐";
console.log(star.repeat(5));  // "⭐⭐⭐⭐⭐"

// Creating separators
console.log("-".repeat(30));  // "------------------------------"
```

---

## 10.9 startsWith() - Check Start of String

Returns `true` if string starts with specified substring.

**Timestamp:** [01:59:19]

```javascript
let username = "BroCode";

console.log(username.startsWith("Bro"));   // true
console.log(username.startsWith("Code"));  // false
console.log(username.startsWith("bro"));   // false (case-sensitive!)

// Checking file extensions
let filename = "document.pdf";
if (filename.startsWith("doc")) {
    console.log("This is a document file");
}
```

---

## 10.10 endsWith() - Check End of String

Returns `true` if string ends with specified substring.

**Timestamp:** [02:00:38]

```javascript
let username = "BroCode";

console.log(username.endsWith("Code"));  // true
console.log(username.endsWith("Bro"));   // false
console.log(username.endsWith("code"));  // false (case-sensitive!)

// Checking file extensions
let filename = "image.jpg";
if (filename.endsWith(".jpg") || filename.endsWith(".png")) {
    console.log("This is an image file");
}
```

---

## 10.11 includes() - Check if Contains Substring

Returns `true` if string contains the specified substring anywhere.

**Timestamp:** [02:00:58]

```javascript
let username = "BroCode";

console.log(username.includes("Code"));  // true
console.log(username.includes("Bro"));   // true
console.log(username.includes("xyz"));   // false

// Email validation
let email = "user@example.com";
if (email.includes("@") && email.includes(".")) {
    console.log("Valid email format");
}
```

---

## 10.12 replaceAll() - Replace All Occurrences

Replaces ALL occurrences of a substring with a new substring.

**Timestamp:** [02:01:19]

```javascript
let phoneNumber = "123-456-7890";
phoneNumber = phoneNumber.replaceAll("-", "");
console.log(phoneNumber);  // "1234567890"

let text = "I like apples. Apples are great!";
text = text.replaceAll("apples", "oranges");
// Note: Case-sensitive! "Apples" won't be replaced

// For case-insensitive, use regex (covered later)
```

---

## 10.13 padStart() - Pad Beginning

Pads the string from the START until it reaches the specified length.

**Timestamp:** [02:02:29]

```javascript
let number = "42";
console.log(number.padStart(5, "0"));  // "00042"

let id = "7";
console.log(id.padStart(4, "ID"));     // "IDI7"

// Credit card display
let lastFour = "1234";
let masked = lastFour.padStart(16, "*");
console.log(masked);  // "************1234"
```

---

## 10.14 padEnd() - Pad End

Pads the string from the END until it reaches the specified length.

**Timestamp:** [02:03:14]

```javascript
let number = "42";
console.log(number.padEnd(5, "0"));    // "42000"

let name = "John";
console.log(name.padEnd(10, "."));     // "John......"

// Creating aligned text
let label = "Name:";
console.log(label.padEnd(15, " ") + "John Doe");
```

---

## 10.15 String Slicing

**Timestamp:** [02:03:35]

Slicing extracts a portion of a string and returns it as a NEW string. The original string is NOT modified.

**Timestamp:** [02:03:43]

---

## 10.16 slice() Method Basics

**Timestamp:** [02:04:10]

```javascript
string.slice(startIndex, endIndex)
```

- **startIndex**: Where to begin (included)
- **endIndex**: Where to stop (excluded)

**Timestamp:** [02:04:26], [02:04:48]

```javascript
let fullName = "John Doe";

// Extract "John"
let firstName = fullName.slice(0, 4);
console.log(firstName);  // "John"
// Starts at index 0, stops before index 4

// Extract "Doe"
let lastName = fullName.slice(5, 8);
console.log(lastName);   // "Doe"
```

---

## 10.17 slice() with Single Parameter

If you omit the endIndex, it slices to the END of the string.

**Timestamp:** [02:05:53]

```javascript
let fullName = "John Doe";

let lastName = fullName.slice(5);
console.log(lastName);  // "Doe" (from index 5 to end)

let text = "JavaScript";
console.log(text.slice(4));  // "Script"
```

---

## 10.18 Negative Indices in slice()

Negative numbers count from the END of the string.

**Timestamp:** [02:06:32]

```javascript
let fullName = "John Doe";

// Get last 3 characters
console.log(fullName.slice(-3));    // "Doe"

// Get all except last 3
console.log(fullName.slice(0, -3)); // "John "

let text = "JavaScript";
console.log(text.slice(-6));        // "Script"
```

---

## 10.19 Dynamic Slicing with indexOf()

**Timestamp:** [02:07:06]

Combine `indexOf()` with `slice()` for dynamic string extraction.

### Example 1: Extract First and Last Names

**Timestamp:** [02:07:28]

```javascript
let fullName = "John Doe";

// Find the space
let spaceIndex = fullName.indexOf(" ");

// Extract first name (before space)
let firstName = fullName.slice(0, spaceIndex);
console.log(firstName);  // "John"

// Extract last name (after space)
let lastName = fullName.slice(spaceIndex + 1);
console.log(lastName);   // "Doe"
```

### Example 2: Extract Email Parts

**Timestamp:** [02:09:28]

```javascript
let email = "john.doe@example.com";

// Find the @ symbol
let atIndex = email.indexOf("@");

// Extract username (before @)
let username = email.slice(0, atIndex);
console.log(username);  // "john.doe"

// Extract domain (after @)
let domain = email.slice(atIndex + 1);
console.log(domain);    // "example.com"
```

---

## 10.20 Practical String Manipulation Examples

### Example 1: Format Phone Number
```javascript
let phone = "1234567890";
let formatted = `(${phone.slice(0, 3)}) ${phone.slice(3, 6)}-${phone.slice(6)}`;
console.log(formatted);  // "(123) 456-7890"
```

### Example 2: Validate Email
```javascript
function isValidEmail(email) {
    email = email.trim().toLowerCase();
    return email.includes("@") && 
           email.includes(".") && 
           email.indexOf("@") < email.lastIndexOf(".");
}

console.log(isValidEmail("user@example.com"));  // true
console.log(isValidEmail("invalid.email"));     // false
```

### Example 3: Extract File Extension
```javascript
let filename = "document.pdf";
let dotIndex = filename.lastIndexOf(".");
let extension = filename.slice(dotIndex + 1);
console.log(extension);  // "pdf"
```

### Example 4: Create Initials
```javascript
let fullName = "John Doe Smith";
let names = fullName.split(" ");
let initials = names.map(name => name.charAt(0).toUpperCase()).join(".");
console.log(initials);  // "J.D.S"
```

---

## Summary - Chapter 10

✅ `charAt(index)` - Get character at position  
✅ `indexOf(substring)` - Find first occurrence  
✅ `lastIndexOf(substring)` - Find last occurrence  
✅ `length` - Get string length  
✅ `trim()` - Remove whitespace  
✅ `toUpperCase()` / `toLowerCase()` - Change case  
✅ `repeat(n)` - Repeat string  
✅ `startsWith()` / `endsWith()` - Check string boundaries  
✅ `includes()` - Check if contains substring  
✅ `replaceAll()` - Replace all occurrences  
✅ `padStart()` / `padEnd()` - Pad string  
✅ `slice(start, end)` - Extract substring  

---

# Chapter 11: Method Chaining

## Overview
Method chaining allows you to call multiple methods on the same object in a single line, making code more concise and readable.

**Timestamp:** [02:11:36]

---

## 11.1 What is Method Chaining?

**Timestamp:** [02:11:43]

Method chaining is calling one method after another in a continuous line of code.

```javascript
// Without chaining (multiple steps)
let username = "  bRoCoDe  ";
username = username.trim();
username = username.toLowerCase();
username = username.charAt(0).toUpperCase() + username.slice(1);

// With chaining (one line)
let username = "  bRoCoDe  ".trim().toLowerCase();
```

---

## 11.2 How Method Chaining Works

When a method returns a value, you can immediately call another method on that returned value.

```javascript
let text = "hello";

// Each method returns a new string
let result = text.toUpperCase();  // Returns "HELLO"
result = result.slice(1);         // Returns "ELLO"
result = result.toLowerCase();    // Returns "ello"

// Chained version
let result = text.toUpperCase().slice(1).toLowerCase();
```

---

## 11.3 Problem: Capitalizing First Letter (Without Chaining)

**Timestamp:** [02:11:58]

Let's capitalize the first letter of a username:

```javascript
let username = "  brocode  ";

// Step 1: Remove whitespace
username = username.trim();           // "brocode"

// Step 2: Get first character
let firstChar = username.charAt(0);   // "b"

// Step 3: Uppercase it
firstChar = firstChar.toUpperCase();  // "B"

// Step 4: Get rest of string
let restOfString = username.slice(1); // "rocode"

// Step 5: Lowercase it
restOfString = restOfString.toLowerCase();  // "rocode"

// Step 6: Combine
username = firstChar + restOfString;  // "Brocode"

console.log(username);  // "Brocode"
```

**Problem:** Too many variables! Code is verbose.

**Timestamp:** [02:14:43]

---

## 11.4 Solution: Using Method Chaining

**Timestamp:** [02:14:55]

```javascript
let username = "  brocode  ";

// Chain all operations together
let firstChar = username.trim().charAt(0).toUpperCase();
let restOfString = username.trim().slice(1).toLowerCase();
username = firstChar + restOfString;

console.log(username);  // "Brocode"
```

**Even Better - All in One:**

```javascript
let username = "  brocode  ";

username = username.trim().charAt(0).toUpperCase() + 
           username.trim().slice(1).toLowerCase();

console.log(username);  // "Brocode"
```

---

## 11.5 Method Chaining Examples

### Example 1: Clean and Format Username

```javascript
let username = "  JoHn_DoE123  ";

// Remove whitespace, convert to lowercase, replace underscore
username = username.trim().toLowerCase().replaceAll("_", "");

console.log(username);  // "johndoe123"
```

### Example 2: Format Email

```javascript
let email = "  USER@EXAMPLE.COM  ";

email = email.trim().toLowerCase();

console.log(email);  // "user@example.com"
```

### Example 3: Password Validation

```javascript
let password = "  Pass1234  ";

// Remove spaces and check length
let isValid = password.trim().length >= 8;

console.log(isValid);  // true
```

### Example 4: Extract and Format Initials

```javascript
let fullName = "john doe";

let firstName = fullName.slice(0, fullName.indexOf(" ")).charAt(0).toUpperCase();
let lastName = fullName.slice(fullName.indexOf(" ") + 1).charAt(0).toUpperCase();
let initials = firstName + "." + lastName + ".";

console.log(initials);  // "J.D."
```

### Example 5: Format Phone Number

```javascript
let phone = "1234567890";

let formatted = phone.slice(0, 3) + "-" + 
                phone.slice(3, 6) + "-" + 
                phone.slice(6);

console.log(formatted);  // "123-456-7890"
```

---

## 11.6 Advantages of Method Chaining

**Timestamp:** [02:16:47]

### ✅ Pros:
1. **Less code** - Fewer lines to write
2. **No temporary variables** - Cleaner namespace
3. **Readable** - Easy to follow the flow
4. **Efficient** - Direct transformation pipeline

### ❌ Cons:
1. **Can become hard to read** if chain is too long
2. **Debugging is harder** - Can't inspect intermediate values easily
3. **Must return compatible types** - Each method must return something chainable

---

## 11.7 When to Use Method Chaining

### ✅ Use When:
- Operations are simple and related
- Chain is short (2-4 methods typically)
- Code readability improves
- No need to inspect intermediate values

### ❌ Avoid When:
- Chain becomes too long (5+ methods)
- Need to debug intermediate steps
- Operations are complex
- Reduces readability

---

## 11.8 Breaking Long Chains for Readability

You can split chains across multiple lines:

```javascript
let username = "  john_doe@example.com  ";

// Readable multi-line chain
let formatted = username
    .trim()
    .toLowerCase()
    .replaceAll("_", "")
    .slice(0, username.indexOf("@"));

console.log(formatted);  // "johndoe"
```

---

## 11.9 Practical Complete Examples

### Example 1: User Registration Form

```javascript
function processUsername(input) {
    return input
        .trim()
        .toLowerCase()
        .replaceAll(" ", "_")
        .slice(0, 20);  // Max 20 characters
}

console.log(processUsername("  John Doe  "));  // "john_doe"
console.log(processUsername("SUPER_LONG_USERNAME_HERE"));  // "super_long_username_"
```

### Example 2: URL Slug Generator

```javascript
function createSlug(title) {
    return title
        .trim()
        .toLowerCase()
        .replaceAll(" ", "-")
        .replaceAll("?", "")
        .replaceAll("!", "");
}

console.log(createSlug("How to Learn JavaScript?"));
// "how-to-learn-javascript"
```

### Example 3: Format Display Name

```javascript
function formatDisplayName(name) {
    return name
        .trim()
        .toLowerCase()
        .charAt(0)
        .toUpperCase() + name.trim().slice(1).toLowerCase();
}

console.log(formatDisplayName("  jOHN  "));  // "John"
```

### Example 4: Clean and Validate Input

```javascript
function cleanInput(text) {
    return text
        .trim()
        .replaceAll("<", "&lt;")
        .replaceAll(">", "&gt;");
}

let userInput = "  <script>alert('xss')</script>  ";
console.log(cleanInput(userInput));
// "&lt;script&gt;alert('xss')&lt;/script&gt;"
```

---

## 11.10 Method Chaining with Other Objects

Method chaining works with arrays too (covered in later chapters):

```javascript
let numbers = [1, 2, 3, 4, 5];

// Chain array methods
let result = numbers
    .filter(n => n > 2)
    .map(n => n * 2)
    .reduce((sum, n) => sum + n, 0);

console.log(result);  // 24
```

---

## Summary - Chapter 11

✅ **Method Chaining** - Call multiple methods in sequence  
✅ **Benefits** - Less code, fewer variables, cleaner syntax  
✅ **Drawbacks** - Can reduce readability if overused  
✅ **Best Practice** - Keep chains short and readable  
✅ **Formatting** - Break long chains across multiple lines  
✅ Works with strings, arrays, and other objects  

---

## Practice Exercises

### Exercise 1: Email Formatter
Create a function that takes an email, trims it, converts to lowercase, and validates it contains @ and .

### Exercise 2: Title Case
Write a function that converts "hello world" to "Hello World" using method chaining.

### Exercise 3: Username Validator
Create a function that cleans username input (trim, lowercase, remove special characters).

### Exercise 4: Phone Formatter
Format a 10-digit phone string into (XXX) XXX-XXXX format using slice and method chaining.

---

## Quick Reference

```javascript
// Basic Chaining
let result = string
    .trim()
    .toLowerCase()
    .replaceAll(" ", "-");

// Common Pattern: Capitalize First Letter
let capitalized = string
    .trim()
    .charAt(0).toUpperCase() + 
    string.trim().slice(1).toLowerCase();

// Multi-line for Readability
let processed = input
    .trim()
    .toLowerCase()
    .replaceAll("_", "")
    .slice(0, 50);
```

---

**Next: Chapters 12 & 13 - Logical Operators & Loops**
