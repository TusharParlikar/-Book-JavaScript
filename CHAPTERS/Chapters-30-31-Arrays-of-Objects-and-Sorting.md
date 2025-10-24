# Chapters 30 & 31: Arrays of Objects Review + Sorting Arrays

---

# Chapter 30: Arrays of Objects (Comprehensive Review)

## Overview
A comprehensive look at working with arrays containing objects - a common and powerful data structure in JavaScript.

**Timestamp:** [06:19:25]

---

## 30.1 Creating Arrays of Objects

**Timestamp:** [06:19:25]

```javascript
const fruits = [
    { name: "Apple", color: "red", calories: 95 },
    { name: "Banana", color: "yellow", calories: 105 },
    { name: "Orange", color: "orange", calories: 62 },
    { name: "Grape", color: "purple", calories: 67 }
];
```

**Timestamp:** [06:19:33]

---

## 30.2 Accessing Properties

**Timestamp:** [06:20:51]

```javascript
// Access by index and property
console.log(fruits[0].name);      // "Apple"
console.log(fruits[1].color);     // "yellow"
console.log(fruits[2].calories);  // 62
```

---

## 30.3 Array Manipulation

**Timestamp:** [06:21:46]

```javascript
// Add new object
fruits.push({ name: "Mango", color: "yellow", calories: 99 });

// Remove last object
fruits.pop();

// Remove specific object by index
fruits.splice(1, 1); // Remove element at index 1

// Find and remove by property
const index = fruits.findIndex(fruit => fruit.name === "Orange");
if (index !== -1) {
    fruits.splice(index, 1);
}
```

---

## 30.4 forEach with Objects

**Timestamp:** [06:22:57]

Iterate through each object:

```javascript
fruits.forEach(fruit => {
    console.log(fruit.name);
});
// Apple
// Banana
// Orange
// Grape

// Access index
fruits.forEach((fruit, index) => {
    console.log(`${index + 1}. ${fruit.name}`);
});
// 1. Apple
// 2. Banana
// 3. Orange
// 4. Grape
```

---

## 30.5 map with Objects

**Timestamp:** [06:23:34]

Transform array of objects:

```javascript
// Extract single property
const names = fruits.map(fruit => fruit.name);
console.log(names);
// ["Apple", "Banana", "Orange", "Grape"]

// Create formatted strings
const formatted = fruits.map(fruit => 
    `${fruit.name} is ${fruit.color}`
);
console.log(formatted);
// ["Apple is red", "Banana is yellow", ...]

// Transform objects
const simplified = fruits.map(fruit => ({
    name: fruit.name,
    cals: fruit.calories
}));
console.log(simplified);
// [{ name: "Apple", cals: 95 }, ...]
```

---

## 30.6 filter with Objects

**Timestamp:** [06:24:47]

Select objects matching criteria:

```javascript
// Filter by property value
const yellowFruits = fruits.filter(fruit => fruit.color === "yellow");
console.log(yellowFruits);
// [{ name: "Banana", color: "yellow", calories: 105 }]

// Filter by numeric property
const lowCalFruits = fruits.filter(fruit => fruit.calories < 100);
console.log(lowCalFruits.map(f => f.name));
// ["Apple", "Orange", "Grape"]

// Multiple conditions
const redLowCal = fruits.filter(fruit => 
    fruit.color === "red" && fruit.calories < 100
);
```

---

## 30.7 reduce with Objects

**Timestamp:** [06:26:33]

Reduce array to single value:

```javascript
// Find maximum
const maxCalFruit = fruits.reduce((max, fruit) => 
    fruit.calories > max.calories ? fruit : max
, fruits[0]);
console.log(maxCalFruit);
// { name: "Banana", color: "yellow", calories: 105 }

// Calculate sum
const totalCalories = fruits.reduce((sum, fruit) => 
    sum + fruit.calories
, 0);
console.log(totalCalories); // 329

// Count by property
const colorCount = fruits.reduce((acc, fruit) => {
    acc[fruit.color] = (acc[fruit.color] || 0) + 1;
    return acc;
}, {});
console.log(colorCount);
// { red: 1, yellow: 1, orange: 1, purple: 1 }
```

