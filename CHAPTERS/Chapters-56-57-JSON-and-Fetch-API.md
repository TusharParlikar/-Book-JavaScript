# Chapters 56 & 57: JSON + Fetch API

---

# Chapter 56: JSON (JavaScript Object Notation)

## Overview
Learn JSON - the standard format for data exchange between applications.

**Timestamp:** [10:57:01]

---

## 56.1 What is JSON?

**Timestamp:** [10:57:08]

**JSON = JavaScript Object Notation**

- Text format for storing and exchanging data
- Language-independent (not just JavaScript!)
- Human-readable
- Used by APIs, databases, config files

**Common uses:**
- API responses
- Configuration files
- Data storage
- Communication between client and server

**Timestamp:** [10:57:50]

---

## 56.2 JSON Syntax Rules

**Timestamp:** [10:58:20]

✅ **Valid JSON:**
- Data in key/value pairs
- Keys MUST be in double quotes
- Values can be: string, number, boolean, null, array, object
- No trailing commas
- No comments allowed

```json
{
    "name": "John",
    "age": 30,
    "isStudent": false,
    "hobbies": ["reading", "gaming"],
    "address": {
        "city": "New York",
        "country": "USA"
    }
}
```

**Timestamp:** [10:59:30]

---

## 56.3 JSON vs JavaScript Object

**Timestamp:** [11:00:00]

### JavaScript Object

```javascript
const person = {
    name: "John",           // No quotes on key
    age: 30,
    greet: function() {     // Can have functions
        console.log("Hello");
    }
};
```

### JSON

```json
{
    "name": "John",         // Quotes required on key
    "age": 30
}
```

❌ **JSON cannot have:**
- Functions
- Undefined
- Symbols
- Comments

**Timestamp:** [11:01:20]

---

## 56.4 JSON Data Types

**Timestamp:** [11:01:50]

### String

```json
{
    "name": "John",
    "email": "john@example.com"
}
```

### Number

```json
{
    "age": 30,
    "price": 19.99,
    "quantity": 5
}
```

### Boolean

```json
{
    "isActive": true,
    "hasAccess": false
}
```

### Null

```json
{
    "middleName": null
}
```

### Array

```json
{
    "colors": ["red", "green", "blue"],
    "numbers": [1, 2, 3, 4, 5]
}
```

### Object

```json
{
    "address": {
        "street": "123 Main St",
        "city": "New York"
    }
}
```

**Timestamp:** [11:03:40]

---

## 56.5 JSON.stringify()

**Timestamp:** [11:04:10]

Convert JavaScript object to JSON string:

```javascript
const person = {
    name: "John",
    age: 30,
    hobbies: ["reading", "gaming"],
    address: {
        city: "New York",
        country: "USA"
    }
};

// Convert to JSON string
const jsonString = JSON.stringify(person);

console.log(jsonString);
// {"name":"John","age":30,"hobbies":["reading","gaming"],"address":{"city":"New York","country":"USA"}}

console.log(typeof jsonString); // "string"
```

**Timestamp:** [11:05:20]

---

## 56.6 JSON.stringify() with Formatting

**Timestamp:** [11:05:50]

```javascript
const person = {
    name: "John",
    age: 30,
    city: "New York"
};

// Pretty print with indentation
const prettyJSON = JSON.stringify(person, null, 2);

console.log(prettyJSON);
/*
{
  "name": "John",
  "age": 30,
  "city": "New York"
}
*/
```

**Parameters:**
1. Object to convert
2. Replacer function/array (or null)
3. Number of spaces for indentation

**Timestamp:** [11:06:50]

---

## 56.7 JSON.parse()

**Timestamp:** [11:07:20]

Convert JSON string back to JavaScript object:

```javascript
const jsonString = '{"name":"John","age":30,"city":"New York"}';

// Convert to object
const person = JSON.parse(jsonString);

console.log(person); // {name: "John", age: 30, city: "New York"}
console.log(person.name); // "John"
console.log(person.age); // 30
```

**Timestamp:** [11:08:20]

---

## 56.8 Handling JSON Parse Errors

**Timestamp:** [11:08:50]

```javascript
const invalidJSON = '{name: "John"}'; // Invalid: keys must be in quotes

try {
    const data = JSON.parse(invalidJSON);
} catch (error) {
    console.error("Invalid JSON:", error.message);
    // "Unexpected token n in JSON at position 1"
}
```

