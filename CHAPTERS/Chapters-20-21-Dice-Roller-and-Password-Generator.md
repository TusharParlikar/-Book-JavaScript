# Chapters 20 & 21: Dice Roller + Password Generator Projects

---

# Chapter 20: Dice Roller Project

## Overview
Create a dice rolling program that generates random dice faces and displays them visually.



---

## 20.1 Project Goal

Build a dice roller that:
- Allows user to choose number of dice
- Generates random numbers (1-6)
- Displays dice face images
- Shows results in text and images



---

## 20.2 HTML Structure



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dice Roller</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Dice Roller</h1>
        
        <!-- Input for number of dice -->
        <label for="numOfDice">Number of dice:</label>
        <input type="number" id="numOfDice" min="1" max="10" value="1">
        <br>
        
        <!-- Roll button -->
        <button id="rollBtn">Roll Dice</button>
        <br>
        
        <!-- Display results -->
        <div id="diceResult"></div>
        <div id="diceImages"></div>
    </div>
    
    <script src="index.js"></script>
</body>
</html>
```

, [03:24:33], [03:24:50]

---

## 20.3 Prepare Dice Images



Ensure you have dice face images:
- `dice1.png`
- `dice2.png`
- `dice3.png`
- `dice4.png`
- `dice5.png`
- `dice6.png`

Place in an `images` folder or root directory.

---

## 20.4 JavaScript - Get Elements

, [03:25:23], [03:25:35], [03:25:43]

```javascript
// Get HTML element references
const numOfDice = document.getElementById("numOfDice");
// Output: numOfDice element reference obtained

const diceResult = document.getElementById("diceResult");
// Output: diceResult element reference obtained

const diceImages = document.getElementById("diceImages");
// Output: diceImages element reference obtained

const rollBtn = document.getElementById("rollBtn");
// Output: rollBtn element reference obtained
```

---

## 20.5 JavaScript - Roll Function



```javascript
function rollDice() {
    // Get number of dice to roll
    const numOfDiceValue = numOfDice.value;
    
    // Arrays to store results
    const values = [];
    const images = [];
    
    // Roll each die
    for (let i = 0; i < numOfDiceValue; i++) {
        const value = Math.floor(Math.random() * 6) + 1;
        values.push(value);
        images.push(`<img src="images/dice${value}.png" alt="Dice ${value}">`);
    }
    
    // Display results
    diceResult.textContent = `Dice: ${values.join(', ')}`;
    diceImages.innerHTML = images.join('');
}

// Add event listener
rollBtn.onclick = rollDice;
```

, [03:26:27], [03:26:46], [03:27:08], [03:27:25], [03:27:42]

---

## 20.6 Step-by-Step Explanation

### Step 1: Get Number of Dice



```javascript
const numOfDiceValue = numOfDice.value;
```

Get the number from the input field.

### Step 2: Create Storage Arrays



```javascript
const values = [];  // Store dice numbers
const images = [];  // Store image HTML
```

### Step 3: Roll Each Die



```javascript
for (let i = 0; i < numOfDiceValue; i++) {
    const value = Math.floor(Math.random() * 6) + 1;
    values.push(value);
    images.push(`<img src="images/dice${value}.png">`);
}
```

- Loop for each die
- Generate random 1-6
- Store number and corresponding image

### Step 4: Display Results

, [03:27:42]

```javascript
diceResult.textContent = `Dice: ${values.join(', ')}`;
diceImages.innerHTML = images.join('');
```

- Show numbers as text (comma-separated)
- Show images as HTML

---

## 20.7 Complete JavaScript Code

```javascript
// Get elements
const numOfDice = document.getElementById("numOfDice");
const diceResult = document.getElementById("diceResult");
const diceImages = document.getElementById("diceImages");
const rollBtn = document.getElementById("rollBtn");

// Roll function
function rollDice() {
    const numOfDiceValue = numOfDice.value;
    const values = [];
    const images = [];
    
    for (let i = 0; i < numOfDiceValue; i++) {
        const value = Math.floor(Math.random() * 6) + 1;
        values.push(value);
        images.push(`<img src="images/dice${value}.png" alt="Dice ${value}" class="dice-img">`);
    }
    
    diceResult.textContent = `Dice: ${values.join(', ')}`;
    diceImages.innerHTML = images.join('');
}

