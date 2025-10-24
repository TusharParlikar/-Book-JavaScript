# Chapters 18 & 19: Arrays + Spread & Rest Operators

---

# Chapter 18: Arrays

## Overview
Arrays are used to store multiple values in a single variable. They're ordered collections that can hold any data type.



---

## 18.1 What are Arrays?

, [03:10:37]

Arrays are:
- Variables used to store **multiple values**
- **Ordered** collections (indexed)
- Can contain any data type
- Accessed using **index numbers** (starting from 0)

---

## 18.2 Creating Arrays

### Array Literal Syntax



```javascript
let fruits = ["apple", "orange", "banana"];
```

### Using the Array Constructor

```javascript
let numbers = new Array(1, 2, 3, 4, 5);
```

### Empty Array

```javascript
let emptyArray = [];
```

---

## 18.3 Accessing Elements

, [03:11:23]

Use square brackets with the **index** (starting from 0):

```javascript
let fruits = ["apple", "orange", "banana"];

console.log(fruits[0]); 
// Output: "apple"

console.log(fruits[1]); 
// Output: "orange"

console.log(fruits[2]); 
// Output: "banana"
```

---

## 18.4 Modifying Elements



```javascript
let fruits = ["apple", "orange", "banana"];

// Change an element
fruits[0] = "pear";
console.log(fruits); 
// Output: ["pear", "orange", "banana"]
```

---

## 18.5 Array Length



Get the number of elements using `.length`:

```javascript
let fruits = ["apple", "orange", "banana"];
console.log(fruits.length); 
// Output: 3
```

---

## 18.6 Adding Elements

### Push - Add to End



```javascript
let fruits = ["apple", "orange", "banana"];
fruits.push("mango");
console.log(fruits); // ["apple", "orange", "banana", "mango"]
```

### Unshift - Add to Beginning



```javascript
fruits.unshift("grape");
console.log(fruits); // ["grape", "apple", "orange", "banana", "mango"]
```

---

## 18.7 Removing Elements

### Pop - Remove from End



```javascript
let fruits = ["apple", "orange", "banana"];
let removed = fruits.pop();
console.log(removed); // "banana"
console.log(fruits);  // ["apple", "orange"]
```

### Shift - Remove from Beginning



```javascript
let removed = fruits.shift();
console.log(removed); // "apple"
console.log(fruits);  // ["orange"]
```

---

## 18.8 Finding Elements

### indexOf - Find Index



```javascript
let fruits = ["apple", "orange", "banana"];
let index = fruits.indexOf("orange");
console.log(index); // 1

// Element not found returns -1
console.log(fruits.indexOf("grape")); // -1
```

---

## 18.9 Looping Through Arrays

### For Loop



```javascript
let fruits = ["apple", "orange", "banana"];

for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
// Output:
// apple
// orange
// banana
```



### For...of Loop (Enhanced)



```javascript
for (let fruit of fruits) {
    console.log(fruit);
}
// Output: same as above
```

Cleaner and more readable!

---

## 18.10 Sorting Arrays



### Sort Alphabetically

```javascript
let fruits = ["banana", "apple", "orange"];
fruits.sort();
console.log(fruits); // ["apple", "banana", "orange"]
```

### Reverse Order



```javascript
fruits.reverse();
console.log(fruits); // ["orange", "banana", "apple"]
```

---

## 18.11 2D Arrays



Arrays within arrays (matrix/grid structure):

```javascript
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

// Access elements
console.log(matrix[0][0]); // 1
console.log(matrix[1][2]); // 6
console.log(matrix[2][1]); // 8
```

, [03:15:26], [03:15:36]

---

## 18.12 Practical Array Examples

### Example 1: Shopping List

```javascript
let shoppingList = [];

shoppingList.push("milk");
shoppingList.push("bread");
shoppingList.push("eggs");

console.log(`You have ${shoppingList.length} items`);

for (let item of shoppingList) {
    console.log(`- ${item}`);
}
```

### Example 2: Grade Average

```javascript
let grades = [85, 92, 78, 95, 88];
let sum = 0;

for (let grade of grades) {
    sum += grade;
}

let average = sum / grades.length;
console.log(`Average: ${average.toFixed(1)}`); // 87.6
```

### Example 3: Find Maximum

