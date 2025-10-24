# Chapters 34 & 35: Closures + setTimeout/clearTimeout

---

# Chapter 34: Closures

## Overview
Closures are functions that have access to variables from their outer (enclosing) scope, even after the outer function has finished executing.

**Timestamp:** [06:48:08]

---

## 34.1 What are Closures?

**Timestamp:** [06:48:15]

A **closure** is:
- A function defined inside another function
- Has access to the outer function's variables
- Maintains access to those variables even after outer function returns
- Creates "private" variables

---

## 34.2 Basic Closure Example

**Timestamp:** [06:48:49]

```javascript
function outer() {
    let message = "Hello";
    
    function inner() {
        console.log(message); // Access outer variable
    }
    
    inner();
}

outer(); // "Hello"
```

The `inner` function has access to `message` from the outer scope.

---

## 34.3 Returning a Function (True Closure)

```javascript
function outer() {
    let message = "Hello";
    
    function inner() {
        console.log(message);
    }
    
    return inner; // Return the inner function
}

const myFunction = outer();
myFunction(); // "Hello" - still has access to message!
```

Even after `outer()` finishes, the returned function remembers `message`.

---

## 34.4 Private Variables

**Timestamp:** [06:49:53]

Closures create **private variables** that can't be accessed from outside:

```javascript
function createCounter() {
    let count = 0; // Private variable
    
    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();

console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3

// Cannot access 'count' directly
console.log(count); // Error: count is not defined
```

**Timestamp:** [06:50:30]

---

## 34.5 Problem: Simple Counter Without Closure

**Timestamp:** [06:50:37]

Without closure, variables reset:

```javascript
function increment() {
    let count = 0; // Resets every time!
    count++;
    return count;
}

console.log(increment()); // 1
console.log(increment()); // 1 (resets)
console.log(increment()); // 1 (resets)
```

---

## 34.6 Solution: Counter with Closure

**Timestamp:** [06:51:22]

```javascript
function createCounter() {
    let count = 0; // Persists!
    
    function increment() {
        count++;
        console.log(count);
    }
    
    return increment;
}

const counter = createCounter();

counter(); // 1
counter(); // 2
counter(); // 3
```

The `count` variable persists between calls!

---

## 34.7 Returning Object with Multiple Methods

**Timestamp:** [06:54:15]

```javascript
function createCounter() {
    let count = 0;
    
    return {
        increment() {
            count++;
            console.log(count);
        },
        decrement() {
            count--;
            console.log(count);
        },
        getCount() {
            return count;
        }
    };
}

const counter = createCounter();

counter.increment(); // 1
counter.increment(); // 2
counter.decrement(); // 1
console.log(counter.getCount()); // 1
```

All methods share access to the same `count` variable!

---

## 34.8 Practical Example: Game Score

**Timestamp:** [06:55:13]

```javascript
function createGame() {
    let score = 0; // Private score
    
    return {
        increaseScore(points) {
            score += points;
            console.log(`Score: ${score}`);
        },
        
        decreaseScore(points) {
            score -= points;
            console.log(`Score: ${score}`);
        },
        
        getScore() {
            return score;
        },
        
        resetScore() {
            score = 0;
            console.log("Score reset!");
        }
    };
}

const game = createGame();

game.increaseScore(10);  // Score: 10
game.increaseScore(5);   // Score: 15
game.decreaseScore(3);   // Score: 12
console.log(game.getScore()); // 12
game.resetScore();       // Score reset!

// Cannot access score directly
// console.log(game.score); // undefined
```

---

## 34.9 Multiple Independent Closures

```javascript
function createCounter() {
    let count = 0;
    
    return {
        increment() {
            count++;
            return count;
        },
        getCount() {
            return count;
        }
    };
}

const counter1 = createCounter();
const counter2 = createCounter();

counter1.increment(); // 1
counter1.increment(); // 2
console.log(counter1.getCount()); // 2

counter2.increment(); // 1
console.log(counter2.getCount()); // 1

// Each closure has its own separate 'count'
```

---

## 34.10 Practical Examples

### Example 1: ID Generator

```javascript
function createIDGenerator() {
    let id = 0;
    
    return function() {
        id++;
        return `ID-${id}`;
    };
}

const generateID = createIDGenerator();

console.log(generateID()); // "ID-1"
console.log(generateID()); // "ID-2"
console.log(generateID()); // "ID-3"
```

### Example 2: Bank Account