// Attach event
rollBtn.onclick = rollDice;
```

---

## 20.8 CSS Styling (Optional)

```css
body {
    font-family: Arial, sans-serif;
    background-color: #2c3e50;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
}

.container {
    text-align: center;
    background: #34495e;
    padding: 40px;
    border-radius: 15px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
}

h1 {
    color: #ecf0f1;
    margin-bottom: 20px;
}

input[type="number"] {
    padding: 10px;
    font-size: 18px;
    width: 100px;
    margin: 10px 0;
    border-radius: 5px;
    border: none;
}

button {
    padding: 12px 30px;
    font-size: 18px;
    background: #e74c3c;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin: 20px 0;
}

button:hover {
    background: #c0392b;
}

#diceResult {
    font-size: 24px;
    font-weight: bold;
    margin: 20px 0;
}

#diceImages {
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
}

.dice-img {
    width: 80px;
    height: 80px;
}
```

---

## 20.9 Enhancements

### Add Animation

```javascript
rollBtn.onclick = function() {
    // Disable button during roll
    rollBtn.disabled = true;
    
    // Simulate rolling animation
    let rolls = 0;
    const interval = setInterval(() => {
        rollDice();
        rolls++;
        
        if (rolls >= 10) {
            clearInterval(interval);
            rollBtn.disabled = false;
        }
    }, 100);
};
```

### Calculate Total

```javascript
const total = values.reduce((sum, val) => sum + val, 0);
diceResult.textContent = `Dice: ${values.join(', ')} | Total: ${total}`;
```

### Add Sound Effect

```javascript
const rollSound = new Audio('sounds/dice-roll.mp3');

function rollDice() {
    rollSound.play();
    // ... rest of code
}
```

---

## Summary - Chapter 20

✅ Built dice roller project  
✅ Generated random dice values  
✅ Displayed results as text and images  
✅ Used arrays to store multiple results  
✅ Dynamic HTML generation with `.innerHTML`  

---

# Chapter 21: Random Password Generator Project

## Overview
Create a program that generates random passwords based on user-specified criteria.



---

## 21.1 Project Goal

Build a password generator that:
- Allows customizable password length
- Includes/excludes character types (lowercase, uppercase, numbers, symbols)
- Generates secure random passwords
- Displays result



---

## 21.2 HTML Structure



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Generator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Password Generator</h1>
        
        <!-- Password length input -->
        <label for="passwordLength">Password length:</label>
        <input type="number" id="passwordLength" min="1" max="50" value="12">
        <br><br>
        
        <!-- Checkboxes for character types -->
        <label>
            <input type="checkbox" id="includeLowercase" checked>
            Include Lowercase
        </label>
        <br>
        <label>
            <input type="checkbox" id="includeUppercase" checked>
            Include Uppercase
        </label>
        <br>
        <label>
            <input type="checkbox" id="includeNumbers" checked>
            Include Numbers
        </label>
        <br>
        <label>
            <input type="checkbox" id="includeSymbols" checked>
            Include Symbols
        </label>
        <br><br>
        
        <!-- Generate button -->
        <button id="generateBtn">Generate Password</button>
        <br><br>
        
        <!-- Display result -->
        <div id="passwordDisplay"></div>
    </div>
    
    <script src="index.js"></script>
</body>
</html>
```

, [03:29:02], [03:29:23], [03:29:40]

---

## 21.3 JavaScript - Setup

, [03:30:11], [03:30:28], [03:30:46]

```javascript
// Get HTML elements
const passwordLength = document.getElementById("passwordLength");
const includeLowercase = document.getElementById("includeLowercase");
const includeUppercase = document.getElementById("includeUppercase");
const includeNumbers = document.getElementById("includeNumbers");
const includeSymbols = document.getElementById("includeSymbols");
const passwordDisplay = document.getElementById("passwordDisplay");
const generateBtn = document.getElementById("generateBtn");

// Character sets
const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
const uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
const numberChars = "0123456789";
const symbolChars = "!@#$%^&*()_+-=[]{}|;:,.<>?";
```

