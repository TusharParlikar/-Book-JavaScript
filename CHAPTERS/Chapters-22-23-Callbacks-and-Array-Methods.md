# Chapters 22 & 23: Callbacks + Array Methods

---

# Chapter 22: Callbacks

## Overview
A callback is a function passed as an argument to another function, executed after a task completes.

**Timestamp:** [03:34:20]

---

## 22.1 What are Callbacks?

**Timestamp:** [03:34:20], [03:34:26]

**Callback** = A function passed as an argument to another function

Used to handle:
- Asynchronous operations
- Event handling
- Array methods
- Custom operations after task completion

---

## 22.2 Basic Callback Example

**Timestamp:** [03:34:38]

```javascript
function greet(name) {
    console.log(`Hello, ${name}!`);
}

function processUserInput(callback) {
    const name = "John";
    callback(name); // Call the callback function
}

processUserInput(greet);
// Output: Hello, John!
```

**Timestamp:** [03:34:51], [03:35:08]

---

## 22.3 Practical Example: Sum and Display

**Timestamp:** [03:35:32]

```javascript
function sum(x, y) {
    return x + y;
}

function displayResult(result) {
    console.log(`Result: ${result}`);
}

function calculate(x, y, callback) {
    let result = callback(x, y);
    displayResult(result);
}

calculate(5, 3, sum);
// Output: Result: 8
```

**Timestamp:** [03:35:45], [03:36:02], [03:36:18]

---

## 22.4 Multiple Callback Functions

**Timestamp:** [03:36:35]

```javascript
function sum(x, y) {
    return x + y;
}

function subtract(x, y) {
    return x - y;
}

function multiply(x, y) {
    return x * y;
}

function divide(x, y) {
    return x / y;
}

function displayResult(result) {
    console.log(result);
}

function calculate(x, y, callback) {
    let result = callback(x, y);
    displayResult(result);
}

// Use different operations
calculate(10, 5, sum);      // 15
calculate(10, 5, subtract); // 5
calculate(10, 5, multiply); // 50
calculate(10, 5, divide);   // 2
```

**Timestamp:** [03:36:48], [03:37:04]

---

## 22.5 Anonymous Function Callbacks

**Timestamp:** [03:37:22]

```javascript
function calculate(x, y, callback) {
    let result = callback(x, y);
    console.log(result);
}

// Pass anonymous function directly
calculate(10, 5, function(a, b) {
    return a + b;
});
// Output: 15
```

---

## 22.6 Arrow Function Callbacks

**Timestamp:** [03:37:42]

```javascript
// Using arrow function
calculate(10, 5, (a, b) => a + b);      // 15
calculate(10, 5, (a, b) => a - b);      // 5
calculate(10, 5, (a, b) => a * b);      // 50
calculate(10, 5, (a, b) => a / b);      // 2
```

Cleaner and more concise!

---

## 22.7 Callbacks in Asynchronous Code

### setTimeout Example

**Timestamp:** [03:38:05]

```javascript
function greetLater(name, callback) {
    setTimeout(() => {
        callback(name);
    }, 2000);
}

function sayHello(name) {
    console.log(`Hello, ${name}!`);
}

greetLater("John", sayHello);
// After 2 seconds: Hello, John!
```

---

## 22.8 Callbacks with Array Methods

Callbacks are heavily used in array methods:

```javascript
let numbers = [1, 2, 3, 4, 5];

// forEach with callback
numbers.forEach(function(num) {
    console.log(num);
});

// Using arrow function
numbers.forEach(num => console.log(num));
```

---

## 22.9 Real-World Example: Data Processing

```javascript
function fetchData(callback) {
    // Simulate API call
    setTimeout(() => {
        const data = { name: "John", age: 30 };
        callback(data);
    }, 1000);
}

function processData(data) {
    console.log(`Processing: ${data.name}, Age: ${data.age}`);
}

fetchData(processData);
// After 1 second: Processing: John, Age: 30
```

---

## 22.10 Callback Hell (Problem)

Multiple nested callbacks become hard to read:

```javascript
getData(function(a) {
    getMoreData(a, function(b) {
        getMoreData(b, function(c) {
            getMoreData(c, function(d) {
                console.log(d);
            });
        });
    });
});
```

