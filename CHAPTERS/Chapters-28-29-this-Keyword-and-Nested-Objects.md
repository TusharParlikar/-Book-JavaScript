# Chapters 28 & 29: this Keyword + Nested Objects

---

# Chapter 28: The "this" Keyword

## Overview
The `this` keyword references the object that is executing the current function or code. Its value depends on the context in which it's used.

**Timestamp:** [05:10:42]

---

## 28.1 What is "this"?

**Timestamp:** [05:10:42], [05:10:49]

`this` is a reference to:
- The object **currently executing** the code
- Context-dependent (changes based on how function is called)
- In objects: refers to the object itself
- In global scope: refers to `window` (browser) or `global` (Node.js)

---

## 28.2 "this" in Object Methods

**Timestamp:** [05:11:08]

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
    
    greet() {
        console.log(`Hello, I'm ${this.firstName}`);
        // "this" refers to the person object
    },
    
    getFullName() {
        return `${this.firstName} ${this.lastName}`;
    },
    
    haveBirthday() {
        this.age++;
        console.log(`Now ${this.age} years old`);
    }
};

person.greet();                    // "Hello, I'm John"
console.log(person.getFullName()); // "John Doe"
person.haveBirthday();             // "Now 31 years old"
```

**Timestamp:** [05:11:32]

---

## 28.3 "this" in Regular Functions

**Timestamp:** [05:11:58]

```javascript
function showThis() {
    console.log(this);
}

showThis(); // Window object (in browser) or global (in Node.js)
```

In **strict mode**:

```javascript
"use strict";

function showThis() {
    console.log(this);
}

showThis(); // undefined
```

---

## 28.4 "this" in Arrow Functions

**Timestamp:** [05:12:25]

Arrow functions **don't have their own `this`**. They inherit `this` from the parent scope:

```javascript
const person = {
    name: "John",
    
    // Regular function - has own "this"
    greet: function() {
        console.log(`Hello, ${this.name}`);
    },
    
    // Arrow function - inherits "this" from parent
    greetArrow: () => {
        console.log(`Hello, ${this.name}`); // undefined!
    }
};

person.greet();      // "Hello, John"
person.greetArrow(); // "Hello, undefined"
```

**Timestamp:** [05:12:48]

---

## 28.5 "this" in Event Handlers

**Timestamp:** [05:13:15]

```javascript
const button = document.getElementById("myButton");

// Regular function - "this" refers to button element
button.addEventListener("click", function() {
    console.log(this); // <button id="myButton">
    this.style.backgroundColor = "blue";
});

// Arrow function - "this" refers to parent scope
button.addEventListener("click", () => {
    console.log(this); // Window object
    // this.style.backgroundColor = "blue"; // Won't work!
});
```

---

## 28.6 "this" in Classes

**Timestamp:** [05:13:42]

```javascript
class Person {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
    
    greet() {
        console.log(`Hello, I'm ${this.firstName}`);
        // "this" refers to the instance
    }
    
    delayedGreet() {
        setTimeout(function() {
            console.log(`Hello, ${this.firstName}`);
            // "this" is undefined (or window) in regular function
        }, 1000);
    }
    
    delayedGreetFixed() {
        setTimeout(() => {
            console.log(`Hello, ${this.firstName}`);
            // Arrow function inherits "this" from class method
        }, 1000);
    }
}

const person = new Person("John", "Doe");
person.greet();              // "Hello, I'm John"
person.delayedGreet();       // "Hello, undefined"
person.delayedGreetFixed();  // "Hello, I'm John"
```

**Timestamp:** [05:14:08]

---

## 28.7 Binding "this"

### bind() Method

**Timestamp:** [05:14:35]

```javascript
const person = {
    name: "John",
    greet() {
        console.log(`Hello, ${this.name}`);
    }
};

const greetFunction = person.greet;
greetFunction(); // "Hello, undefined" (loses context)

const boundGreet = person.greet.bind(person);
boundGreet(); // "Hello, John" (bound to person)
```

### call() Method

**Timestamp:** [05:15:02]

```javascript
function greet(greeting, punctuation) {
    console.log(`${greeting}, ${this.name}${punctuation}`);
}