```javascript
let numbers = [12, 45, 23, 67, 34, 89, 56];
let max = numbers[0];

for (let num of numbers) {
    if (num > max) {
        max = num;
    }
}

console.log(`Maximum: ${max}`); // 89
```

---

## 18.13 Common Array Methods Summary

| Method | Description | Example |
|--------|-------------|---------|
| `.push(item)` | Add to end | `arr.push("new")` |
| `.pop()` | Remove from end | `arr.pop()` |
| `.unshift(item)` | Add to beginning | `arr.unshift("first")` |
| `.shift()` | Remove from beginning | `arr.shift()` |
| `.indexOf(item)` | Find index | `arr.indexOf("item")` |
| `.length` | Get size | `arr.length` |
| `.sort()` | Sort alphabetically | `arr.sort()` |
| `.reverse()` | Reverse order | `arr.reverse()` |

---

## Summary - Chapter 18

✅ Arrays store multiple values  
✅ Zero-indexed (start at 0)  
✅ Access with square brackets `[]`  
✅ `.push()` / `.pop()` for end  
✅ `.unshift()` / `.shift()` for beginning  
✅ Loop with `for` or `for...of`  
✅ 2D arrays for matrices  

---

# Chapter 19: Spread Operator (...)

## Overview
The spread operator (`...`) expands iterables (arrays, strings) into individual elements.



---

## 19.1 What is the Spread Operator?

, [03:16:32]

- Uses three dots: `...`
- **Unpacks** elements from an array or string
- Expands elements into individual pieces
- Introduced in ES6 (2015)

---

## 19.2 Basic Syntax

```javascript
let array = [1, 2, 3];
console.log(...array); // 1 2 3 (individual elements)
```

Compare to:
```javascript
console.log(array); // [1, 2, 3] (array)
```

---

## 19.3 Using with Math Functions

, [03:17:06]

### Find Maximum

```javascript
let numbers = [1, 2, 3, 4, 5];

// Without spread (doesn't work)
let maximum = Math.max(numbers); // NaN

// With spread (works!)
let maximum = Math.max(...numbers); // 5
```



### Find Minimum

```javascript
let minimum = Math.min(...numbers); // 1
```



---

## 19.4 Combining Arrays



### Without Spread

```javascript
let fruits = ["apple", "orange", "banana"];
let vegetables = ["carrot", "potato", "onion"];

// This creates nested arrays
let combined = [fruits, vegetables];
console.log(combined);
// [["apple", "orange", "banana"], ["carrot", "potato", "onion"]]
```

### With Spread



```javascript
let foods = [...fruits, ...vegetables];
console.log(foods);
// ["apple", "orange", "banana", "carrot", "potato", "onion"]
```

Spreads both arrays into a single flat array!

---

## 19.5 Inserting in Middle



```javascript
let fruits = ["apple", "banana"];
let vegetables = ["carrot", "potato"];
let meat = ["chicken", "beef"];

let foods = [...fruits, ...vegetables, ...meat];
console.log(foods);
// ["apple", "banana", "carrot", "potato", "chicken", "beef"]
```

---

## 19.6 Copying Arrays



### Shallow Copy

```javascript
let original = [1, 2, 3];
let copy = [...original];

console.log(copy); // [1, 2, 3]

// Modifying copy doesn't affect original
copy.push(4);
console.log(original); // [1, 2, 3]
console.log(copy);     // [1, 2, 3, 4]
```



---

## 19.7 Spreading Strings



```javascript
let username = "John Doe";
let letters = [...username];

console.log(letters);
// ["J", "o", "h", "n", " ", "D", "o", "e"]
```



### Joining with Separator

```javascript
let username = "John";
console.log(...username); // J o h n (space-separated)
```

---

## 19.8 Rest Operator (Related)



The **rest operator** uses the same syntax (`...`) but **bundles** elements into an array.

### In Function Parameters

, [03:20:54]

```javascript
function sum(...numbers) {
    // numbers is an array of all arguments
    let total = 0;
    for (let num of numbers) {
        total += num;
    }
    return total;
}

console.log(sum(1, 2));          // 3
console.log(sum(1, 2, 3, 4));    // 10
console.log(sum(1, 2, 3, 4, 5)); // 15
```

Accepts any number of arguments!

, [03:21:19], [03:21:25]

---

## 19.9 Rest with Other Parameters



```javascript
function getAverage(...numbers) {
    let sum = 0;
    for (let num of numbers) {
        sum += num;
    }
    return sum / numbers.length;
}

console.log(getAverage(10, 20, 30)); // 20
```