, [03:31:15], [03:31:28], [03:31:42]

---

## 21.4 JavaScript - Generate Function



```javascript
function generatePassword() {
    const length = passwordLength.value;
    let allowedChars = "";
    let password = "";
    
    // Build character pool based on selections
    allowedChars += includeLowercase.checked ? lowercaseChars : "";
    allowedChars += includeUppercase.checked ? uppercaseChars : "";
    allowedChars += includeNumbers.checked ? numberChars : "";
    allowedChars += includeSymbols.checked ? symbolChars : "";
    
    // Check if at least one type is selected
    if (allowedChars === "") {
        passwordDisplay.textContent = "Please select at least one character type!";
        return;
    }
    
    // Generate password
    for (let i = 0; i < length; i++) {
        const randomIndex = Math.floor(Math.random() * allowedChars.length);
        password += allowedChars[randomIndex];
    }
    
    // Display result
    passwordDisplay.textContent = password;
}

// Attach event listener
generateBtn.onclick = generatePassword;
```

, [03:32:25], [03:32:46], [03:33:10], [03:33:31], [03:33:48]

---

## 21.5 Step-by-Step Explanation

### Step 1: Get Password Length



```javascript
const length = passwordLength.value;
```

### Step 2: Build Character Pool

, [03:32:46]

```javascript
let allowedChars = "";

allowedChars += includeLowercase.checked ? lowercaseChars : "";
allowedChars += includeUppercase.checked ? uppercaseChars : "";
allowedChars += includeNumbers.checked ? numberChars : "";
allowedChars += includeSymbols.checked ? symbolChars : "";
```

Uses ternary operator to conditionally add character sets.

### Step 3: Validate Selection



```javascript
if (allowedChars === "") {
    passwordDisplay.textContent = "Please select at least one character type!";
    return;
}
```

Ensure at least one character type is selected.

### Step 4: Generate Password



```javascript
for (let i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * allowedChars.length);
    password += allowedChars[randomIndex];
}
```

- Loop for desired length
- Pick random character from pool
- Append to password string

### Step 5: Display Result



```javascript
passwordDisplay.textContent = password;
```

---

## 21.6 Complete JavaScript Code

```javascript
// Get elements
const passwordLength = document.getElementById("passwordLength");
const includeLowercase = document.getElementById("includeLowercase");
const includeUppercase = document.getElementById("includeUppercase");
const includeNumbers = document.getElementById("includeNumbers");
const includeSymbols = document.getElementById("includeSymbols");
const passwordDisplay = document.getElementById("passwordDisplay");
const generateBtn = document.getElementById("generateBtn");

// Character sets
const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
const uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
const numberChars = "0123456789";
const symbolChars = "!@#$%^&*()_+-=[]{}|;:,.<>?";

// Generate password function
function generatePassword() {
    const length = passwordLength.value;
    let allowedChars = "";
    let password = "";
    
    // Build allowed characters
    allowedChars += includeLowercase.checked ? lowercaseChars : "";
    allowedChars += includeUppercase.checked ? uppercaseChars : "";
    allowedChars += includeNumbers.checked ? numberChars : "";
    allowedChars += includeSymbols.checked ? symbolChars : "";
    
    // Validate
    if (allowedChars === "") {
        passwordDisplay.textContent = "⚠ Select at least one option!";
        return;
    }
    
    if (length < 1) {
        passwordDisplay.textContent = "⚠ Password length must be at least 1!";
        return;
    }
    
    // Generate
    for (let i = 0; i < length; i++) {
        const randomIndex = Math.floor(Math.random() * allowedChars.length);
        password += allowedChars[randomIndex];
    }
    
    // Display
    passwordDisplay.textContent = password;
}

// Attach event
generateBtn.onclick = generatePassword;
```

---

## 21.7 CSS Styling (Optional)

