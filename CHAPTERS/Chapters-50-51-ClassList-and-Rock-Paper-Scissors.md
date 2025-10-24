# Chapters 50 & 51: ClassList + Rock Paper Scissors Project

---

# Chapter 50: ClassList

## Overview
Learn how to manipulate CSS classes dynamically using the classList property.

**Timestamp:** [09:43:28]

---

## 50.1 What is classList?

**Timestamp:** [09:43:35]

**classList:**
- Property that returns DOMTokenList
- Contains all classes of an element
- Provides methods to add, remove, toggle classes
- Better than manipulating `className` directly

```javascript
const element = document.getElementById("myElement");
console.log(element.classList); // DOMTokenList ["class1", "class2"]
```

**Timestamp:** [09:44:10]

---

## 50.2 classList.add()

**Timestamp:** [09:44:40]

Add one or more classes:

```html
<div id="box">Content</div>
```

```javascript
const box = document.getElementById("box");

// Add single class
box.classList.add("highlight");

// Add multiple classes
box.classList.add("large", "blue", "rounded");
```

**Result:**
```html
<div id="box" class="highlight large blue rounded">Content</div>
```

**Timestamp:** [09:45:30]

---

## 50.3 classList.remove()

**Timestamp:** [09:46:00]

Remove one or more classes:

```javascript
const box = document.getElementById("box");

// Remove single class
box.classList.remove("highlight");

// Remove multiple classes
box.classList.remove("large", "blue");
```

---

## 50.4 classList.toggle()

**Timestamp:** [09:46:50]

Toggle class (add if absent, remove if present):

```html
<style>
    .active {
        background-color: yellow;
        font-weight: bold;
    }
</style>

<button id="btn">Click Me</button>
```

```javascript
const btn = document.getElementById("btn");

btn.addEventListener("click", () => {
    btn.classList.toggle("active");
});
```

**First click:** Adds `active` class  
**Second click:** Removes `active` class  
**Third click:** Adds `active` class (repeats)

**Timestamp:** [09:47:50]

---

## 50.5 classList.contains()

**Timestamp:** [09:48:20]

Check if element has a class:

```javascript
const box = document.getElementById("box");

if (box.classList.contains("highlight")) {
    console.log("Box is highlighted");
} else {
    console.log("Box is not highlighted");
}
```

Returns `true` or `false`

**Timestamp:** [09:49:10]

---

## 50.6 classList.replace()

**Timestamp:** [09:49:40]

Replace one class with another:

```javascript
const box = document.getElementById("box");

// Replace "old-class" with "new-class"
box.classList.replace("old-class", "new-class");
```

### Example: Theme Switcher

```javascript
const btn = document.getElementById("themeBtn");

btn.addEventListener("click", () => {
    document.body.classList.replace("light-theme", "dark-theme");
});
```

**Timestamp:** [09:50:40]

---

## 50.7 Practical Example: Active Menu Item

**Timestamp:** [09:51:10]

```html
<style>
    .menu-item {
        padding: 10px 20px;
        cursor: pointer;
        background: #f0f0f0;
    }
    
    .menu-item.active {
        background: #007bff;
        color: white;
    }
</style>

<div class="menu-item">Home</div>
<div class="menu-item">About</div>
<div class="menu-item">Services</div>
<div class="menu-item">Contact</div>
```

```javascript
const menuItems = document.querySelectorAll(".menu-item");

menuItems.forEach(item => {
    item.addEventListener("click", () => {
        // Remove active from all items
        menuItems.forEach(i => i.classList.remove("active"));
        
        // Add active to clicked item
        item.classList.add("active");
    });
});
```

**Timestamp:** [09:53:00]

---

## 50.8 Dark Mode Toggle

**Timestamp:** [09:53:30]

```html
<style>
    body {
        transition: all 0.3s ease;
    }
    
    body.dark-mode {
        background-color: #1a1a1a;
        color: #ffffff;
    }
    
    body.dark-mode button {
        background-color: #333;
        color: #fff;
    }
</style>

<button id="darkModeToggle">Toggle Dark Mode</button>
```

```javascript
const toggleBtn = document.getElementById("darkModeToggle");

toggleBtn.addEventListener("click", () => {
    document.body.classList.toggle("dark-mode");
    
    // Update button text
    if (document.body.classList.contains("dark-mode")) {
        toggleBtn.textContent = "Light Mode";
    } else {
        toggleBtn.textContent = "Dark Mode";
    }
});
```

**Timestamp:** [09:55:10]

---

## 50.9 Tab Navigation Example

**Timestamp:** [09:55:40]

