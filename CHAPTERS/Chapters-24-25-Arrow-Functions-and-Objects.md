# Chapters 24 & 25: Arrow Functions + JavaScript Objects

---

# Chapter 24: Arrow Functions

## Overview
Arrow functions provide a concise syntax for writing function expressions in JavaScript.

**Timestamp:** [04:16:52]

---

## 24.1 What are Arrow Functions?

**Timestamp:** [04:16:52]

Arrow functions are:
- A compact alternative to traditional function expressions
- Introduced in ES6 (2015)
- Use the "arrow" syntax `=>`
- Particularly useful for callbacks

**Syntax:**
```javascript
const functionName = (parameters) => expression;
```

---

## 24.2 Traditional vs Arrow Function

### Traditional Function Expression

```javascript
const greet = function(name) {
    return `Hello, ${name}!`;
};

console.log(greet("John")); // Hello, John!
```

### Arrow Function

**Timestamp:** [04:17:15]

```javascript
const greet = (name) => {
    return `Hello, ${name}!`;
};

console.log(greet("John")); // Hello, John!
```

---

## 24.3 Arrow Function Shortcuts

### Single Parameter (No Parentheses Needed)

**Timestamp:** [04:17:38]

```javascript
// With parentheses
const double = (x) => x * 2;

// Without parentheses (single parameter)
const double = x => x * 2;

console.log(double(5)); // 10
```

### Single Expression (Implicit Return)

**Timestamp:** [04:17:55]

```javascript
// With explicit return
const add = (a, b) => {
    return a + b;
};

// Implicit return (no curly braces needed)
const add = (a, b) => a + b;

console.log(add(3, 5)); // 8
```

### No Parameters

**Timestamp:** [04:18:12]

```javascript
const greet = () => console.log("Hello!");

greet(); // Hello!
```

---

## 24.4 Arrow Functions in Callbacks

Arrow functions shine when used as callbacks:

### forEach Example

**Timestamp:** [04:18:35]

```javascript
let numbers = [1, 2, 3, 4, 5];

// Traditional function
numbers.forEach(function(num) {
    console.log(num);
});

// Arrow function
numbers.forEach(num => console.log(num));
```

### map Example

**Timestamp:** [04:19:02]

```javascript
let numbers = [1, 2, 3, 4, 5];

// Traditional
let squared = numbers.map(function(num) {
    return num ** 2;
});

// Arrow (implicit return)
let squared = numbers.map(num => num ** 2);

console.log(squared); // [1, 4, 9, 16, 25]
```

### filter Example

**Timestamp:** [04:19:28]

```javascript
let numbers = [1, 2, 3, 4, 5, 6];

// Traditional
let evens = numbers.filter(function(num) {
    return num % 2 === 0;
});

// Arrow
let evens = numbers.filter(num => num % 2 === 0);

console.log(evens); // [2, 4, 6]
```

### reduce Example

**Timestamp:** [04:19:55]

```javascript
let numbers = [1, 2, 3, 4, 5];

// Traditional
let sum = numbers.reduce(function(acc, num) {
    return acc + num;
}, 0);

// Arrow
let sum = numbers.reduce((acc, num) => acc + num, 0);

console.log(sum); // 15
```

---

## 24.5 Multiple Statements (Need Curly Braces)

**Timestamp:** [04:20:22]

```javascript
const calculate = (a, b) => {
    let sum = a + b;
    let product = a * b;
    console.log(`Sum: ${sum}, Product: ${product}`);
    return sum;
};

calculate(5, 3);
// Sum: 15, Product: 15
// Returns: 8
```

---

## 24.6 Returning Objects

**Timestamp:** [04:20:48]

Wrap object in parentheses to avoid syntax confusion:

```javascript
// Incorrect (thinks {} is function body)
const makePerson = (name, age) => { name: name, age: age };

// Correct (wrap in parentheses)
const makePerson = (name, age) => ({ name: name, age: age });

// Or use shorthand property names
const makePerson = (name, age) => ({ name, age });

console.log(makePerson("John", 30));
// { name: "John", age: 30 }
```

---

## 24.7 Arrow Functions vs Regular Functions

### Key Differences

| Feature | Regular Function | Arrow Function |
|---------|-----------------|----------------|
| `this` binding | Has its own `this` | Inherits `this` from parent |
| `arguments` object | Has `arguments` | No `arguments` |
| Constructor | Can be constructor | Cannot be constructor |
| Method shorthand | Yes | Not recommended |

### This Binding Example

```javascript
const person = {
    name: "John",
    // Regular function (has own 'this')
    greet: function() {
        console.log(`Hello, ${this.name}`);
    },
    // Arrow function (inherits 'this')
    greetArrow: () => {
        console.log(`Hello, ${this.name}`); // undefined
    }
};

person.greet(); // Hello, John
person.greetArrow(); // Hello, undefined
```

---

## 24.8 When to Use Arrow Functions

### ✅ Use Arrow Functions:
- Callbacks (forEach, map, filter, reduce)
- Short, simple functions
- When you want to inherit `this` from parent scope
- Event handlers (in some cases)