**Always use try/catch when parsing JSON!**

**Timestamp:** [11:09:50]

---

## 56.9 Practical Example: Local Storage

**Timestamp:** [11:10:20]

```javascript
// Save object to local storage
const user = {
    name: "John",
    age: 30,
    email: "john@example.com"
};

// Convert to JSON string and save
localStorage.setItem("user", JSON.stringify(user));

// Retrieve and parse
const savedUser = localStorage.getItem("user");
const userObject = JSON.parse(savedUser);

console.log(userObject.name); // "John"
```

**Timestamp:** [11:11:30]

---

## 56.10 Nested JSON Example

**Timestamp:** [11:12:00]

```javascript
const company = {
    name: "Tech Corp",
    employees: [
        {
            id: 1,
            name: "John",
            position: "Developer",
            skills: ["JavaScript", "Python"]
        },
        {
            id: 2,
            name: "Jane",
            position: "Designer",
            skills: ["Photoshop", "Figma"]
        }
    ],
    location: {
        city: "New York",
        country: "USA",
        coordinates: {
            lat: 40.7128,
            lng: -74.0060
        }
    }
};

// Convert to JSON
const json = JSON.stringify(company, null, 2);
console.log(json);

// Parse back
const parsed = JSON.parse(json);
console.log(parsed.employees[0].name); // "John"
console.log(parsed.location.coordinates.lat); // 40.7128
```

**Timestamp:** [11:14:00]

---

## 56.11 Common JSON Use Cases

**Timestamp:** [11:14:30]

### 1. Configuration Files

```json
{
    "appName": "MyApp",
    "version": "1.0.0",
    "apiUrl": "https://api.example.com",
    "features": {
        "darkMode": true,
        "notifications": false
    }
}
```

### 2. API Response

```json
{
    "status": "success",
    "data": {
        "users": [
            {"id": 1, "name": "John"},
            {"id": 2, "name": "Jane"}
        ]
    },
    "message": "Users retrieved successfully"
}
```

### 3. Form Data

```json
{
    "username": "john123",
    "email": "john@example.com",
    "preferences": {
        "newsletter": true,
        "theme": "dark"
    }
}
```

**Timestamp:** [11:16:10]

---

## Summary - Chapter 56

✅ **JSON** - Text format for data exchange  
✅ Keys must be in double quotes  
✅ **JSON.stringify()** - Object → JSON string  
✅ **JSON.parse()** - JSON string → Object  
✅ Cannot contain functions or undefined  
✅ Used for APIs, storage, configuration  
✅ Always use try/catch with JSON.parse()  

---

# Chapter 57: Fetch API

## Overview
Learn to fetch data from APIs using the modern Fetch API.

**Timestamp:** [11:16:28]

---

## 57.1 What is the Fetch API?

**Timestamp:** [11:16:35]

**Fetch API:**
- Modern way to make HTTP requests
- Replaces old XMLHttpRequest
- Returns Promises
- Supported in all modern browsers
- Works with JSON, text, files

**Common uses:**
- Get data from API
- Send data to server
- Upload files
- Submit forms

**Timestamp:** [11:17:30]

---

## 57.2 Basic Fetch Syntax

**Timestamp:** [11:18:00]

```javascript
fetch(url)
    .then(response => response.json())
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error("Error:", error);
    });
```

**Steps:**
1. Call `fetch(url)` → Returns Promise
2. Get Response object
3. Convert response to JSON
4. Use the data
5. Handle errors

**Timestamp:** [11:19:10]

---

## 57.3 Simple GET Request

**Timestamp:** [11:19:40]

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
    .then(response => {
        console.log(response); // Response object
        return response.json(); // Parse JSON
    })
    .then(users => {
        console.log(users); // Array of users
        users.forEach(user => {
            console.log(user.name);
        });
    })
    .catch(error => {
        console.error("Error fetching users:", error);
    });
```

**Timestamp:** [11:20:50]

---

## 57.4 Fetch with Async/Await

**Timestamp:** [11:21:20]

```javascript
async function fetchUsers() {
    try {
        const response = await fetch("https://jsonplaceholder.typicode.com/users");
        
        if (!response.ok) {
            throw new Error(`HTTP error! Status: ${response.status}`);
        }
        
        const users = await response.json();
        console.log(users);
        
    } catch (error) {
        console.error("Error:", error);
    }
}

