# Chapters 54 & 55: Promises + Async/Await

---

# Chapter 54: Promises

## Overview
Learn how Promises solve callback hell and provide a better way to handle asynchronous operations.



---

## 54.1 What is a Promise?



**Promise:**
- Object representing eventual completion (or failure) of async operation
- Solves callback hell problem
- Three states: **pending**, **fulfilled**, **rejected**
- Once settled (fulfilled/rejected), cannot change

**Real-world analogy:** Ordering food
- **Pending:** Order placed, waiting
- **Fulfilled:** Food delivered successfully
- **Rejected:** Restaurant closed, order cancelled



---

## 54.2 Promise States



```javascript
// PENDING - Initial state
const promise = new Promise((resolve, reject) => {
    // Async operation in progress...
});

// FULFILLED - Success
resolve(value);

// REJECTED - Failure
reject(error);
```

// Output: Promise progresses from pending to fulfilled or rejected state

**Timeline:**
```
Pending → Fulfilled (success)
Pending → Rejected (failure)
```

**Once settled, state is permanent!**



---

## 54.3 Creating a Promise



```javascript
const myPromise = new Promise((resolve, reject) => {
    // Async operation
    const success = true;
    
    if (success) {
        resolve("Operation successful!"); // Fulfill
    } else {
        reject("Operation failed!"); // Reject
    }
});
// Output: Promise either fulfills or rejects immediately
```

**`resolve`** - Call when successful  
**`reject`** - Call when failed



---

## 54.4 Consuming a Promise



### .then() and .catch()

```javascript
myPromise
    .then(result => {
        console.log(result);
        // Output: Operation successful!
    })
    .catch(error => {
        console.error(error);
        // Output: Operation failed! (if promise rejects)
    });
```

**`.then()`** - Runs when fulfilled  
**`.catch()`** - Runs when rejected



---

## 54.5 Practical Example: Delayed Task



```javascript
function wait(ms) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(`Waited ${ms}ms`);
        }, ms);
    });
}

wait(2000)
    .then(message => {
        console.log(message); 
        // Output: Waited 2000ms (after 2 second delay)
    });
```



---

## 54.6 Promise with Success/Failure



```javascript
function checkAge(age) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (age >= 18) {
                resolve("Access granted");
            } else {
                reject("Access denied: Too young");
            }
        }, 1000);
    });
}

checkAge(20)
    .then(message => {
        console.log(message); // "Access granted"
    })
    .catch(error => {
        console.error(error);
    });

checkAge(15)
    .then(message => {
        console.log(message);
    })
    .catch(error => {
        console.error(error); // "Access denied: Too young"
    });
```



---

## 54.7 Chaining Promises



Solve callback hell with promise chaining:

```javascript
function step1() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("Step 1 complete");
            resolve("Result from step 1");
        }, 1000);
    });
}

function step2(data) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("Step 2 complete");
            console.log("Received:", data);
            resolve("Result from step 2");
        }, 1000);
    });
}

function step3(data) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("Step 3 complete");
            console.log("Received:", data);
            resolve("Result from step 3");
        }, 1000);
    });
}

// CLEAN CHAINING! ✅
step1()
    .then(result1 => step2(result1))
    .then(result2 => step3(result2))
    .then(result3 => {
        console.log("All steps complete!");
        console.log("Final result:", result3);
    })
    .catch(error => {
        console.error("Error:", error);
    });
```

**Much better than callback hell!**



---

## 54.8 Error Handling in Chain



```javascript
function task1() {
    return new Promise((resolve) => {
        resolve("Task 1 done");
    });
}

function task2() {
    return new Promise((resolve, reject) => {
        reject("Task 2 failed!"); // Error here
    });
}

function task3() {
    return new Promise((resolve) => {
        resolve("Task 3 done");
    });
}

task1()
    .then(result => {
        console.log(result);
        return task2();
    })
    .then(result => {
        console.log(result);
        return task3(); // Won't reach here
    })
    .then(result => {
        console.log(result);
    })
    .catch(error => {
        console.error("Error caught:", error); // Catches task2 error
    });
```

**`.catch()` catches ANY error in the chain!**



---

## 54.9 finally() Method



