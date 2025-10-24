# Chapters 26 & 27: Constructors + Classes

---

# Chapter 26: Constructors

## Overview
Constructors are special functions used to create and initialize objects with similar properties and methods.

**Timestamp:** [04:55:08]

---

## 26.1 What are Constructors?

**Timestamp:** [04:55:08], [04:55:15]

Constructors are:
- Special functions for creating objects
- Define properties and methods for an object type
- Use the `new` keyword to create instances
- Convention: Start with capital letter

---

## 26.2 Creating a Constructor

**Timestamp:** [04:55:32]

```javascript
function Person(firstName, lastName, age) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
}
```

**Timestamp:** [04:55:48], [04:56:05], [04:56:18]

---

## 26.3 Creating Objects with Constructors

**Timestamp:** [04:56:35]

```javascript
const person1 = new Person("John", "Doe", 30);
const person2 = new Person("Jane", "Smith", 25);
const person3 = new Person("Bob", "Johnson", 35);

console.log(person1.firstName); // "John"
console.log(person2.age);       // 25
console.log(person3.lastName);  // "Johnson"
```

**Timestamp:** [04:56:52], [04:57:08]

---

## 26.4 Adding Methods to Constructors

**Timestamp:** [04:57:25]

```javascript
function Person(firstName, lastName, age) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
    
    this.greet = function() {
        console.log(`Hello, I'm ${this.firstName}!`);
    };
    
    this.getFullName = function() {
        return `${this.firstName} ${this.lastName}`;
    };
}

const person1 = new Person("John", "Doe", 30);
person1.greet(); // "Hello, I'm John!"
console.log(person1.getFullName()); // "John Doe"
```

**Timestamp:** [04:57:42], [04:58:02]

---

## 26.5 Complete Constructor Example

**Timestamp:** [04:58:22]

```javascript
function Car(make, model, year, color) {
    this.make = make;
    this.model = model;
    this.year = year;
    this.color = color;
    this.mileage = 0;
    
    this.drive = function(distance) {
        this.mileage += distance;
        console.log(`${this.make} ${this.model} drove ${distance} miles`);
    };
    
    this.getInfo = function() {
        return `${this.year} ${this.color} ${this.make} ${this.model}`;
    };
}

const car1 = new Car("Toyota", "Camry", 2023, "blue");
const car2 = new Car("Honda", "Accord", 2022, "red");

car1.drive(100);
// "Toyota Camry drove 100 miles"

console.log(car2.getInfo());
// "2022 red Honda Accord"
```

**Timestamp:** [04:58:45], [04:59:08]

---

## 26.6 Constructor Best Practices

### ✅ Do:
- Start constructor names with capital letter
- Use `this` to assign properties
- Always use `new` keyword
- Keep constructors simple

### ❌ Avoid:
- Forgetting `new` keyword
- Lowercase constructor names
- Complex logic in constructors

---

## 26.7 Problem: Memory Inefficiency

**Timestamp:** [04:59:32]

Each object gets its own copy of methods:

```javascript
function Person(name) {
    this.name = name;
    this.greet = function() {
        console.log(`Hello, ${this.name}`);
    };
}

const person1 = new Person("John");
const person2 = new Person("Jane");

// Each has separate greet function
console.log(person1.greet === person2.greet); // false
```

**Solution:** Use prototypes (or classes) to share methods.

---

## Summary - Chapter 26

✅ Constructors create similar objects  
✅ Use capital letter naming  
✅ Use `new` keyword  
✅ `this` refers to new object  
✅ Can add properties and methods  
✅ Each instance is unique  
✅ Methods are duplicated (memory issue)  

---

# Chapter 27: Classes

## Overview
Classes provide a cleaner, more organized way to create objects with shared methods. They're syntactic sugar over constructors and prototypes.

**Timestamp:** [05:00:15]

---

## 27.1 What are Classes?

**Timestamp:** [05:00:15], [05:00:22]

Classes:
- Blueprint for creating objects (ES6 feature)
- More organized than constructors
- Use `class` keyword
- Define properties and methods
- Use `constructor` method for initialization

---

## 27.2 Creating a Class

**Timestamp:** [05:00:42]

```javascript
class Person {
    constructor(firstName, lastName, age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
}
```

**Timestamp:** [05:01:02], [05:01:18]

---

## 27.3 Creating Objects from Classes

**Timestamp:** [05:01:35]

```javascript
class Person {
    constructor(firstName, lastName, age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
}

const person1 = new Person("John", "Doe", 30);
const person2 = new Person("Jane", "Smith", 25);

console.log(person1.firstName); // "John"
console.log(person2.age);       // 25
```

**Timestamp:** [05:01:52]

---

## 27.4 Adding Methods to Classes

**Timestamp:** [05:02:12]

```javascript
class Person {
    constructor(firstName, lastName, age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
    
    greet() {
        console.log(`Hello, I'm ${this.firstName}!`);
    }
    
    getFullName() {
        return `${this.firstName} ${this.lastName}`;
    }
    
    haveBirthday() {
        this.age++;
        console.log(`Happy Birthday! Now ${this.age} years old.`);
    }
}

const person1 = new Person("John", "Doe", 30);
person1.greet();                    // "Hello, I'm John!"
console.log(person1.getFullName()); // "John Doe"
person1.haveBirthday();             // "Happy Birthday! Now 31 years old."
```

**Timestamp:** [05:02:32], [05:02:55], [05:03:18]

---

## 27.5 Complete Class Example: Car

**Timestamp:** [05:03:42]

```javascript
class Car {
    constructor(make, model, year, color) {
        this.make = make;
        this.model = model;
        this.year = year;
        this.color = color;
        this.mileage = 0;
    }
    