fetchUsers();
```

✅ **Cleaner and easier to read!**

**Timestamp:** [11:22:40]

---

## 57.5 Response Object

**Timestamp:** [11:23:10]

```javascript
fetch(url).then(response => {
    console.log(response.ok);        // true if 200-299
    console.log(response.status);    // 200, 404, 500, etc.
    console.log(response.statusText); // "OK", "Not Found", etc.
    console.log(response.headers);   // Headers object
    console.log(response.url);       // Request URL
});
```

**Common methods:**
- `response.json()` - Parse as JSON
- `response.text()` - Get as text
- `response.blob()` - Get as binary data

**Timestamp:** [11:24:20]

---

## 57.6 Checking Response Status

**Timestamp:** [11:24:50]

```javascript
async function fetchData(url) {
    try {
        const response = await fetch(url);
        
        // Check if response is OK (200-299)
        if (!response.ok) {
            throw new Error(`HTTP error! Status: ${response.status}`);
        }
        
        const data = await response.json();
        return data;
        
    } catch (error) {
        console.error("Fetch error:", error.message);
        return null;
    }
}
```

**Important:** Fetch only rejects on network failure, not HTTP errors!

**Timestamp:** [11:26:00]

---

## 57.7 POST Request (Sending Data)

**Timestamp:** [11:26:30]

```javascript
async function createUser(userData) {
    try {
        const response = await fetch("https://jsonplaceholder.typicode.com/users", {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify(userData)
        });
        
        if (!response.ok) {
            throw new Error(`HTTP error! Status: ${response.status}`);
        }
        
        const newUser = await response.json();
        console.log("User created:", newUser);
        return newUser;
        
    } catch (error) {
        console.error("Error creating user:", error);
        return null;
    }
}

// Use it
const userData = {
    name: "John Doe",
    email: "john@example.com",
    age: 30
};

createUser(userData);
```

**Timestamp:** [11:28:30]

---

## 57.8 PUT Request (Update Data)

**Timestamp:** [11:29:00]

```javascript
async function updateUser(userId, updates) {
    try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/users/${userId}`, {
            method: "PUT",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify(updates)
        });
        
        const updatedUser = await response.json();
        console.log("User updated:", updatedUser);
        return updatedUser;
        
    } catch (error) {
        console.error("Error updating user:", error);
    }
}

updateUser(1, { name: "Jane Doe", email: "jane@example.com" });
```

**Timestamp:** [11:30:20]

---

## 57.9 DELETE Request

**Timestamp:** [11:30:50]

```javascript
async function deleteUser(userId) {
    try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/users/${userId}`, {
            method: "DELETE"
        });
        
        if (response.ok) {
            console.log(`User ${userId} deleted successfully`);
        }
        
    } catch (error) {
        console.error("Error deleting user:", error);
    }
}

deleteUser(1);
```

**Timestamp:** [11:31:40]

---

## 57.10 Fetch Options

**Timestamp:** [11:32:10]

```javascript
fetch(url, {
    method: "POST",              // GET, POST, PUT, DELETE, etc.
    headers: {
        "Content-Type": "application/json",
        "Authorization": "Bearer token123"
    },
    body: JSON.stringify(data),  // Data to send
    mode: "cors",                // cors, no-cors, same-origin
    credentials: "include",      // include, same-origin, omit
    cache: "no-cache"           // default, no-cache, reload, etc.
});
```

**Timestamp:** [11:33:20]

---

## 57.11 Practical Example: Display Users

**Timestamp:** [11:33:50]

```html
<!DOCTYPE html>
<html>
<head>
    <title>Fetch Users</title>
</head>
<body>
    <button id="loadBtn">Load Users</button>
    <div id="userList"></div>
    
    <script src="script.js"></script>
</body>
</html>
```

```javascript
const loadBtn = document.getElementById("loadBtn");
const userList = document.getElementById("userList");

loadBtn.addEventListener("click", fetchAndDisplayUsers);