Runs regardless of success or failure:

```javascript
fetchData()
    .then(data => {
        console.log("Data:", data);
    })
    .catch(error => {
        console.error("Error:", error);
    })
    .finally(() => {
        console.log("Cleanup: Close connection");
        // Always runs!
    });
```

**Use case:** Hiding loading spinners, closing connections



---

## 54.10 Real-World Example: User Registration



```javascript
function validateUser(username) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (username.length >= 3) {
                resolve(username);
            } else {
                reject("Username too short");
            }
        }, 1000);
    });
}

function checkAvailability(username) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (username !== "admin") {
                resolve(username);
            } else {
                reject("Username taken");
            }
        }, 1000);
    });
}

function createUser(username) {
    return new Promise((resolve) => {
        setTimeout(() => {
            const user = { id: 123, username: username };
            resolve(user);
        }, 1000);
    });
}

function sendEmail(user) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(`Email sent to ${user.username}`);
        }, 1000);
    });
}

// CLEAN PROMISE CHAIN! ✅
validateUser("john")
    .then(username => checkAvailability(username))
    .then(username => createUser(username))
    .then(user => sendEmail(user))
    .then(message => {
        console.log("Success:", message);
        console.log("Registration complete!");
    })
    .catch(error => {
        console.error("Registration failed:", error);
    })
    .finally(() => {
        console.log("Process finished");
    });
```

**Compare this to callback hell version in previous chapter!**



---

## 54.11 Promise.all()



Run multiple promises in parallel:

```javascript
const promise1 = new Promise(resolve => setTimeout(() => resolve("Result 1"), 1000));
const promise2 = new Promise(resolve => setTimeout(() => resolve("Result 2"), 2000));
const promise3 = new Promise(resolve => setTimeout(() => resolve("Result 3"), 1500));

Promise.all([promise1, promise2, promise3])
    .then(results => {
        console.log(results); // ["Result 1", "Result 2", "Result 3"]
        console.log("All promises completed!");
    })
    .catch(error => {
        console.error("One promise failed:", error);
    });
```

**Waits for ALL to complete!**  
**Rejects if ANY fails!**



---

## 54.12 Promise.race()



Returns first promise to settle:

```javascript
const slow = new Promise(resolve => setTimeout(() => resolve("Slow"), 3000));
const fast = new Promise(resolve => setTimeout(() => resolve("Fast"), 1000));

Promise.race([slow, fast])
    .then(result => {
        console.log(result); // "Fast" (wins the race!)
    });
```



---

## Summary - Chapter 54

✅ **Promise** - Object for async operations  
✅ **Three states:** pending, fulfilled, rejected  
✅ **`.then()`** - Handle success  
✅ **`.catch()`** - Handle errors  
✅ **`.finally()`** - Always runs  
✅ **Chaining** - Solve callback hell  
✅ **Promise.all()** - Multiple parallel promises  
✅ **Promise.race()** - First to complete wins  

---

# Chapter 55: Async/Await

## Overview
Learn async/await syntax - the modern way to write asynchronous code that looks synchronous.



---

## 55.1 What is Async/Await?



**Async/Await:**
- Syntactic sugar over Promises
- Makes async code look synchronous
- Easier to read and write
- Built on top of Promises

**Magic keywords:**
- **`async`** - Declares async function
- **`await`** - Waits for Promise to resolve



---

## 55.2 async Function



```javascript
// Regular function
function regularFunction() {
    return "Hello";
}

// Async function (returns Promise automatically)
async function asyncFunction() {
    return "Hello";
}

console.log(regularFunction()); // "Hello"
console.log(asyncFunction()); // Promise {<fulfilled>: "Hello"}

// Use .then() to get value
asyncFunction().then(value => {
    console.log(value); // "Hello"
});
```

**`async` functions ALWAYS return a Promise!**



---

## 55.3 await Keyword



**Rules:**
- Can ONLY use `await` inside `async` function
- `await` pauses function execution until Promise resolves
- Makes code look synchronous

```javascript
function wait(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

async function example() {
    console.log("Start");
    
    await wait(2000); // Wait 2 seconds
    
    console.log("After 2 seconds");
    
    await wait(1000); // Wait 1 second
    
    console.log("After 3 seconds total");
}

example();
```