    drive(distance) {
        this.mileage += distance;
        console.log(`${this.make} ${this.model} drove ${distance} miles`);
        console.log(`Total mileage: ${this.mileage}`);
    }
    
    paint(newColor) {
        this.color = newColor;
        console.log(`Car painted ${newColor}`);
    }
    
    getInfo() {
        return `${this.year} ${this.color} ${this.make} ${this.model}`;
    }
    
    getAge() {
        const currentYear = new Date().getFullYear();
        return currentYear - this.year;
    }
}

const car1 = new Car("Toyota", "Camry", 2023, "blue");
const car2 = new Car("Honda", "Accord", 2020, "red");

car1.drive(150);
// Toyota Camry drove 150 miles
// Total mileage: 150

car2.paint("black");
// Car painted black

console.log(car1.getInfo());
// "2023 blue Toyota Camry"

console.log(car2.getAge());
// 4 (or current year - 2020)
```

**Timestamp:** [05:04:05], [05:04:28]

---

## 27.6 Static Methods

**Timestamp:** [05:04:52]

Static methods belong to the class itself, not instances:

```javascript
class MathHelper {
    static add(a, b) {
        return a + b;
    }
    
    static multiply(a, b) {
        return a * b;
    }
    
    static PI = 3.14159;
}

// Call on class, not instance
console.log(MathHelper.add(5, 3));      // 8
console.log(MathHelper.multiply(4, 6)); // 24
console.log(MathHelper.PI);             // 3.14159

// Cannot call on instance
const helper = new MathHelper();
// helper.add(5, 3); // Error!
```

**Timestamp:** [05:05:15]

---

## 27.7 Getters and Setters

**Timestamp:** [05:05:42]

### Getters

**Timestamp:** [05:06:02]

```javascript
class Circle {
    constructor(radius) {
        this.radius = radius;
    }
    
    get diameter() {
        return this.radius * 2;
    }
    
    get area() {
        return Math.PI * this.radius ** 2;
    }
}

const circle = new Circle(5);

// Access like properties (no parentheses)
console.log(circle.diameter); // 10
console.log(circle.area);     // 78.54
```

**Timestamp:** [05:06:25]

### Setters

**Timestamp:** [05:06:48]

```javascript
class Person {
    constructor(firstName, lastName) {
        this._firstName = firstName;
        this._lastName = lastName;
    }
    
    get fullName() {
        return `${this._firstName} ${this._lastName}`;
    }
    
    set fullName(name) {
        const parts = name.split(' ');
        this._firstName = parts[0];
        this._lastName = parts[1];
    }
}

const person = new Person("John", "Doe");

console.log(person.fullName); // "John Doe"

// Use setter like property assignment
person.fullName = "Jane Smith";
console.log(person.fullName); // "Jane Smith"
```

**Timestamp:** [05:07:12]

---

## 27.8 Private Fields (ES2022)

**Timestamp:** [05:07:38]

```javascript
class BankAccount {
    #balance; // Private field
    
    constructor(owner, initialBalance) {
        this.owner = owner;
        this.#balance = initialBalance;
    }
    
    deposit(amount) {
        if (amount > 0) {
            this.#balance += amount;
            console.log(`Deposited $${amount}`);
        }
    }
    
    withdraw(amount) {
        if (amount > 0 && amount <= this.#balance) {
            this.#balance -= amount;
            console.log(`Withdrew $${amount}`);
        } else {
            console.log("Insufficient funds!");
        }
    }
    
    getBalance() {
        return this.#balance;
    }
}

const account = new BankAccount("John", 1000);
account.deposit(500);
console.log(account.getBalance()); // 1500

// Cannot access private field directly
// console.log(account.#balance); // Error!
```

**Timestamp:** [05:08:02]

---

## 27.9 Inheritance

**Timestamp:** [05:08:32]

Classes can inherit from other classes:

```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }
    