### ❌ Avoid Arrow Functions:
- Object methods (use regular functions)
- When you need `arguments` object
- Constructor functions
- When you need dynamic `this` binding

---

## 24.9 Practical Examples

### Example 1: Sorting Array

```javascript
let numbers = [10, 5, 8, 1, 7];

// Ascending order
numbers.sort((a, b) => a - b);
console.log(numbers); // [1, 5, 7, 8, 10]

// Descending order
numbers.sort((a, b) => b - a);
console.log(numbers); // [10, 8, 7, 5, 1]
```

### Example 2: Chaining with Arrow Functions

```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let result = numbers
    .filter(n => n % 2 === 0)  // Keep evens
    .map(n => n ** 2)          // Square them
    .reduce((acc, n) => acc + n, 0); // Sum

console.log(result); // 220
```

### Example 3: setTimeout

```javascript
// Traditional
setTimeout(function() {
    console.log("Hello!");
}, 1000);

// Arrow
setTimeout(() => console.log("Hello!"), 1000);
```

### Example 4: Event Listener

```javascript
const button = document.getElementById("myButton");

// Arrow function
button.addEventListener("click", () => {
    console.log("Button clicked!");
});
```

---

## Summary - Chapter 24

✅ Arrow functions use `=>` syntax  
✅ Concise for simple functions  
✅ Implicit return for single expressions  
✅ No parentheses for single parameter  
✅ Perfect for callbacks  
✅ Inherits `this` from parent scope  
✅ Cannot be used as constructors  

---

# Chapter 25: JavaScript Objects

## Overview
Objects are collections of related properties and methods. They represent real-world entities with characteristics (properties) and behaviors (methods).

**Timestamp:** [04:47:31]

---

## 25.1 What are Objects?

**Timestamp:** [04:47:31], [04:47:37]

Objects are:
- Collections of related **properties** and/or **methods**
- Represent "things" in the real world
- Written as `key: value` pairs
- Enclosed in curly braces `{}`

---

## 25.2 Creating Objects

**Timestamp:** [04:47:51]

### Object Literal Syntax

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
    isEmployed: true
};
```

**Timestamp:** [04:48:05], [04:48:18], [04:48:31], [04:48:44]

---

## 25.3 Accessing Properties

**Timestamp:** [04:48:58]

### Dot Notation

```javascript
console.log(person.firstName); // "John"
console.log(person.age);       // 30
```

### Bracket Notation

```javascript
console.log(person["firstName"]); // "John"
console.log(person["age"]);       // 30
```

**When to use bracket notation:**
- Property name has spaces or special characters
- Property name is stored in a variable
- Property name is computed dynamically

---

## 25.4 Modifying Properties

**Timestamp:** [04:49:18]

```javascript
const person = {
    firstName: "John",
    age: 30
};

// Change existing property
person.age = 31;
console.log(person.age); // 31

// Add new property
person.email = "john@example.com";
console.log(person.email); // "john@example.com"
```

---

## 25.5 Object Methods

**Timestamp:** [04:49:42]

**Methods** are functions defined inside objects:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
    
    // Method
    greet: function() {
        console.log(`Hello, my name is ${this.firstName}`);
    }
};

person.greet(); // "Hello, my name is John"
```

**Timestamp:** [04:50:02], [04:50:18]

---

## 25.6 The "this" Keyword

**Timestamp:** [04:50:35]

`this` refers to the **object** the method belongs to:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    
    getFullName: function() {
        return `${this.firstName} ${this.lastName}`;
    }
};

console.log(person.getFullName()); // "John Doe"
```

**Timestamp:** [04:50:48], [04:51:05]

---

## 25.7 Method Shorthand (ES6)

**Timestamp:** [04:51:22]

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    
    // Old way
    greet: function() {
        console.log("Hello!");
    },
    
    // ES6 shorthand
    sayGoodbye() {
        console.log("Goodbye!");
    }
};

person.greet();      // "Hello!"
person.sayGoodbye(); // "Goodbye!"
```

---

## 25.8 Complete Object Example

**Timestamp:** [04:51:45]

```javascript
const person = {
    // Properties
    firstName: "John",
    lastName: "Doe",
    age: 30,
    isEmployed: true,
    hobbies: ["reading", "gaming", "cooking"],
    address: {
        street: "123 Main St",
        city: "Boston",
        state: "MA"
    },
    
    // Methods
    greet() {
        console.log(`Hello, I'm ${this.firstName}!`);
    },
    
    getFullName() {
        return `${this.firstName} ${this.lastName}`;
    },
    
    haveBirthday() {
        this.age++;
        console.log(`Happy Birthday! Now ${this.age} years old.`);
    }
};

// Using the object
person.greet();                    // "Hello, I'm John!"
console.log(person.getFullName()); // "John Doe"
person.haveBirthday();             // "Happy Birthday! Now 31 years old."
console.log(person.hobbies[0]);    // "reading"
console.log(person.address.city);  // "Boston"
```

**Timestamp:** [04:52:08], [04:52:32], [04:52:55]

---

## 25.9 Arrays of Objects

**Timestamp:** [04:53:18]

```javascript
const people = [
    {
        firstName: "John",
        lastName: "Doe",
        age: 30
    },
    {
        firstName: "Jane",
        lastName: "Smith",
        age: 25
    },
    {
        firstName: "Bob",
        lastName: "Johnson",
        age: 35
    }
];