const person = { name: "John" };

greet.call(person, "Hello", "!"); // "Hello, John!"
```

### apply() Method

**Timestamp:** [05:15:28]

```javascript
function greet(greeting, punctuation) {
    console.log(`${greeting}, ${this.name}${punctuation}`);
}

const person = { name: "John" };

greet.apply(person, ["Hello", "!"]); // "Hello, John!"
// Like call() but arguments in array
```

---

## 28.8 Common "this" Pitfalls

### Pitfall 1: Losing Context

```javascript
const person = {
    name: "John",
    greet() {
        console.log(`Hello, ${this.name}`);
    }
};

const greet = person.greet;
greet(); // Error or undefined - lost context!

// Fix: Use bind
const boundGreet = person.greet.bind(person);
boundGreet(); // "Hello, John"
```

### Pitfall 2: Arrow Functions in Methods

```javascript
const person = {
    name: "John",
    greet: () => {
        console.log(`Hello, ${this.name}`); // undefined!
    }
};

// Fix: Use regular function
const person = {
    name: "John",
    greet() {
        console.log(`Hello, ${this.name}`); // "Hello, John"
    }
};
```

### Pitfall 3: Callbacks Losing Context

```javascript
class Counter {
    constructor() {
        this.count = 0;
    }
    
    increment() {
        setTimeout(function() {
            this.count++; // Error! "this" is undefined
        }, 1000);
    }
    
    incrementFixed() {
        setTimeout(() => {
            this.count++; // Works! Arrow function inherits "this"
        }, 1000);
    }
}
```

---

## 28.9 "this" Rules Summary

1. **Global context:** `this` = `window` (browser) or `global` (Node.js)
2. **Object method:** `this` = object owning the method
3. **Regular function:** `this` = `undefined` (strict mode) or global object
4. **Arrow function:** `this` = inherited from parent scope
5. **Event handler:** `this` = element that received the event
6. **Class method:** `this` = instance of the class
7. **Explicitly bound:** `this` = whatever you bind it to (bind/call/apply)

---

## Summary - Chapter 28

✅ `this` refers to execution context  
✅ In methods: refers to object  
✅ Regular functions: have own `this`  
✅ Arrow functions: inherit `this`  
✅ Can lose context when passing methods  
✅ Use `bind()`, `call()`, or `apply()` to set `this`  
✅ Arrow functions good for callbacks  

---

# Chapter 29: Nested Objects & Arrays of Objects

## Overview
Objects can contain other objects (nested objects) and arrays can contain objects, allowing complex data structures.

**Timestamp:** [06:10:14], [06:19:25]

---

## 29.1 Nested Objects

**Timestamp:** [06:10:14]

Objects can contain other objects as properties:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
    address: {
        street: "123 Main St",
        city: "Boston",
        state: "MA",
        zipCode: "02101"
    }
};
```

**Timestamp:** [06:10:23], [06:11:55]

---

## 29.2 Accessing Nested Properties

**Timestamp:** [06:13:26]

### Dot Notation

```javascript
console.log(person.address.street);  // "123 Main St"
console.log(person.address.city);    // "Boston"
console.log(person.address.zipCode); // "02101"
```

### Bracket Notation

```javascript
console.log(person["address"]["street"]); // "123 Main St"
```

---

## 29.3 Iterating Through Nested Objects

**Timestamp:** [06:14:02]

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    address: {
        street: "123 Main St",
        city: "Boston",
        state: "MA"
    }
};

// Iterate through address properties
for (const key in person.address) {
    console.log(`${key}: ${person.address[key]}`);
}
// Output:
// street: 123 Main St
// city: Boston
// state: MA
```

---

## 29.4 Nested Objects with Classes

**Timestamp:** [06:14:44]

```javascript
class Address {
    constructor(street, city, state, zipCode) {
        this.street = street;
        this.city = city;
        this.state = state;
        this.zipCode = zipCode;
    }
    
    getFullAddress() {
        return `${this.street}, ${this.city}, ${this.state} ${this.zipCode}`;
    }
}