---

## 55.4 Practical Example: Fetching Data



### Without Async/Await (Promises)

```javascript
function getUserData() {
    fetch("https://api.example.com/user")
        .then(response => response.json())
        .then(data => {
            console.log(data);
            return fetch(`https://api.example.com/posts/${data.id}`);
        })
        .then(response => response.json())
        .then(posts => {
            console.log(posts);
        })
        .catch(error => {
            console.error(error);
        });
}
```

### With Async/Await ✅

```javascript
async function getUserData() {
    try {
        const userResponse = await fetch("https://api.example.com/user");
        const user = await userResponse.json();
        console.log(user);
        
        const postsResponse = await fetch(`https://api.example.com/posts/${user.id}`);
        const posts = await postsResponse.json();
        console.log(posts);
        
    } catch (error) {
        console.error(error);
    }
}
```

**Much cleaner and easier to read!**



---

## 55.5 Error Handling with try/catch



```javascript
async function fetchUser(id) {
    try {
        const response = await fetch(`https://api.example.com/user/${id}`);
        
        if (!response.ok) {
            throw new Error("User not found");
        }
        
        const user = await response.json();
        console.log("User:", user);
        return user;
        
    } catch (error) {
        console.error("Error:", error.message);
        return null;
    }
}

fetchUser(123);
```



---

## 55.6 Sequential vs Parallel Execution



### Sequential (One at a time)

```javascript
async function sequential() {
    console.log("Start");
    
    const result1 = await task1(); // Wait for task1
    console.log(result1);
    
    const result2 = await task2(); // Then wait for task2
    console.log(result2);
    
    const result3 = await task3(); // Then wait for task3
    console.log(result3);
    
    console.log("Done");
}

// Total time: task1 + task2 + task3
```

### Parallel (Simultaneous)

```javascript
async function parallel() {
    console.log("Start");
    
    // Start all tasks at once
    const promise1 = task1();
    const promise2 = task2();
    const promise3 = task3();
    
    // Wait for all to complete
    const result1 = await promise1;
    const result2 = await promise2;
    const result3 = await promise3;
    
    console.log(result1, result2, result3);
    console.log("Done");
}

// Total time: max(task1, task2, task3)
```

### Using Promise.all()

```javascript
async function parallelAll() {
    console.log("Start");
    
    const results = await Promise.all([
        task1(),
        task2(),
        task3()
    ]);
    
    console.log(results);
    console.log("Done");
}
```



---

## 55.7 Real-World Example: User Registration



```javascript
// Promise-returning functions
function validateUser(username) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (username.length >= 3) {
                resolve(username);
            } else {
                reject("Username too short");
            }
        }, 1000);
    });
}

function checkAvailability(username) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (username !== "admin") {
                resolve(username);
            } else {
                reject("Username taken");
            }
        }, 1000);
    });
}

function createUser(username) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve({ id: 123, username: username });
        }, 1000);
    });
}

function sendEmail(user) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(`Email sent to ${user.username}`);
        }, 1000);
    });
}

// ASYNC/AWAIT VERSION ✅
async function registerUser(username) {
    try {
        console.log("Starting registration...");
        
        const validatedUsername = await validateUser(username);
        console.log("✓ Username validated");
        
        const availableUsername = await checkAvailability(validatedUsername);
        console.log("✓ Username available");
        
        const user = await createUser(availableUsername);
        console.log("✓ User created:", user);
        
        const emailResult = await sendEmail(user);
        console.log("✓", emailResult);
        
        console.log("✅ Registration complete!");
        return user;
        
    } catch (error) {
        console.error("❌ Registration failed:", error);
        throw error;
    }
}

// Use it
registerUser("john");
```

**Compare to callback hell and promise chain versions!**



---

## 55.8 Comparison: Callbacks vs Promises vs Async/Await



### Callbacks (Hell) ❌

```javascript
step1((result1) => {
    step2(result1, (result2) => {
        step3(result2, (result3) => {
            console.log("Done:", result3);
        });
    });
});
```

### Promises ✅

```javascript
step1()
    .then(result1 => step2(result1))
    .then(result2 => step3(result2))
    .then(result3 => {
        console.log("Done:", result3);
    })
    .catch(error => console.error(error));