// Access objects in array
console.log(people[0].firstName); // "John"
console.log(people[1].age);       // 25

// Loop through array of objects
people.forEach(person => {
    console.log(`${person.firstName} is ${person.age} years old`);
});
// John is 30 years old
// Jane is 25 years old
// Bob is 35 years old
```

**Timestamp:** [04:53:35], [04:53:52]

---

## 25.10 Object Destructuring

**Timestamp:** [04:54:12]

Extract properties into variables:

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

// Without destructuring
const firstName = person.firstName;
const age = person.age;

// With destructuring
const { firstName, age } = person;

console.log(firstName); // "John"
console.log(age);       // 30
```

---

## 25.11 Practical Examples

### Example 1: Car Object

```javascript
const car = {
    make: "Toyota",
    model: "Camry",
    year: 2023,
    color: "blue",
    mileage: 5000,
    
    drive(distance) {
        this.mileage += distance;
        console.log(`Drove ${distance} miles. Total: ${this.mileage}`);
    },
    
    getInfo() {
        return `${this.year} ${this.make} ${this.model} - ${this.color}`;
    }
};

console.log(car.getInfo()); // "2023 Toyota Camry - blue"
car.drive(100);             // "Drove 100 miles. Total: 5100"
```

### Example 2: Shopping Cart

```javascript
const cart = {
    items: [],
    
    addItem(name, price, quantity) {
        this.items.push({ name, price, quantity });
        console.log(`Added ${quantity}x ${name}`);
    },
    
    getTotal() {
        return this.items.reduce((total, item) => {
            return total + (item.price * item.quantity);
        }, 0);
    },
    
    display() {
        console.log("Cart Items:");
        this.items.forEach(item => {
            console.log(`${item.name}: $${item.price} x ${item.quantity}`);
        });
        console.log(`Total: $${this.getTotal().toFixed(2)}`);
    }
};

cart.addItem("Apple", 0.99, 5);
cart.addItem("Bread", 2.50, 2);
cart.display();
// Cart Items:
// Apple: $0.99 x 5
// Bread: $2.50 x 2
// Total: $9.95
```

### Example 3: Bank Account

```javascript
const account = {
    owner: "John Doe",
    balance: 1000,
    
    deposit(amount) {
        if (amount > 0) {
            this.balance += amount;
            console.log(`Deposited $${amount}. New balance: $${this.balance}`);
        }
    },
    
    withdraw(amount) {
        if (amount > 0 && amount <= this.balance) {
            this.balance -= amount;
            console.log(`Withdrew $${amount}. New balance: $${this.balance}`);
        } else {
            console.log("Insufficient funds!");
        }
    },
    
    getBalance() {
        return this.balance;
    }
};

account.deposit(500);   // Deposited $500. New balance: $1500
account.withdraw(200);  // Withdrew $200. New balance: $1300
console.log(account.getBalance()); // 1300
```

---

## 25.12 Object.keys(), Object.values(), Object.entries()

**Timestamp:** [04:54:38]

```javascript
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30
};

// Get all keys
console.log(Object.keys(person));
// ["firstName", "lastName", "age"]

// Get all values
console.log(Object.values(person));
// ["John", "Doe", 30]

// Get key-value pairs
console.log(Object.entries(person));
// [["firstName", "John"], ["lastName", "Doe"], ["age", 30]]
```

---

## 25.13 Comparing Objects

Objects are compared by **reference**, not value:

```javascript
const obj1 = { name: "John" };
const obj2 = { name: "John" };
const obj3 = obj1;

console.log(obj1 === obj2); // false (different objects)
console.log(obj1 === obj3); // true (same reference)
```

---

## Summary - Chapter 25

✅ Objects store related data and functions  
✅ Properties are **key: value** pairs  
✅ Methods are functions in objects  
✅ `this` refers to the object  
✅ Access with dot or bracket notation  
✅ Can nest objects and arrays  
✅ Arrays can contain objects  
✅ Objects compared by reference  

---

## Practice Exercises

### Exercise 1: Student Object
Create a student object with name, grades array, and a method to calculate average.

### Exercise 2: Product Catalog
Create an array of product objects with methods to filter by price range.

### Exercise 3: Todo List
Create a todo object with add, remove, and display methods.

### Exercise 4: Calculator Object
Create a calculator with methods for add, subtract, multiply, divide.

---

## Quick Reference

```javascript
// Create object
const obj = {
    property: value,
    method() {
        // code
    }
};

// Access properties
obj.property
obj["property"]

// Modify
obj.property = newValue;

// Methods
obj.method();

// "this" refers to object
this.property

// Object utilities
Object.keys(obj)
Object.values(obj)
Object.entries(obj)

// Destructuring
const { prop1, prop2 } = obj;
```

---

**Next: Chapters 26 & 27 - Constructors + Classes**