**Solution:** Use Promises or async/await (covered later).

---

## Summary - Chapter 22

✅ **Callback** - Function passed as argument  
✅ Executed after task completes  
✅ Used in async operations  
✅ Common in array methods  
✅ Can use named, anonymous, or arrow functions  
✅ Enables flexible, reusable code  

---

# Chapter 23: Array Methods (forEach, map, filter, reduce)

## Overview
Powerful array methods that use callbacks to iterate and transform arrays.

**Timestamp:** [03:38:30], [03:42:21], [03:45:49], [03:50:34]

---

# 23.1 forEach Method

**Timestamp:** [03:38:30]

## What is forEach?

- Executes a callback for **each element** in an array
- Does **not return** a new array
- Used for iteration and side effects

**Syntax:**
```javascript
array.forEach(callback);
```

---

## forEach Basic Example

**Timestamp:** [03:38:48]

```javascript
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(element) {
    console.log(element);
});

// Output:
// 1
// 2
// 3
// 4
// 5
```

---

## forEach with Arrow Function

**Timestamp:** [03:39:12]

```javascript
numbers.forEach(element => console.log(element));
```

Cleaner syntax!

---

## forEach with Index

**Timestamp:** [03:39:32]

```javascript
let fruits = ["apple", "orange", "banana"];

fruits.forEach((element, index) => {
    console.log(`${index}: ${element}`);
});

// Output:
// 0: apple
// 1: orange
// 2: banana
```

---

## forEach Practical Examples

### Example 1: Display Prices

**Timestamp:** [03:40:05]

```javascript
let prices = [10.99, 25.50, 5.75, 15.00];

prices.forEach(price => {
    console.log(`$${price.toFixed(2)}`);
});

// Output:
// $10.99
// $25.50
// $5.75
// $15.00
```

### Example 2: Modify Elements (Display Only)

```javascript
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(num => {
    console.log(num * 2);
});
// Output: 2, 4, 6, 8, 10
// Original array unchanged
```

### Example 3: Uppercase Strings

**Timestamp:** [03:40:28]

```javascript
let fruits = ["apple", "orange", "banana"];

fruits.forEach(fruit => {
    console.log(fruit.toUpperCase());
});

// Output:
// APPLE
// ORANGE
// BANANA
```

---

## forEach Summary

✅ Executes callback for each element  
✅ No return value  
✅ Used for side effects (logging, updating UI)  
✅ Cannot break/continue (use regular for loop if needed)  

---

# 23.2 map Method

**Timestamp:** [03:42:21]

## What is map?

- Creates a **new array** with results of calling callback on each element
- **Returns** the new array
- Original array is **not modified**
- Same length as original array

**Syntax:**
```javascript
const newArray = array.map(callback);
```

**Timestamp:** [03:42:33], [03:42:42]

---

## map Basic Example

**Timestamp:** [03:42:55]

```javascript
let numbers = [1, 2, 3, 4, 5];

let squared = numbers.map(num => num * num);

console.log(squared);
// [1, 4, 9, 16, 25]

console.log(numbers);
// [1, 2, 3, 4, 5] (unchanged)
```

**Timestamp:** [03:43:12], [03:43:26]

---

## map with Arrow Functions

**Timestamp:** [03:43:42]

```javascript
let numbers = [1, 2, 3, 4, 5];

// Double each number
let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// Square each number
let squared = numbers.map(num => num ** 2);
console.log(squared); // [1, 4, 9, 16, 25]
```

---

## map Practical Examples

### Example 1: Uppercase Strings

**Timestamp:** [03:44:08]

```javascript
let fruits = ["apple", "orange", "banana"];

let upperFruits = fruits.map(fruit => fruit.toUpperCase());

console.log(upperFruits);
// ["APPLE", "ORANGE", "BANANA"]
```

**Timestamp:** [03:44:22], [03:44:34]

---

### Example 2: Format Dates

```javascript
let dates = ["2024-01-01", "2024-02-15", "2024-03-30"];

let formatted = dates.map(date => {
    let parts = date.split("-");
    return `${parts[1]}/${parts[2]}/${parts[0]}`;
});

console.log(formatted);
// ["01/01/2024", "02/15/2024", "03/30/2024"]
```