    speak() {
        console.log(`${this.name} makes a sound`);
    }
}

class Dog extends Animal {
    constructor(name, breed) {
        super(name); // Call parent constructor
        this.breed = breed;
    }
    
    speak() {
        console.log(`${this.name} barks`);
    }
    
    fetch() {
        console.log(`${this.name} fetches the ball`);
    }
}

class Cat extends Animal {
    constructor(name, color) {
        super(name);
        this.color = color;
    }
    
    speak() {
        console.log(`${this.name} meows`);
    }
}

const dog = new Dog("Buddy", "Golden Retriever");
const cat = new Cat("Whiskers", "orange");

dog.speak();  // "Buddy barks"
dog.fetch();  // "Buddy fetches the ball"
cat.speak();  // "Whiskers meows"
```

**Timestamp:** [05:08:55], [05:09:18], [05:09:42]

---

## 27.10 Practical Example: Student Management

**Timestamp:** [05:10:05]

```javascript
class Student {
    constructor(name, age, gpa) {
        this.name = name;
        this.age = age;
        this.gpa = gpa;
        this.grades = [];
    }
    
    addGrade(subject, grade) {
        this.grades.push({ subject, grade });
        this.updateGPA();
    }
    
    updateGPA() {
        if (this.grades.length === 0) return;
        
        const sum = this.grades.reduce((acc, item) => acc + item.grade, 0);
        this.gpa = (sum / this.grades.length).toFixed(2);
    }
    
    getInfo() {
        return `${this.name}, Age: ${this.age}, GPA: ${this.gpa}`;
    }
    
    displayGrades() {
        console.log(`${this.name}'s Grades:`);
        this.grades.forEach(item => {
            console.log(`  ${item.subject}: ${item.grade}`);
        });
    }
}

const student1 = new Student("John Doe", 20, 0);
student1.addGrade("Math", 85);
student1.addGrade("English", 92);
student1.addGrade("Science", 88);

console.log(student1.getInfo());
// "John Doe, Age: 20, GPA: 88.33"

student1.displayGrades();
// John Doe's Grades:
//   Math: 85
//   English: 92
//   Science: 88
```

---

## 27.11 Constructor vs Class Comparison

| Feature | Constructor | Class |
|---------|------------|-------|
| Syntax | Function-based | Class keyword |
| Methods | In constructor or prototype | Inside class body |
| Inheritance | Prototype chain | `extends` keyword |
| Readability | Less clear | More organized |
| Private fields | No native support | `#field` syntax |
| Static methods | Add to function | `static` keyword |

---

## 27.12 When to Use Classes

### ✅ Use Classes:
- Creating multiple similar objects
- Need inheritance
- Complex objects with many methods
- Modern codebases (ES6+)
- Need private fields

### ❌ Avoid Classes:
- Simple one-off objects (use object literals)
- Functional programming style
- Very simple data structures

---

## Summary - Chapter 27

✅ Classes are blueprints for objects  
✅ Use `constructor` method  
✅ Methods defined in class body  
✅ Use `new` keyword to create instances  
✅ `static` methods belong to class  
✅ `get`/`set` for computed properties  
✅ `#field` for private properties  
✅ `extends` for inheritance  
✅ `super()` calls parent constructor  

---

## Practice Exercises

### Exercise 1: Rectangle Class
Create class with width, height, getArea(), getPerimeter() methods.

### Exercise 2: Library System
Create Book and Library classes with add/remove/search methods.

### Exercise 3: Employee Hierarchy
Create Employee base class, Manager and Developer subclasses with inheritance.

### Exercise 4: Shopping Cart
Create Product and ShoppingCart classes with add/remove/total methods.

---

## Quick Reference

```javascript
// Constructor (old way)
function Person(name) {
    this.name = name;
    this.greet = function() {
        console.log(`Hello, ${this.name}`);
    };
}

// Class (modern way)
class Person {
    constructor(name) {
        this.name = name;
    }
    
    greet() {
        console.log(`Hello, ${this.name}`);
    }
    
    static info() {
        return "This is a Person class";
    }
    
    get age() {
        return this._age;
    }
    
    set age(value) {
        this._age = value;
    }
}

// Inheritance
class Student extends Person {
    constructor(name, grade) {
        super(name);
        this.grade = grade;
    }
}

// Create instances
const person = new Person("John");
const student = new Student("Jane", "A");
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Arrow Functions & Objects](Chapters-24-25-Arrow-Functions-and-Objects.md) | [📑 Index](../README.md) | [this Keyword & Nested Objects ▶️](Chapters-28-29-this-Keyword-and-Nested-Objects.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-26--27-constructors--classes)**

Made with ❤️ for JavaScript learners

</div>