---

## 30.8 Method Chaining

Combine methods for powerful transformations:

```javascript
// Get names of fruits with less than 100 calories
const result = fruits
    .filter(fruit => fruit.calories < 100)
    .map(fruit => fruit.name)
    .join(", ");

console.log(result);
// "Apple, Orange, Grape"

// Calculate average calories of yellow fruits
const avgYellowCals = fruits
    .filter(fruit => fruit.color === "yellow")
    .reduce((sum, fruit) => sum + fruit.calories, 0) 
    / fruits.filter(fruit => fruit.color === "yellow").length;

console.log(avgYellowCals); // 105
```

---

## 30.9 Real-World Example: E-commerce

```javascript
const products = [
    { id: 1, name: "Laptop", price: 999, category: "Electronics", inStock: true },
    { id: 2, name: "Phone", price: 699, category: "Electronics", inStock: false },
    { id: 3, name: "Desk", price: 299, category: "Furniture", inStock: true },
    { id: 4, name: "Chair", price: 199, category: "Furniture", inStock: true },
    { id: 5, name: "Monitor", price: 399, category: "Electronics", inStock: true }
];

// Get available electronics under $1000
const availableElectronics = products
    .filter(p => p.category === "Electronics" && p.inStock && p.price < 1000)
    .map(p => ({ name: p.name, price: p.price }));

console.log(availableElectronics);
// [{ name: "Phone", price: 699 }, { name: "Monitor", price: 399 }]

// Calculate total inventory value
const totalValue = products
    .filter(p => p.inStock)
    .reduce((sum, p) => sum + p.price, 0);

console.log(`Total: $${totalValue}`); // "Total: $1896"

// Group by category
const byCategory = products.reduce((acc, product) => {
    if (!acc[product.category]) {
        acc[product.category] = [];
    }
    acc[product.category].push(product);
    return acc;
}, {});

console.log(byCategory);
// {
//   Electronics: [...],
//   Furniture: [...]
// }
```

---

## Summary - Chapter 30

✅ Arrays of objects are powerful data structures  
✅ forEach for iteration  
✅ map for transformation  
✅ filter for selection  
✅ reduce for aggregation  
✅ Chain methods for complex operations  
✅ Access nested properties easily  

---

# Chapter 31: Sorting Arrays & Objects

## Overview
Learn how to sort arrays properly, especially arrays containing numbers and objects.

**Timestamp:** [06:29:24]

---

## 31.1 Default sort() Behavior

**Timestamp:** [06:29:31]

The `.sort()` method sorts elements **as strings** by default:

```javascript
let words = ["banana", "apple", "cherry"];
words.sort();
console.log(words);
// ["apple", "banana", "cherry"] ✓ Works!

let numbers = [10, 5, 40, 25, 1000];
numbers.sort();
console.log(numbers);
// [10, 1000, 25, 40, 5] ✗ Wrong! (lexicographic sort)
```

**Timestamp:** [06:30:19]

---

## 31.2 Sorting Numbers Correctly

**Timestamp:** [06:30:46]

Use a **compare function**:

**Timestamp:** [06:30:53]

```javascript
let numbers = [10, 5, 40, 25, 1000];

// Ascending order
numbers.sort((a, b) => a - b);
console.log(numbers);
// [5, 10, 25, 40, 1000] ✓ Correct!

// Descending order
numbers.sort((a, b) => b - a);
console.log(numbers);
// [1000, 40, 25, 10, 5] ✓ Correct!
```

**Timestamp:** [06:31:16], [06:31:47]

---

## 31.3 How Compare Function Works

**Timestamp:** [06:31:07]

The compare function receives two elements (`a` and `b`):