---

## 19.10 Combining Regular and Rest Parameters



```javascript
function introduce(firstName, lastName, ...hobbies) {
    console.log(`Name: ${firstName} ${lastName}`);
    console.log(`Hobbies:`);
    for (let hobby of hobbies) {
        console.log(`- ${hobby}`);
    }
}

introduce("John", "Doe", "reading", "gaming", "coding");
// Output:
// Name: John Doe
// Hobbies:
// - reading
// - gaming
// - coding
```

**Important:** Rest parameter must be the **last** parameter!

---

## 19.11 Spread vs Rest

### Spread Operator
- **Unpacks** elements from array
- Used when calling functions or creating arrays
- Expands into individual elements

```javascript
let nums = [1, 2, 3];
console.log(...nums); // 1 2 3
```

### Rest Operator
- **Bundles** elements into array
- Used in function parameters
- Collects multiple arguments

```javascript
function sum(...nums) {
    // nums is [1, 2, 3]
}
sum(1, 2, 3);
```

---

## 19.12 Practical Examples

### Example 1: Merge and Sort

```javascript
let scores1 = [85, 92, 78];
let scores2 = [88, 95, 73];

let allScores = [...scores1, ...scores2];
allScores.sort((a, b) => a - b);

console.log(allScores); // [73, 78, 85, 88, 92, 95]
```

### Example 2: Remove Duplicates

```javascript
let numbers = [1, 2, 2, 3, 4, 4, 5];
let unique = [...new Set(numbers)];

console.log(unique); // [1, 2, 3, 4, 5]
```

### Example 3: Function with Unlimited Args

```javascript
function multiply(multiplier, ...numbers) {
    return numbers.map(num => num * multiplier);
}

console.log(multiply(2, 1, 2, 3, 4)); // [2, 4, 6, 8]
```

### Example 4: Concatenate Strings

```javascript
function combineWords(...words) {
    return words.join(" ");
}

console.log(combineWords("Hello", "World", "from", "JavaScript"));
// "Hello World from JavaScript"
```

---

## 19.13 Advanced Use Cases

### Destructuring with Rest

```javascript
let [first, second, ...rest] = [1, 2, 3, 4, 5];

console.log(first);  // 1
console.log(second); // 2
console.log(rest);   // [3, 4, 5]
```

### Object Spread (ES2018)

```javascript
let person = { name: "John", age: 30 };
let employee = { ...person, id: 123, role: "Developer" };

console.log(employee);
// { name: "John", age: 30, id: 123, role: "Developer" }
```

---

## Summary - Chapter 19

✅ **Spread (`...`)** - Unpacks array elements  
✅ Used with `Math.max()`, `Math.min()`  
✅ Combines multiple arrays  
✅ Creates shallow copies  
✅ Spreads strings into characters  
✅ **Rest (`...`)** - Bundles function arguments  
✅ Accepts variable number of parameters  
✅ Rest must be last parameter  

---

## Practice Exercises

### Exercise 1: Merge Three Arrays
Combine three arrays of numbers and find the maximum.

### Exercise 2: Sum Function
Create a function that sums unlimited numbers using rest.

### Exercise 3: Clone and Modify
Copy an array, add elements, without changing original.

### Exercise 4: Full Name Function
Create function accepting unlimited name parts (first, middle, last, etc.).

---

## Quick Reference

```javascript
// SPREAD - Unpack
let arr = [1, 2, 3];
console.log(...arr);           // 1 2 3
let max = Math.max(...arr);    // 3
let copy = [...arr];           // [1, 2, 3]
let merged = [...arr1, ...arr2];

// REST - Bundle
function sum(...nums) {
    // nums is an array
}
sum(1, 2, 3);

// Mixed Parameters
function greet(name, ...hobbies) {
    console.log(name);
    console.log(hobbies);
}
```

---

**Next: Chapters 20 & 21 - Dice Roller + Password Generator Projects**

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Chapters 16-17: Scope & Temperature](Chapters-16-17-Variable-Scope-and-Temperature-Conversion.md) | [📑 Index](../README.md) | [Chapters 20-21: Dice & Password Projects ▶️](Chapters-20-21-Dice-Roller-and-Password-Generator.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-18--19-arrays--spread--rest-operators)**

Made with ❤️ for JavaScript learners

</div>