async function fetchAndDisplayUsers() {
    try {
        // Show loading
        userList.innerHTML = "<p>Loading...</p>";
        
        // Fetch data
        const response = await fetch("https://jsonplaceholder.typicode.com/users");
        
        if (!response.ok) {
            throw new Error(`HTTP error! Status: ${response.status}`);
        }
        
        const users = await response.json();
        
        // Display users
        userList.innerHTML = "";
        users.forEach(user => {
            const userDiv = document.createElement("div");
            userDiv.innerHTML = `
                <h3>${user.name}</h3>
                <p>Email: ${user.email}</p>
                <p>Phone: ${user.phone}</p>
                <hr>
            `;
            userList.appendChild(userDiv);
        });
        
    } catch (error) {
        userList.innerHTML = `<p style="color: red;">Error: ${error.message}</p>`;
    }
}
```

**Timestamp:** [11:36:30]

---

## 57.12 Error Handling Best Practices

**Timestamp:** [11:37:00]

```javascript
async function fetchWithErrorHandling(url) {
    try {
        const response = await fetch(url);
        
        // Check HTTP status
        if (!response.ok) {
            throw new Error(`HTTP ${response.status}: ${response.statusText}`);
        }
        
        // Try to parse JSON
        const data = await response.json();
        return { success: true, data };
        
    } catch (error) {
        // Network error or JSON parse error
        console.error("Fetch error:", error);
        return { success: false, error: error.message };
    }
}

// Use it
const result = await fetchWithErrorHandling("https://api.example.com/data");

if (result.success) {
    console.log("Data:", result.data);
} else {
    console.log("Error:", result.error);
}
```

**Timestamp:** [11:38:40]

---

## 57.13 Timeout for Fetch

**Timestamp:** [11:39:10]

```javascript
async function fetchWithTimeout(url, timeout = 5000) {
    const controller = new AbortController();
    const timeoutId = setTimeout(() => controller.abort(), timeout);
    
    try {
        const response = await fetch(url, {
            signal: controller.signal
        });
        
        clearTimeout(timeoutId);
        return await response.json();
        
    } catch (error) {
        if (error.name === "AbortError") {
            throw new Error("Request timeout");
        }
        throw error;
    }
}

// Use it
try {
    const data = await fetchWithTimeout("https://api.example.com/data", 3000);
    console.log(data);
} catch (error) {
    console.error(error.message); // "Request timeout"
}
```

**Timestamp:** [11:40:50]

---

## 57.14 Multiple Fetch Requests

**Timestamp:** [11:41:20]

### Sequential

```javascript
async function fetchSequential() {
    const user = await fetch("https://api.example.com/user").then(r => r.json());
    const posts = await fetch(`https://api.example.com/posts/${user.id}`).then(r => r.json());
    const comments = await fetch(`https://api.example.com/comments/${posts[0].id}`).then(r => r.json());
    
    return { user, posts, comments };
}
```

### Parallel

```javascript
async function fetchParallel() {
    const [users, posts, comments] = await Promise.all([
        fetch("https://api.example.com/users").then(r => r.json()),
        fetch("https://api.example.com/posts").then(r => r.json()),
        fetch("https://api.example.com/comments").then(r => r.json())
    ]);
    
    return { users, posts, comments };
}
```

**Timestamp:** [11:43:00]

---

## Summary - Chapter 57

✅ **Fetch API** - Modern HTTP requests  
✅ Returns Promises (use with .then() or async/await)  
✅ **response.json()** - Parse JSON  
✅ **response.ok** - Check if successful  
✅ Methods: GET, POST, PUT, DELETE  
✅ Send data with `body: JSON.stringify(data)`  
✅ Always check response status  
✅ Use try/catch for error handling  

---

## Practice Exercises

### Exercise 1: User Directory
Fetch and display user list with search/filter.

### Exercise 2: CRUD Application
Create full CRUD app with API.

### Exercise 3: Weather App
Fetch weather data and display forecast.

### Exercise 4: Todo App
Build todo app with API backend.

---

## Quick Reference

```javascript
// JSON
const obj = { name: "John", age: 30 };
const json = JSON.stringify(obj);     // Object → JSON string
const parsed = JSON.parse(json);      // JSON string → Object

// Fetch - GET
async function getData() {
    const response = await fetch(url);
    if (!response.ok) throw new Error("HTTP error");
    const data = await response.json();
    return data;
}

// Fetch - POST
async function postData(data) {
    const response = await fetch(url, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(data)
    });
    return await response.json();
}

// Error handling
try {
    const data = await fetch(url).then(r => r.json());
} catch (error) {
    console.error("Error:", error);
}

// Multiple requests
const [data1, data2] = await Promise.all([
    fetch(url1).then(r => r.json()),
    fetch(url2).then(r => r.json())
]);
```

---

**Next: Chapter 58 - Weather App (Final Project)**