- If return value is **negative**: `a` comes before `b`
- If return value is **positive**: `b` comes before `a`
- If return value is **zero**: order unchanged

```javascript
// Ascending: a - b
(a, b) => a - b
// If a < b: negative (a before b)
// If a > b: positive (b before a)

// Descending: b - a
(a, b) => b - a
// If b < a: negative (b before a)
// If b > a: positive (a before b)
```

---

## 31.4 Sorting Objects by Numeric Property

**Timestamp:** [06:32:02], [06:33:17]

```javascript
const people = [
    { name: "John", age: 30 },
    { name: "Jane", age: 25 },
    { name: "Bob", age: 35 },
    { name: "Alice", age: 28 }
];

// Sort by age (ascending)
people.sort((a, b) => a.age - b.age);
console.log(people);
// [
//   { name: "Jane", age: 25 },
//   { name: "Alice", age: 28 },
//   { name: "John", age: 30 },
//   { name: "Bob", age: 35 }
// ]

// Sort by age (descending)
people.sort((a, b) => b.age - a.age);
```

**Timestamp:** [06:34:03]

---

## 31.5 Sorting Objects by String Property

**Timestamp:** [06:35:00]

Use `.localeCompare()` for strings:

```javascript
const people = [
    { name: "John", age: 30 },
    { name: "Jane", age: 25 },
    { name: "Bob", age: 35 },
    { name: "Alice", age: 28 }
];

// Sort by name (ascending)
people.sort((a, b) => a.name.localeCompare(b.name));
console.log(people);
// [
//   { name: "Alice", age: 28 },
//   { name: "Bob", age: 35 },
//   { name: "Jane", age: 25 },
//   { name: "John", age: 30 }
// ]

// Sort by name (descending)
people.sort((a, b) => b.name.localeCompare(a.name));
```

**Timestamp:** [06:35:25]

---

## 31.6 Complete Sorting Example

**Timestamp:** [06:33:17]

```javascript
const students = [
    { name: "John", gpa: 3.5, age: 20 },
    { name: "Alice", gpa: 3.9, age: 19 },
    { name: "Bob", gpa: 3.2, age: 21 },
    { name: "Jane", gpa: 3.8, age: 20 }
];

// Sort by GPA (descending - highest first)
students.sort((a, b) => b.gpa - a.gpa);
console.log("By GPA:", students.map(s => `${s.name}: ${s.gpa}`));
// By GPA: ["Alice: 3.9", "Jane: 3.8", "John: 3.5", "Bob: 3.2"]

// Sort by age (ascending - youngest first)
students.sort((a, b) => a.age - b.age);
console.log("By Age:", students.map(s => `${s.name}: ${s.age}`));
// By Age: ["Alice: 19", "John: 20", "Jane: 20", "Bob: 21"]

// Sort by name (alphabetically)
students.sort((a, b) => a.name.localeCompare(b.name));
console.log("By Name:", students.map(s => s.name));
// By Name: ["Alice", "Bob", "Jane", "John"]
```

---

## 31.7 Advanced Sorting: Multiple Criteria

Sort by primary criterion, then secondary if equal:

```javascript
const students = [
    { name: "John", grade: "A", age: 20 },
    { name: "Alice", grade: "A", age: 19 },
    { name: "Bob", grade: "B", age: 21 },
    { name: "Jane", grade: "A", age: 20 }
];

// Sort by grade, then by age if grades are equal
students.sort((a, b) => {
    // First compare grades
    const gradeCompare = a.grade.localeCompare(b.grade);
    if (gradeCompare !== 0) {
        return gradeCompare;
    }
    // If grades equal, compare ages
    return a.age - b.age;
});

console.log(students);
// All A's first (sorted by age), then B's
```

---

## 31.8 Practical Examples

### Example 1: Sort Products by Price