```javascript
function createBankAccount(initialBalance) {
    let balance = initialBalance; // Private
    
    return {
        deposit(amount) {
            if (amount > 0) {
                balance += amount;
                console.log(`Deposited $${amount}. Balance: $${balance}`);
            }
        },
        
        withdraw(amount) {
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                console.log(`Withdrew $${amount}. Balance: $${balance}`);
            } else {
                console.log("Insufficient funds!");
            }
        },
        
        getBalance() {
            return balance;
        }
    };
}

const account = createBankAccount(1000);
account.deposit(500);   // Deposited $500. Balance: $1500
account.withdraw(200);  // Withdrew $200. Balance: $1300
console.log(account.getBalance()); // 1300

// Balance is protected - cannot modify directly
```

### Example 3: Secret Message

```javascript
function createSecureMessage(message) {
    let secret = message; // Private
    let locked = true;
    
    return {
        unlock(password) {
            if (password === "1234") {
                locked = false;
                console.log("Unlocked!");
            } else {
                console.log("Wrong password!");
            }
        },
        
        read() {
            if (!locked) {
                return secret;
            } else {
                return "Message is locked!";
            }
        },
        
        lock() {
            locked = true;
            console.log("Locked!");
        }
    };
}

const message = createSecureMessage("Top Secret Info");

console.log(message.read()); // "Message is locked!"
message.unlock("wrong");     // "Wrong password!"
message.unlock("1234");      // "Unlocked!"
console.log(message.read()); // "Top Secret Info"
message.lock();              // "Locked!"
console.log(message.read()); // "Message is locked!"
```

---

## 34.11 Benefits of Closures

✅ **Data Privacy:** Variables are hidden from outside scope  
✅ **State Maintenance:** Variables persist between function calls  
✅ **Encapsulation:** Bundle data with functions that use it  
✅ **Factory Functions:** Create multiple independent instances  

---

## Summary - Chapter 34

✅ Closures are inner functions accessing outer variables  
✅ Variables persist after outer function returns  
✅ Create private variables  
✅ Maintain state between calls  
✅ Each closure instance is independent  
✅ Useful for data privacy and encapsulation  

---

# Chapter 35: setTimeout & clearTimeout

## Overview
Learn how to schedule code execution with setTimeout and how to cancel scheduled timeouts.

**Timestamp:** [06:59:08]

---

## 35.1 What is setTimeout?

**Timestamp:** [06:59:13]

`setTimeout()`:
- Schedules a function to run **once** after a delay
- Takes two arguments: callback function and delay (milliseconds)
- **Asynchronous** - doesn't block code execution
- Returns a timeout ID

**Syntax:**
```javascript
setTimeout(callback, delay);
```

**Timestamp:** [06:59:22]

---

## 35.2 Basic setTimeout Example

**Timestamp:** [06:59:43]

```javascript
function sayHello() {
    console.log("Hello!");
}

// Execute after 3 seconds (3000 ms)
setTimeout(sayHello, 3000);

console.log("This runs immediately");

// Output:
// "This runs immediately" (immediately)
// "Hello!" (after 3 seconds)
```

---

## 35.3 setTimeout with Anonymous Function

**Timestamp:** [06:59:59]

```javascript
setTimeout(function() {
    console.log("Hello after 2 seconds!");
}, 2000);
```

---

## 35.4 setTimeout with Arrow Function

```javascript
setTimeout(() => {
    console.log("Hello after 1 second!");
}, 1000);
```

Cleaner and more concise!

---

## 35.5 setTimeout Return Value

**Timestamp:** [07:00:59]

`setTimeout` returns a **timeout ID** (number):

```javascript
const timeoutId = setTimeout(() => {
    console.log("This will run");
}, 5000);

console.log(timeoutId); // Example: 1
```

This ID can be used to cancel the timeout.

---

## 35.6 clearTimeout

**Timestamp:** [07:00:59]

Cancel a scheduled timeout before it executes:

```javascript
const timeoutId = setTimeout(() => {
    console.log("This will NOT run");
}, 5000);

// Cancel the timeout
clearTimeout(timeoutId);
```

The callback function never executes!

---

## 35.7 Practical Example: Delayed Alert

**Timestamp:** [06:59:43]

```javascript
console.log("Starting countdown...");

setTimeout(() => {
    alert("Time's up!");
}, 3000);

console.log("Countdown started!");

// Output:
// "Starting countdown..." (immediately)
// "Countdown started!" (immediately)
// Alert appears after 3 seconds
```

---

## 35.8 Example with Start and Cancel Buttons

**Timestamp:** [07:01:40]

```html
<button id="startBtn">Start Timer</button>
<button id="cancelBtn">Cancel Timer</button>
```

```javascript
let timeoutId;

const startBtn = document.getElementById("startBtn");
const cancelBtn = document.getElementById("cancelBtn");

startBtn.addEventListener("click", () => {
    timeoutId = setTimeout(() => {
        alert("Time's up!");
    }, 5000);
    console.log("Timer started!");
});

cancelBtn.addEventListener("click", () => {
    clearTimeout(timeoutId);
    console.log("Timer cancelled!");
});
```