```html
<style>
    .tab {
        padding: 10px 20px;
        cursor: pointer;
        background: #ddd;
        display: inline-block;
    }
    
    .tab.active {
        background: #007bff;
        color: white;
    }
    
    .tab-content {
        display: none;
        padding: 20px;
        border: 1px solid #ddd;
    }
    
    .tab-content.active {
        display: block;
    }
</style>

<div class="tab active" data-tab="tab1">Tab 1</div>
<div class="tab" data-tab="tab2">Tab 2</div>
<div class="tab" data-tab="tab3">Tab 3</div>

<div class="tab-content active" id="tab1">Content 1</div>
<div class="tab-content" id="tab2">Content 2</div>
<div class="tab-content" id="tab3">Content 3</div>
```

```javascript
const tabs = document.querySelectorAll(".tab");
const contents = document.querySelectorAll(".tab-content");

tabs.forEach(tab => {
    tab.addEventListener("click", () => {
        const targetTab = tab.dataset.tab;
        
        // Remove active from all tabs
        tabs.forEach(t => t.classList.remove("active"));
        
        // Remove active from all contents
        contents.forEach(c => c.classList.remove("active"));
        
        // Add active to clicked tab
        tab.classList.add("active");
        
        // Add active to corresponding content
        document.getElementById(targetTab).classList.add("active");
    });
});
```

**Timestamp:** [09:58:20]

---

## 50.10 classList vs className

**Timestamp:** [09:58:50]

### className (Old Way)

```javascript
const box = document.getElementById("box");

// Get classes (returns string)
console.log(box.className); // "class1 class2 class3"

// Set classes (replaces all)
box.className = "new-class";

// Add class (messy)
box.className += " another-class";
```

### classList (Modern Way)

```javascript
// Get classes (returns DOMTokenList)
console.log(box.classList); // DOMTokenList ["class1", "class2", "class3"]

// Add class
box.classList.add("new-class");

// Remove class
box.classList.remove("old-class");

// Toggle class
box.classList.toggle("active");
```

✅ **Always use classList!**

**Timestamp:** [10:00:20]

---

## Summary - Chapter 50

✅ **classList.add()** - Add classes  
✅ **classList.remove()** - Remove classes  
✅ **classList.toggle()** - Toggle class  
✅ **classList.contains()** - Check if has class  
✅ **classList.replace()** - Replace class  
✅ Better than manipulating `className`  
✅ Common uses: themes, active states, animations  

---

# Chapter 51: Rock Paper Scissors Game

## Overview
Build a complete Rock Paper Scissors game with score tracking and visual feedback.

**Timestamp:** [10:00:48]

---

## 51.1 Project Setup

**Timestamp:** [10:00:55]

### HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock Paper Scissors</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="game-container">
        <h1>Rock Paper Scissors</h1>
        
        <div class="score-board">
            <div class="score">
                <h3>Player</h3>
                <p id="playerScore">0</p>
            </div>
            <div class="score">
                <h3>Computer</h3>
                <p id="computerScore">0</p>
            </div>
        </div>
        
        <div class="choices">
            <button class="choice-btn" data-choice="rock">✊ Rock</button>
            <button class="choice-btn" data-choice="paper">✋ Paper</button>
            <button class="choice-btn" data-choice="scissors">✌️ Scissors</button>
        </div>
        
        <div class="result">
            <p id="playerChoice">Your choice: -</p>
            <p id="computerChoice">Computer: -</p>
            <h2 id="result">Choose your weapon!</h2>
        </div>
        
        <button id="resetBtn">Reset Game</button>
    </div>
    
    <script src="index.js"></script>
</body>
</html>
```

**Timestamp:** [10:02:30]

---

## 51.2 CSS Styling

**Timestamp:** [10:03:00]

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    padding: 20px;
}

.game-container {
    background: rgba(255, 255, 255, 0.95);
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
    text-align: center;
    max-width: 600px;
    width: 100%;
}

h1 {
    color: #333;
    margin-bottom: 30px;
    font-size: 36px;
}

.score-board {
    display: flex;
    justify-content: space-around;
    margin-bottom: 40px;
}

.score {
    padding: 20px;
    background: #f0f0f0;
    border-radius: 10px;
    min-width: 150px;
}

.score h3 {
    color: #666;
    margin-bottom: 10px;
}

.score p {
    font-size: 48px;
    font-weight: bold;
    color: #007bff;
}

.choices {
    display: flex;
    gap: 15px;
    justify-content: center;
    margin-bottom: 40px;
    flex-wrap: wrap;
}

.choice-btn {
    padding: 20px 30px;
    font-size: 24px;
    border: none;
    border-radius: 10px;
    background: #007bff;
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
}

.choice-btn:hover {
    background: #0056b3;
    transform: translateY(-5px);
    box-shadow: 0 5px 15px rgba(0, 123, 255, 0.4);
}

.choice-btn:active {
    transform: translateY(0);
}

.result {
    background: #f8f9fa;
    padding: 30px;
    border-radius: 10px;
    margin-bottom: 30px;
}

.result p {
    font-size: 20px;
    margin: 10px 0;
    color: #666;
}

.result h2 {
    font-size: 32px;
    margin-top: 20px;
    color: #333;
}

.result h2.win {
    color: #28a745;
}

.result h2.lose {
    color: #dc3545;
}

.result h2.tie {
    color: #ffc107;
}

#resetBtn {
    padding: 15px 40px;
    font-size: 18px;
    border: none;
    border-radius: 10px;
    background: #6c757d;
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
}

#resetBtn:hover {
    background: #5a6268;
    transform: scale(1.05);
}
```