---

### Example 3: Extract Properties

**Timestamp:** [03:44:49]

```javascript
let students = [
    { name: "John", grade: 85 },
    { name: "Sarah", grade: 92 },
    { name: "Mike", grade: 78 }
];

let names = students.map(student => student.name);
console.log(names); // ["John", "Sarah", "Mike"]

let grades = students.map(student => student.grade);
console.log(grades); // [85, 92, 78]
```

---

## map vs forEach

| Feature | forEach | map |
|---------|---------|-----|
| Returns | undefined | New array |
| Purpose | Side effects | Transform data |
| Original array | Unchanged | Unchanged |
| Use when | Just iterating | Creating new array |

---

## map Summary

✅ **Returns** new array  
✅ Transforms each element  
✅ Original array unchanged  
✅ Same length as original  
✅ Use for data transformation  

---

# 23.3 filter Method

**Timestamp:** [03:45:49]

## What is filter?

- Creates a **new array** with elements that **pass a test**
- Callback returns `true` or `false`
- Only elements returning `true` are included
- Can have **different length** than original

**Syntax:**
```javascript
const newArray = array.filter(callback);
```

**Timestamp:** [03:46:01], [03:46:12]

---

## filter Basic Example

**Timestamp:** [03:46:28]

```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let evenNumbers = numbers.filter(num => num % 2 === 0);

console.log(evenNumbers);
// [2, 4, 6, 8, 10]
```

**Timestamp:** [03:46:42], [03:46:55]

---

## filter Practical Examples

### Example 1: Filter by Age

**Timestamp:** [03:47:15]

```javascript
let ages = [12, 18, 25, 16, 30, 14, 21];

let adults = ages.filter(age => age >= 18);

console.log(adults);
// [18, 25, 30, 21]
```

**Timestamp:** [03:47:28], [03:47:42]

---

### Example 2: Filter Short Words

**Timestamp:** [03:48:05]

```javascript
let words = ["apple", "cat", "banana", "dog", "elephant"];

let shortWords = words.filter(word => word.length <= 5);

console.log(shortWords);
// ["apple", "cat", "dog"]
```

**Timestamp:** [03:48:18], [03:48:32]

---

### Example 3: Filter Objects

```javascript
let students = [
    { name: "John", grade: 85 },
    { name: "Sarah", grade: 92 },
    { name: "Mike", grade: 78 },
    { name: "Emma", grade: 95 }
];

let topStudents = students.filter(student => student.grade >= 90);

console.log(topStudents);
// [{ name: "Sarah", grade: 92 }, { name: "Emma", grade: 95 }]
```

---

### Example 4: Remove Null/Undefined

```javascript
let data = [1, null, 2, undefined, 3, null, 4];

let cleanData = data.filter(item => item != null);

console.log(cleanData);
// [1, 2, 3, 4]
```

---

## filter with Multiple Conditions

**Timestamp:** [03:49:05]

```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Even numbers greater than 5
let filtered = numbers.filter(num => num % 2 === 0 && num > 5);

console.log(filtered);
// [6, 8, 10]
```

---

## filter Summary

✅ **Returns** new array  
✅ Includes only elements that pass test  
✅ Callback returns boolean  
✅ Original array unchanged  
✅ Length can differ from original  

---

# 23.4 reduce Method

**Timestamp:** [03:50:34]

## What is reduce?

- Reduces an array to a **single value**
- Callback takes **accumulator** and **current element**
- Returns the accumulated result
- Can specify initial value

**Syntax:**
```javascript
const result = array.reduce(callback, initialValue);
```

**Timestamp:** [03:50:45], [03:50:58]

---

## reduce Basic Example: Sum

**Timestamp:** [03:51:18]

```javascript
let numbers = [1, 2, 3, 4, 5];

let sum = numbers.reduce((accumulator, element) => {
    return accumulator + element;
}, 0);

console.log(sum); // 15
```

**Breakdown:**
- Initial value: `0`
- Iteration 1: `0 + 1 = 1`
- Iteration 2: `1 + 2 = 3`
- Iteration 3: `3 + 3 = 6`
- Iteration 4: `6 + 4 = 10`
- Iteration 5: `10 + 5 = 15`