**Timestamp:** [07:00:59]

---

## 35.9 Multiple Timeouts

```javascript
setTimeout(() => {
    console.log("1 second");
}, 1000);

setTimeout(() => {
    console.log("2 seconds");
}, 2000);

setTimeout(() => {
    console.log("3 seconds");
}, 3000);

// Output:
// "1 second" (after 1s)
// "2 seconds" (after 2s)
// "3 seconds" (after 3s)
```

---

## 35.10 Passing Arguments to Callback

```javascript
function greet(name, greeting) {
    console.log(`${greeting}, ${name}!`);
}

// Pass arguments after delay
setTimeout(greet, 2000, "John", "Hello");
// After 2 seconds: "Hello, John!"

// Or use arrow function
setTimeout(() => greet("Jane", "Hi"), 3000);
// After 3 seconds: "Hi, Jane!"
```

---

## 35.11 Practical Examples

### Example 1: Loading Message

```javascript
console.log("Loading...");

setTimeout(() => {
    console.log("Data loaded!");
}, 2000);
```

### Example 2: Auto-hide Notification

```javascript
function showNotification(message) {
    const notification = document.getElementById("notification");
    notification.textContent = message;
    notification.style.display = "block";
    
    // Hide after 3 seconds
    setTimeout(() => {
        notification.style.display = "none";
    }, 3000);
}

showNotification("File saved successfully!");
```

### Example 3: Countdown Timer

```javascript
function countdown(seconds) {
    if (seconds > 0) {
        console.log(seconds);
        setTimeout(() => {
            countdown(seconds - 1);
        }, 1000);
    } else {
        console.log("Time's up!");
    }
}

countdown(5);
// Output:
// 5
// 4
// 3
// 2
// 1
// Time's up!
```

### Example 4: Delayed Redirect

```javascript
console.log("Redirecting in 5 seconds...");

const timeoutId = setTimeout(() => {
    window.location.href = "https://example.com";
}, 5000);

// User can cancel redirect
document.getElementById("cancelBtn").addEventListener("click", () => {
    clearTimeout(timeoutId);
    console.log("Redirect cancelled");
});
```

---

## 35.12 setTimeout vs setInterval

| Feature | setTimeout | setInterval |
|---------|-----------|-------------|
| Execution | Once | Repeatedly |
| Syntax | `setTimeout(fn, ms)` | `setInterval(fn, ms)` |
| Cancel | `clearTimeout(id)` | `clearInterval(id)` |
| Use case | Delayed action | Repeated action |

---

## 35.13 Common Patterns

### Pattern 1: Delayed Execution

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Delayed task");
}, 1000);

console.log("End");
// Start
// End
// Delayed task
```

### Pattern 2: Conditional Cancel

```javascript
let cancelled = false;

const id = setTimeout(() => {
    if (!cancelled) {
        console.log("Executed");
    }
}, 2000);

// Cancel if condition met
if (someCondition) {
    clearTimeout(id);
    cancelled = true;
}
```

### Pattern 3: Chain Timeouts

```javascript
setTimeout(() => {
    console.log("Step 1");
    setTimeout(() => {
        console.log("Step 2");
        setTimeout(() => {
            console.log("Step 3");
        }, 1000);
    }, 1000);
}, 1000);
```

---

## Summary - Chapter 35

✅ `setTimeout(callback, ms)` - Execute once after delay  
✅ Asynchronous - doesn't block execution  
✅ Returns timeout ID  
✅ `clearTimeout(id)` - Cancel timeout  
✅ Delay in milliseconds (1000 ms = 1 second)  
✅ Can pass arguments to callback  
✅ Useful for delayed actions  

---

## Practice Exercises

### Exercise 1: Auto-save Feature
Implement auto-save that triggers 2 seconds after user stops typing.

### Exercise 2: Toast Notification
Create self-dismissing notification system.

### Exercise 3: Game Timer
Countdown timer for game with pause/resume.

### Exercise 4: Debounce Function
Delay function execution until after user stops calling it.

---

## Quick Reference

```javascript
// setTimeout - run once
const id = setTimeout(() => {
    console.log("Delayed");
}, 2000);

// clearTimeout - cancel
clearTimeout(id);

// With arguments
setTimeout((name) => {
    console.log(`Hello ${name}`);
}, 1000, "John");

// Multiple timeouts
setTimeout(() => console.log("1"), 1000);
setTimeout(() => console.log("2"), 2000);
setTimeout(() => console.log("3"), 3000);
```

---

**Next: Chapters 36 & 37 - Digital Clock Project + Stopwatch Project**