**Timestamp:** [10:06:00]

---

## 51.3 JavaScript - Variables Setup

**Timestamp:** [10:06:30]

```javascript
const choiceBtns = document.querySelectorAll(".choice-btn");
const playerScoreDisplay = document.getElementById("playerScore");
const computerScoreDisplay = document.getElementById("computerScore");
const playerChoiceDisplay = document.getElementById("playerChoice");
const computerChoiceDisplay = document.getElementById("computerChoice");
const resultDisplay = document.getElementById("result");
const resetBtn = document.getElementById("resetBtn");

let playerScore = 0;
let computerScore = 0;
```

**Timestamp:** [10:07:20]

---

## 51.4 Computer Choice Function

**Timestamp:** [10:07:50]

```javascript
function getComputerChoice() {
    const choices = ["rock", "paper", "scissors"];
    const randomIndex = Math.floor(Math.random() * 3);
    return choices[randomIndex];
}
```

**Timestamp:** [10:08:30]

---

## 51.5 Determine Winner Function

**Timestamp:** [10:09:00]

```javascript
function determineWinner(player, computer) {
    if (player === computer) {
        return "tie";
    }
    
    if (
        (player === "rock" && computer === "scissors") ||
        (player === "paper" && computer === "rock") ||
        (player === "scissors" && computer === "paper")
    ) {
        return "player";
    } else {
        return "computer";
    }
}
```

**Timestamp:** [10:10:15]

---

## 51.6 Update Display Function

**Timestamp:** [10:10:45]

```javascript
function updateDisplay(playerChoice, computerChoice, winner) {
    // Update choices
    playerChoiceDisplay.textContent = `Your choice: ${playerChoice}`;
    computerChoiceDisplay.textContent = `Computer: ${computerChoice}`;
    
    // Update result
    resultDisplay.classList.remove("win", "lose", "tie");
    
    if (winner === "player") {
        playerScore++;
        resultDisplay.textContent = "You Win! 🎉";
        resultDisplay.classList.add("win");
    } else if (winner === "computer") {
        computerScore++;
        resultDisplay.textContent = "You Lose! 😢";
        resultDisplay.classList.add("lose");
    } else {
        resultDisplay.textContent = "It's a Tie! 🤝";
        resultDisplay.classList.add("tie");
    }
    
    // Update scores
    playerScoreDisplay.textContent = playerScore;
    computerScoreDisplay.textContent = computerScore;
}
```

**Timestamp:** [10:12:30]

---

## 51.7 Play Game Function

**Timestamp:** [10:13:00]

```javascript
function playGame(playerChoice) {
    const computerChoice = getComputerChoice();
    const winner = determineWinner(playerChoice, computerChoice);
    updateDisplay(playerChoice, computerChoice, winner);
}
```

---

## 51.8 Event Listeners

**Timestamp:** [10:13:40]

```javascript
// Add click listener to each choice button
choiceBtns.forEach(btn => {
    btn.addEventListener("click", () => {
        const playerChoice = btn.dataset.choice;
        playGame(playerChoice);
    });
});

// Reset button
resetBtn.addEventListener("click", () => {
    playerScore = 0;
    computerScore = 0;
    playerScoreDisplay.textContent = "0";
    computerScoreDisplay.textContent = "0";
    playerChoiceDisplay.textContent = "Your choice: -";
    computerChoiceDisplay.textContent = "Computer: -";
    resultDisplay.textContent = "Choose your weapon!";
    resultDisplay.classList.remove("win", "lose", "tie");
});
```

**Timestamp:** [10:15:10]

---

## 51.9 Complete JavaScript Code

**Timestamp:** [10:15:40]