```css
body {
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
}

.container {
    background: white;
    padding: 40px;
    border-radius: 15px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
    text-align: center;
    max-width: 400px;
}

h1 {
    color: #333;
    margin-bottom: 20px;
}

label {
    display: block;
    margin: 10px 0;
    text-align: left;
    color: #555;
}

input[type="number"] {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 2px solid #ddd;
    border-radius: 5px;
    margin-top: 5px;
}

input[type="checkbox"] {
    margin-right: 10px;
}

button {
    width: 100%;
    padding: 15px;
    font-size: 18px;
    background: #667eea;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 10px;
}

button:hover {
    background: #5568d3;
}

#passwordDisplay {
    margin-top: 20px;
    padding: 15px;
    background: #f0f0f0;
    border-radius: 5px;
    font-size: 18px;
    font-family: monospace;
    word-break: break-all;
    min-height: 25px;
    color: #333;
}
```

---

## 21.8 Enhancements

### Add Copy to Clipboard

```javascript
function copyToClipboard() {
    const password = passwordDisplay.textContent;
    
    if (password && !password.includes("⚠")) {
        navigator.clipboard.writeText(password);
        alert("Password copied to clipboard!");
    }
}

// Add button in HTML
// <button onclick="copyToClipboard()">Copy</button>
```

### Add Strength Indicator

```javascript
function checkStrength(password) {
    let strength = 0;
    
    if (password.length >= 8) strength++;
    if (password.length >= 12) strength++;
    if (/[a-z]/.test(password)) strength++;
    if (/[A-Z]/.test(password)) strength++;
    if (/[0-9]/.test(password)) strength++;
    if (/[^a-zA-Z0-9]/.test(password)) strength++;
    
    if (strength <= 2) return "Weak";
    if (strength <= 4) return "Medium";
    return "Strong";
}
```

### Save Recent Passwords

```javascript
let passwordHistory = [];

function generatePassword() {
    // ... existing code
    
    passwordHistory.push(password);
    if (passwordHistory.length > 5) {
        passwordHistory.shift(); // Keep only last 5
    }
    
    displayHistory();
}

function displayHistory() {
    const historyDiv = document.getElementById("history");
    historyDiv.innerHTML = "<h3>Recent:</h3>" + 
        passwordHistory.map(p => `<div>${p}</div>`).join("");
}
```

---

## 21.9 Security Considerations

### ✅ Good Practices:
- Use cryptographically secure random generator in production
- Recommend minimum length (8-12 characters)
- Encourage using all character types
- Add password strength indicator
- Never store passwords in plain text

### ⚠️ For Production:
```javascript
// Use crypto API for stronger randomness
function secureRandom(max) {
    const array = new Uint32Array(1);
    crypto.getRandomValues(array);
    return array[0] % max;
}

// Use in password generation
const randomIndex = secureRandom(allowedChars.length);
```

---

## Summary - Chapter 21

✅ Built password generator  
✅ Used checkboxes for options  
✅ Conditional character pool building  
✅ Random character selection  
✅ Input validation  
✅ String concatenation techniques  

---

## Practice Exercises

### Exercise 1: PIN Generator
Create 4-6 digit numeric PIN generator.

### Exercise 2: Memorable Password
Generate passwords with alternating consonants and vowels.

### Exercise 3: Passphrase Generator
Generate passwords from random words list.

### Exercise 4: Custom Symbols
Allow users to input their own symbol set.

---

## Quick Reference

```javascript
// Random character from string
const char = str[Math.floor(Math.random() * str.length)];

// Conditional string building
let result = "";
result += condition ? "add this" : "";

// Checkbox state
if (checkbox.checked) {
    // checkbox is checked
}

// String concatenation in loop
for (let i = 0; i < length; i++) {
    result += someChar;
}
```

---

**Next: Chapters 22 & 23 - Callbacks + Array Methods (forEach, map, filter, reduce)**

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Chapters 18-19: Arrays & Spread/Rest](Chapters-18-19-Arrays-and-Spread-Rest-Operators.md) | [📑 Index](../README.md) | [Chapters 22-23: Callbacks & Array Methods ▶️](Chapters-22-23-Callbacks-and-Array-Methods.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-20--21-dice-roller--password-generator-projects)**

Made with ❤️ for JavaScript learners

</div>