class Person {
    constructor(firstName, lastName, street, city, state, zipCode) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.address = new Address(street, city, state, zipCode);
    }
    
    getInfo() {
        return `${this.firstName} ${this.lastName} lives at ${this.address.getFullAddress()}`;
    }
}

const person = new Person("John", "Doe", "123 Main St", "Boston", "MA", "02101");
console.log(person.getInfo());
// "John Doe lives at 123 Main St, Boston, MA 02101"
```

---

## 29.5 Arrays of Objects

**Timestamp:** [06:19:25]

Arrays where each element is an object:

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

## 29.6 Accessing Array of Objects

**Timestamp:** [06:20:51]

```javascript
// Access first fruit's name
console.log(fruits[0].name); // "Apple"

// Access second fruit's color
console.log(fruits[1].color); // "yellow"

// Access third fruit's calories
console.log(fruits[2].calories); // 62
```

---

## 29.7 Manipulating Arrays of Objects

**Timestamp:** [06:21:46]

```javascript
// Add new fruit
fruits.push({ name: "Mango", color: "yellow", calories: 99 });

// Remove last fruit
fruits.pop();

// Remove specific fruit
fruits.splice(1, 1); // Remove banana
```

---

## 29.8 forEach with Objects

**Timestamp:** [06:22:57]

```javascript
fruits.forEach(fruit => {
    console.log(`${fruit.name} is ${fruit.color} and has ${fruit.calories} calories`);
});

// Output:
// Apple is red and has 95 calories
// Banana is yellow and has 105 calories
// Orange is orange and has 62 calories
// Grape is purple and has 67 calories
```

---

## 29.9 map with Objects

**Timestamp:** [06:23:34]

```javascript
// Extract just the names
const fruitNames = fruits.map(fruit => fruit.name);
console.log(fruitNames);
// ["Apple", "Banana", "Orange", "Grape"]

// Extract just the calories
const calories = fruits.map(fruit => fruit.calories);
console.log(calories);
// [95, 105, 62, 67]

// Create formatted strings
const formatted = fruits.map(fruit => `${fruit.name} (${fruit.calories} cal)`);
console.log(formatted);
// ["Apple (95 cal)", "Banana (105 cal)", "Orange (62 cal)", "Grape (67 cal)"]
```

---

## 29.10 filter with Objects

**Timestamp:** [06:24:47]

```javascript
// Get fruits with less than 100 calories
const lowCalFruits = fruits.filter(fruit => fruit.calories < 100);
console.log(lowCalFruits);
// [{ name: "Apple", color: "red", calories: 95 }, 
//  { name: "Orange", color: "orange", calories: 62 },
//  { name: "Grape", color: "purple", calories: 67 }]

// Get yellow fruits
const yellowFruits = fruits.filter(fruit => fruit.color === "yellow");
console.log(yellowFruits);
// [{ name: "Banana", color: "yellow", calories: 105 }]

// Get fruit names with low calories
const lowCalNames = fruits
    .filter(fruit => fruit.calories < 100)
    .map(fruit => fruit.name);
console.log(lowCalNames);
// ["Apple", "Orange", "Grape"]
```

---

## 29.11 reduce with Objects

**Timestamp:** [06:26:33]

```javascript
// Find fruit with maximum calories
const maxCalFruit = fruits.reduce((max, fruit) => {
    return fruit.calories > max.calories ? fruit : max;
}, fruits[0]);

console.log(maxCalFruit);
// { name: "Banana", color: "yellow", calories: 105 }

// Calculate total calories
const totalCalories = fruits.reduce((total, fruit) => {
    return total + fruit.calories;
}, 0);

console.log(totalCalories); // 329
```

---

## 29.12 Complex Example: Student Management

```javascript
const students = [
    {
        id: 1,
        name: "John Doe",
        age: 20,
        grades: {
            math: 85,
            english: 92,
            science: 88
        },
        address: {
            city: "Boston",
            state: "MA"
        }
    },
    {
        id: 2,
        name: "Jane Smith",
        age: 22,
        grades: {
            math: 95,
            english: 88,
            science: 91
        },
        address: {
            city: "New York",
            state: "NY"
        }
    },
    {
        id: 3,
        name: "Bob Johnson",
        age: 21,
        grades: {
            math: 78,
            english: 85,
            science: 82
        },
        address: {
            city: "Boston",
            state: "MA"
        }
    }
];