```javascript
// Select elements
const choiceBtns = document.querySelectorAll(".choice-btn");
const playerScoreDisplay = document.getElementById("playerScore");
const computerScoreDisplay = document.getElementById("computerScore");
const playerChoiceDisplay = document.getElementById("playerChoice");
const computerChoiceDisplay = document.getElementById("computerChoice");
const resultDisplay = document.getElementById("result");
const resetBtn = document.getElementById("resetBtn");

// Game state
let playerScore = 0;
let computerScore = 0;

// Get random computer choice
function getComputerChoice() {
    const choices = ["rock", "paper", "scissors"];
    const randomIndex = Math.floor(Math.random() * 3);
    return choices[randomIndex];
}

// Determine winner
function determineWinner(player, computer) {
    if (player === computer) {
        return "tie";
    }
    
    if (
        (player === "rock" && computer === "scissors") ||
        (player === "paper" && computer === "rock") ||
        (player === "scissors" && computer === "paper")
    ) {
        return "player";
    } else {
        return "computer";
    }
}

// Update display
function updateDisplay(playerChoice, computerChoice, winner) {
    // Show emoji for choices
    const emojis = {
        rock: "✊",
        paper: "✋",
        scissors: "✌️"
    };
    
    playerChoiceDisplay.textContent = `Your choice: ${emojis[playerChoice]} ${playerChoice}`;
    computerChoiceDisplay.textContent = `Computer: ${emojis[computerChoice]} ${computerChoice}`;
    
    // Remove previous result classes
    resultDisplay.classList.remove("win", "lose", "tie");
    
    // Update result and score
    if (winner === "player") {
        playerScore++;
        resultDisplay.textContent = "You Win! 🎉";
        resultDisplay.classList.add("win");
    } else if (winner === "computer") {
        computerScore++;
        resultDisplay.textContent = "You Lose! 😢";
        resultDisplay.classList.add("lose");
    } else {
        resultDisplay.textContent = "It's a Tie! 🤝";
        resultDisplay.classList.add("tie");
    }
    
    // Update scores
    playerScoreDisplay.textContent = playerScore;
    computerScoreDisplay.textContent = computerScore;
}

// Main game function
function playGame(playerChoice) {
    const computerChoice = getComputerChoice();
    const winner = determineWinner(playerChoice, computerChoice);
    updateDisplay(playerChoice, computerChoice, winner);
}

// Event listeners for choice buttons
choiceBtns.forEach(btn => {
    btn.addEventListener("click", () => {
        const playerChoice = btn.dataset.choice;
        playGame(playerChoice);
    });
});

// Reset button
resetBtn.addEventListener("click", () => {
    playerScore = 0;
    computerScore = 0;
    playerScoreDisplay.textContent = "0";
    computerScoreDisplay.textContent = "0";
    playerChoiceDisplay.textContent = "Your choice: -";
    computerChoiceDisplay.textContent = "Computer: -";
    resultDisplay.textContent = "Choose your weapon!";
    resultDisplay.classList.remove("win", "lose", "tie");
});
```

**Timestamp:** [10:18:18]

---

## 51.10 Game Logic Explained

**Timestamp:** [10:18:30]

### Winning Conditions

- **Rock** beats **Scissors** (crushes)
- **Paper** beats **Rock** (covers)
- **Scissors** beats **Paper** (cuts)

### Game Flow

1. Player clicks choice button
2. Get player's choice from data attribute
3. Generate random computer choice
4. Compare choices to determine winner
5. Update scores and display results
6. Apply visual feedback with CSS classes

---

## Summary - Chapter 51

✅ Built complete Rock Paper Scissors game  
✅ Score tracking system  
✅ Random computer choice generation  
✅ Winner determination logic  
✅ Visual feedback with classList  
✅ Reset functionality  
✅ Responsive design  
✅ Emoji for visual appeal  

---

## Practice Exercises

### Exercise 1: Best of 5
Add round limit and declare final winner.

### Exercise 2: Game History
Display last 5 moves and results.

### Exercise 3: Difficulty Levels
Add AI difficulty (easy/hard).

### Exercise 4: Sound Effects
Add sounds for win/lose/tie.

---

## Quick Reference

```javascript
// classList Methods
element.classList.add("class1", "class2");
element.classList.remove("class1");
element.classList.toggle("active");
element.classList.contains("active"); // true/false
element.classList.replace("old", "new");

// Rock Paper Scissors Logic
function determineWinner(player, computer) {
    if (player === computer) return "tie";
    
    if (
        (player === "rock" && computer === "scissors") ||
        (player === "paper" && computer === "rock") ||
        (player === "scissors" && computer === "paper")
    ) {
        return "player";
    }
    return "computer";
}

// Random choice
const choices = ["rock", "paper", "scissors"];
const random = choices[Math.floor(Math.random() * 3)];
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Chapters 48 & 49: Show/Hide Elements + NodeLists](Chapters-48-49-Show-Hide-and-NodeLists.md) | [📑 Index](../README.md) | [Chapters 52 & 53: Image Slider + Callback Hell ▶️](Chapters-52-53-Image-Slider-and-Callback-Hell.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-50--51-classlist--rock-paper-scissors-project)**

Made with ❤️ for JavaScript learners

</div>

**Next: Chapters 52 & 53 - Image Slider + Callback Hell**