```

### Async/Await ✅✅ (Best!)

```javascript
async function doSteps() {
    try {
        const result1 = await step1();
        const result2 = await step2(result1);
        const result3 = await step3(result2);
        console.log("Done:", result3);
    } catch (error) {
        console.error(error);
    }
}

doSteps();
```



---

## 55.9 Common Patterns



### Pattern 1: Loading Data

```javascript
async function loadUserProfile(userId) {
    try {
        const user = await fetchUser(userId);
        const posts = await fetchPosts(user.id);
        const followers = await fetchFollowers(user.id);
        
        return {
            user,
            posts,
            followers
        };
    } catch (error) {
        console.error("Failed to load profile:", error);
        return null;
    }
}
```

### Pattern 2: Retry Logic

```javascript
async function fetchWithRetry(url, retries = 3) {
    for (let i = 0; i < retries; i++) {
        try {
            const response = await fetch(url);
            return await response.json();
        } catch (error) {
            if (i === retries - 1) throw error;
            console.log(`Retry ${i + 1}/${retries}`);
            await wait(1000); // Wait before retry
        }
    }
}
```

### Pattern 3: Timeout

```javascript
async function fetchWithTimeout(url, timeout = 5000) {
    const timeoutPromise = new Promise((_, reject) => {
        setTimeout(() => reject(new Error("Timeout")), timeout);
    });
    
    const fetchPromise = fetch(url);
    
    const response = await Promise.race([fetchPromise, timeoutPromise]);
    return await response.json();
}
```



---

## 55.10 Async/Await with Loops



```javascript
const userIds = [1, 2, 3, 4, 5];

// Sequential (one at a time)
async function processSequential() {
    for (const id of userIds) {
        const user = await fetchUser(id);
        console.log(user);
    }
}

// Parallel (all at once)
async function processParallel() {
    const promises = userIds.map(id => fetchUser(id));
    const users = await Promise.all(promises);
    console.log(users);
}
```



---

## 55.11 Top-Level Await (Modern)



In modern JavaScript (modules):

```javascript
// Can use await at top level (no async function needed)
const user = await fetchUser(123);
console.log(user);

const data = await fetch("https://api.example.com/data");
const json = await data.json();
```

**Only works in modules!**

---

## Summary - Chapter 55

✅ **async** - Declares async function  
✅ **await** - Waits for Promise (only in async functions)  
✅ Makes async code look synchronous  
✅ **try/catch** for error handling  
✅ Sequential vs parallel execution  
✅ Much cleaner than callbacks or promise chains  
✅ Modern standard for async JavaScript  

---

## Practice Exercises

### Exercise 1: API Calls
Fetch and display data from multiple API endpoints.

### Exercise 2: Image Preloader
Load multiple images in parallel.

### Exercise 3: Form Validation
Async validation with database check.

### Exercise 4: Rate Limiter
Implement request rate limiting with delays.

---

## Quick Reference

```javascript
// Promises
const promise = new Promise((resolve, reject) => {
    if (success) resolve(value);
    else reject(error);
});

promise
    .then(result => console.log(result))
    .catch(error => console.error(error))
    .finally(() => console.log("Done"));

// Promise chaining
step1()
    .then(result => step2(result))
    .then(result => step3(result))
    .catch(error => console.error(error));

// Async/Await
async function myFunction() {
    try {
        const result1 = await step1();
        const result2 = await step2(result1);
        const result3 = await step3(result2);
        return result3;
    } catch (error) {
        console.error(error);
    }
}

// Parallel execution
const [result1, result2, result3] = await Promise.all([
    task1(),
    task2(),
    task3()
]);
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Chapters 52 & 53: Image Slider + Callback Hell](Chapters-52-53-Image-Slider-and-Callback-Hell.md) | [📑 Index](../README.md) | [Chapters 56 & 57: JSON + Fetch API ▶️](Chapters-56-57-JSON-and-Fetch-API.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-54--55-promises--asyncawait)**

Made with ❤️ for JavaScript learners

</div>

**Next: Chapters 56 & 57 - JSON + Fetch API**