// Calculate average grade for each student
students.forEach(student => {
    const grades = Object.values(student.grades);
    const average = grades.reduce((sum, grade) => sum + grade, 0) / grades.length;
    console.log(`${student.name}: ${average.toFixed(2)}`);
});

// Find students from Boston
const bostonStudents = students.filter(student => student.address.city === "Boston");
console.log(bostonStudents.map(s => s.name));
// ["John Doe", "Bob Johnson"]

// Find student with highest math grade
const bestMathStudent = students.reduce((best, student) => {
    return student.grades.math > best.grades.math ? student : best;
});
console.log(bestMathStudent.name); // "Jane Smith"
```

---

## 29.13 Practical Example: Product Catalog

```javascript
const products = [
    {
        id: 1,
        name: "Laptop",
        price: 999.99,
        specs: {
            cpu: "Intel i7",
            ram: "16GB",
            storage: "512GB SSD"
        },
        inStock: true
    },
    {
        id: 2,
        name: "Phone",
        price: 699.99,
        specs: {
            cpu: "Snapdragon 888",
            ram: "8GB",
            storage: "128GB"
        },
        inStock: false
    },
    {
        id: 3,
        name: "Tablet",
        price: 449.99,
        specs: {
            cpu: "Apple M1",
            ram: "8GB",
            storage: "256GB"
        },
        inStock: true
    }
];

// Get available products
const availableProducts = products.filter(p => p.inStock);
console.log(availableProducts.map(p => p.name));
// ["Laptop", "Tablet"]

// Calculate total inventory value (in-stock items)
const totalValue = products
    .filter(p => p.inStock)
    .reduce((total, p) => total + p.price, 0);
console.log(`Total inventory value: $${totalValue.toFixed(2)}`);
// "Total inventory value: $1449.98"

// Display product details
products.forEach(product => {
    console.log(`${product.name} - $${product.price}`);
    console.log(`  CPU: ${product.specs.cpu}`);
    console.log(`  RAM: ${product.specs.ram}`);
    console.log(`  Storage: ${product.specs.storage}`);
    console.log(`  Status: ${product.inStock ? "In Stock" : "Out of Stock"}`);
});
```

---

## Summary - Chapter 29

✅ Objects can contain other objects (nesting)  
✅ Access nested properties with dot notation  
✅ Arrays can contain objects  
✅ Use array methods (forEach, map, filter, reduce) with objects  
✅ Combine methods for complex operations  
✅ Iterate through nested structures  
✅ Classes can have nested object properties  

---

## Practice Exercises

### Exercise 1: Company Structure
Create nested objects representing company departments with employees.

### Exercise 2: Shopping Cart
Create array of product objects with nested properties, calculate totals.

### Exercise 3: School System
Create classes for School, Class, and Student with nested relationships.

### Exercise 4: Blog Posts
Create array of blog post objects with nested author and comments objects.

---

## Quick Reference

```javascript
// Nested Objects
const obj = {
    prop: "value",
    nested: {
        prop: "value"
    }
};
obj.nested.prop

// Array of Objects
const arr = [
    { name: "John", age: 30 },
    { name: "Jane", age: 25 }
];

// forEach
arr.forEach(item => console.log(item.name));

// map
const names = arr.map(item => item.name);

// filter
const filtered = arr.filter(item => item.age > 25);

// reduce
const total = arr.reduce((sum, item) => sum + item.age, 0);

// Chaining
const result = arr
    .filter(item => item.age > 25)
    .map(item => item.name);
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Constructors & Classes](Chapters-26-27-Constructors-and-Classes.md) | [📑 Index](../README.md) | [Arrays of Objects & Sorting ▶️](Chapters-30-31-Arrays-of-Objects-and-Sorting.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-28--29-this-keyword--nested-objects)**

Made with ❤️ for JavaScript learners

</div>

**Next: Chapters 30 & 31 - Arrays of Objects + Sorting**