```javascript
const products = [
    { name: "Laptop", price: 999 },
    { name: "Mouse", price: 25 },
    { name: "Keyboard", price: 75 },
    { name: "Monitor", price: 399 }
];

// Cheapest to most expensive
products.sort((a, b) => a.price - b.price);
console.log(products.map(p => `${p.name}: $${p.price}`));
// ["Mouse: $25", "Keyboard: $75", "Monitor: $399", "Laptop: $999"]
```

### Example 2: Sort by Date

```javascript
const events = [
    { name: "Meeting", date: new Date("2024-03-15") },
    { name: "Conference", date: new Date("2024-02-20") },
    { name: "Workshop", date: new Date("2024-04-10") }
];

// Earliest to latest
events.sort((a, b) => a.date - b.date);
console.log(events.map(e => e.name));
// ["Conference", "Meeting", "Workshop"]
```

### Example 3: Sort by Boolean

```javascript
const tasks = [
    { name: "Task A", completed: false },
    { name: "Task B", completed: true },
    { name: "Task C", completed: false },
    { name: "Task D", completed: true }
];

// Incomplete tasks first
tasks.sort((a, b) => a.completed - b.completed);
// or
tasks.sort((a, b) => Number(a.completed) - Number(b.completed));
```

---

## 31.9 Sorting Tips

### ✅ Best Practices:
- Always use compare function for numbers
- Use `.localeCompare()` for strings
- Remember `.sort()` modifies original array
- Use `.slice()` to sort a copy: `arr.slice().sort(...)`

### Common Patterns:
```javascript
// Ascending numbers
arr.sort((a, b) => a - b)

// Descending numbers
arr.sort((a, b) => b - a)

// Ascending strings
arr.sort((a, b) => a.localeCompare(b))

// Descending strings
arr.sort((a, b) => b.localeCompare(a))

// Object by numeric property (ascending)
arr.sort((a, b) => a.prop - b.prop)

// Object by string property (ascending)
arr.sort((a, b) => a.prop.localeCompare(b.prop))
```

---

## 31.10 Reversing Arrays

**Timestamp:** [06:31:47]

```javascript
let numbers = [1, 2, 3, 4, 5];

// Reverse in place
numbers.reverse();
console.log(numbers); // [5, 4, 3, 2, 1]

// Reverse without modifying original
let reversed = [...numbers].reverse();
```

---

## Summary - Chapter 31

✅ Default `.sort()` treats elements as strings  
✅ Use compare function for numeric sort  
✅ `(a, b) => a - b` for ascending numbers  
✅ `(a, b) => b - a` for descending numbers  
✅ Use `.localeCompare()` for string sorting  
✅ Can sort objects by any property  
✅ `.reverse()` reverses array order  

---

## Practice Exercises

### Exercise 1: Sort by Multiple Properties
Sort students by grade, then by name if grades match.

### Exercise 2: Custom Sort Order
Sort colors in custom order: red, green, blue.

### Exercise 3: Sort Nested Properties
Sort products by nested price property.

### Exercise 4: Case-Insensitive Sort
Sort strings ignoring case.

---

## Quick Reference

```javascript
// Numbers ascending
arr.sort((a, b) => a - b);

// Numbers descending
arr.sort((a, b) => b - a);

// Strings ascending
arr.sort((a, b) => a.localeCompare(b));

// Strings descending
arr.sort((a, b) => b.localeCompare(a));

// Objects by number property
arr.sort((a, b) => a.age - b.age);

// Objects by string property
arr.sort((a, b) => a.name.localeCompare(b.name));

// Reverse
arr.reverse();

// Sort copy (don't modify original)
const sorted = [...arr].sort((a, b) => a - b);
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ this Keyword & Nested Objects](Chapters-28-29-this-Keyword-and-Nested-Objects.md) | [📑 Index](../README.md) | [Shuffling Arrays & Date Objects ▶️](Chapters-32-33-Shuffling-Arrays-and-Date-Objects.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-30--31-arrays-of-objects-review--sorting-arrays)**

Made with ❤️ for JavaScript learners

</div>