**Timestamp:** [03:51:32], [03:51:48], [03:52:05]

---

## reduce Shorthand

**Timestamp:** [03:52:22]

```javascript
let sum = numbers.reduce((acc, el) => acc + el, 0);
console.log(sum); // 15
```

---

## reduce Practical Examples

### Example 1: Find Maximum

**Timestamp:** [03:52:48]

```javascript
let numbers = [10, 45, 23, 67, 34];

let max = numbers.reduce((accumulator, element) => {
    return element > accumulator ? element : accumulator;
}, numbers[0]);

console.log(max); // 67
```

**Timestamp:** [03:53:05], [03:53:22]

---

### Example 2: Find Minimum

```javascript
let min = numbers.reduce((acc, el) => 
    el < acc ? el : acc
, numbers[0]);

console.log(min); // 10
```

---

### Example 3: Count Occurrences

```javascript
let fruits = ["apple", "banana", "apple", "orange", "banana", "apple"];

let count = fruits.reduce((acc, fruit) => {
    acc[fruit] = (acc[fruit] || 0) + 1;
    return acc;
}, {});

console.log(count);
// { apple: 3, banana: 2, orange: 1 }
```

---

### Example 4: Flatten Array

```javascript
let nested = [[1, 2], [3, 4], [5, 6]];

let flat = nested.reduce((acc, arr) => acc.concat(arr), []);

console.log(flat);
// [1, 2, 3, 4, 5, 6]
```

---

### Example 5: Calculate Total Price

```javascript
let cart = [
    { item: "Apple", price: 1.50, quantity: 3 },
    { item: "Banana", price: 0.75, quantity: 5 },
    { item: "Orange", price: 2.00, quantity: 2 }
];

let total = cart.reduce((acc, product) => {
    return acc + (product.price * product.quantity);
}, 0);

console.log(total.toFixed(2)); // 12.25
```

---

## reduce Summary

✅ **Returns** single value  
✅ Accumulates result  
✅ Takes accumulator and element  
✅ Specify initial value (recommended)  
✅ Versatile: sum, max, min, count, flatten  

---

# 23.5 Chaining Array Methods

**Timestamp:** [03:54:15]

Combine multiple methods for complex operations:

```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let result = numbers
    .filter(num => num % 2 === 0)  // Get even numbers
    .map(num => num ** 2)          // Square them
    .reduce((acc, num) => acc + num, 0); // Sum them

console.log(result); // 220 (4 + 16 + 36 + 64 + 100)
```

---

## Method Comparison Table

| Method | Returns | Purpose | Changes Original |
|--------|---------|---------|------------------|
| `forEach` | undefined | Iterate/side effects | No |
| `map` | New array | Transform elements | No |
| `filter` | New array | Select elements | No |
| `reduce` | Single value | Accumulate result | No |

---

## Summary - Chapter 23

✅ **forEach** - Iterate, no return  
✅ **map** - Transform to new array  
✅ **filter** - Select matching elements  
✅ **reduce** - Accumulate to single value  
✅ All use callbacks  
✅ None modify original array  
✅ Can be chained together  

---

## Practice Exercises

### Exercise 1: Data Pipeline
Use filter, map, reduce to process student data.

### Exercise 2: Shopping Cart
Calculate discounted total for items over $50.

### Exercise 3: Word Analysis
Count vowels in array of words using reduce.

### Exercise 4: Data Cleanup
Filter null values, trim strings, convert to uppercase.

---

## Quick Reference

```javascript
// forEach - iterate
arr.forEach(el => console.log(el));

// map - transform
let doubled = arr.map(el => el * 2);

// filter - select
let evens = arr.filter(el => el % 2 === 0);

// reduce - accumulate
let sum = arr.reduce((acc, el) => acc + el, 0);

// Chaining
let result = arr
    .filter(el => el > 0)
    .map(el => el * 2)
    .reduce((acc, el) => acc + el, 0);
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Dice Roller & Password Generator](Chapters-20-21-Dice-Roller-and-Password-Generator.md) | [📑 Index](../README.md) | [Arrow Functions & Objects ▶️](Chapters-24-25-Arrow-Functions-and-Objects.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-22--23-callbacks--array-methods)**

Made with ❤️ for JavaScript learners

</div>
