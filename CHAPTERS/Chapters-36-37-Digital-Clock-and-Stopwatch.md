# Chapters 36 & 37: Digital Clock + Stopwatch Projects

---

# Chapter 36: Digital Clock Project

## Overview
Build a digital clock that displays the current time and updates every second using JavaScript's Date object and setInterval.

**Timestamp:** [07:05:21]

---

## 36.1 Project Setup

**Timestamp:** [07:05:28]

### HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Digital Clock</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="clockContainer">
        <div id="clock">00:00:00</div>
        <div id="date"></div>
    </div>
    
    <script src="index.js"></script>
</body>
</html>
```

**Timestamp:** [07:05:40]

---

## 36.2 CSS Styling

**Timestamp:** [07:06:15]

```css
body {
    margin: 0;
    padding: 0;
    font-family: 'Arial', sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

#clockContainer {
    text-align: center;
    background: rgba(255, 255, 255, 0.1);
    padding: 50px;
    border-radius: 20px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
    backdrop-filter: blur(10px);
}

#clock {
    font-size: 80px;
    font-weight: bold;
    color: #fff;
    text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
    letter-spacing: 5px;
    margin-bottom: 20px;
}

#date {
    font-size: 24px;
    color: rgba(255, 255, 255, 0.9);
    letter-spacing: 2px;
}
```

**Timestamp:** [07:07:30]

---

## 36.3 JavaScript Implementation

**Timestamp:** [07:08:45]

### Basic Clock Function

```javascript
function updateClock() {
    const now = new Date();
    
    let hours = now.getHours();
    let minutes = now.getMinutes();
    let seconds = now.getSeconds();
    
    // Add leading zeros
    hours = hours < 10 ? "0" + hours : hours;
    minutes = minutes < 10 ? "0" + minutes : minutes;
    seconds = seconds < 10 ? "0" + seconds : seconds;
    
    const timeString = `${hours}:${minutes}:${seconds}`;
    
    document.getElementById("clock").textContent = timeString;
}

// Update every second
setInterval(updateClock, 1000);

// Call immediately to avoid 1-second delay
updateClock();
```

**Timestamp:** [07:09:20]

---

## 36.4 Adding 12-Hour Format

**Timestamp:** [07:10:35]

```javascript
function updateClock() {
    const now = new Date();
    
    let hours = now.getHours();
    const minutes = now.getMinutes();
    const seconds = now.getSeconds();
    const meridiem = hours >= 12 ? "PM" : "AM";
    
    // Convert to 12-hour format
    hours = hours % 12 || 12;
    
    // Format with leading zeros
    hours = String(hours).padStart(2, "0");
    const min = String(minutes).padStart(2, "0");
    const sec = String(seconds).padStart(2, "0");
    
    const timeString = `${hours}:${min}:${sec} ${meridiem}`;
    
    document.getElementById("clock").textContent = timeString;
}

setInterval(updateClock, 1000);
updateClock();
```

**Timestamp:** [07:11:48]

---

## 36.5 Adding Date Display

**Timestamp:** [07:12:20]

```javascript
function updateClock() {
    const now = new Date();
    
    // Time
    let hours = now.getHours();
    const minutes = now.getMinutes();
    const seconds = now.getSeconds();
    const meridiem = hours >= 12 ? "PM" : "AM";
    
    hours = hours % 12 || 12;
    const timeString = `${String(hours).padStart(2, "0")}:${String(minutes).padStart(2, "0")}:${String(seconds).padStart(2, "0")} ${meridiem}`;
    
    // Date
    const days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
    const months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
    
    const dayName = days[now.getDay()];
    const monthName = months[now.getMonth()];
    const date = now.getDate();
    const year = now.getFullYear();
    
    const dateString = `${dayName}, ${monthName} ${date}, ${year}`;
    
    // Update display
    document.getElementById("clock").textContent = timeString;
    document.getElementById("date").textContent = dateString;
}

setInterval(updateClock, 1000);
updateClock();
```

**Timestamp:** [07:13:55]

---

## 36.6 Complete Enhanced Version

**Timestamp:** [07:14:30]

```javascript
function updateClock() {
    const now = new Date();
    
    // Get time components
    let hours = now.getHours();
    const minutes = now.getMinutes();
    const seconds = now.getSeconds();
    const meridiem = hours >= 12 ? "PM" : "AM";
    
    // Convert to 12-hour format
    hours = hours % 12 || 12;
    
    // Format time with leading zeros
    const formattedTime = `${String(hours).padStart(2, "0")}:${String(minutes).padStart(2, "0")}:${String(seconds).padStart(2, "0")} ${meridiem}`;
    
    // Format date
    const options = { 
        weekday: 'long', 
        year: 'numeric', 
        month: 'long', 
        day: 'numeric' 
    };
    const formattedDate = now.toLocaleDateString('en-US', options);
    
    // Update display
    document.getElementById("clock").textContent = formattedTime;
    document.getElementById("date").textContent = formattedDate;
}

// Update every second
setInterval(updateClock, 1000);

// Initial call
updateClock();
```

---

## 36.7 Key Concepts Used

✅ **Date Object:** Get current time  
✅ **setInterval:** Update every second  
✅ **String Methods:** Format numbers with leading zeros  
✅ **Conditional Operator:** 12-hour format conversion  
✅ **DOM Manipulation:** Update text content  

---

## Summary - Chapter 36

✅ Created digital clock displaying current time  
✅ Used `setInterval` for continuous updates  
✅ Implemented 12-hour format with AM/PM  
✅ Added date display  
✅ Applied CSS styling for visual appeal  
✅ Used `padStart()` for leading zeros  

---

# Chapter 37: Stopwatch Project

## Overview
Build a fully functional stopwatch with start, stop, and reset buttons.

**Timestamp:** [07:15:57]

---

## 37.1 Project Setup

**Timestamp:** [07:16:05]

### HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="stopwatch">
        <div id="display">00:00:00:00</div>
        <div id="controls">
            <button id="startBtn">Start</button>
            <button id="stopBtn">Stop</button>
            <button id="resetBtn">Reset</button>
        </div>
    </div>
    
    <script src="index.js"></script>
</body>
</html>
```

**Timestamp:** [07:16:20]

---

## 37.2 CSS Styling

**Timestamp:** [07:17:10]

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

#stopwatch {
    background: rgba(255, 255, 255, 0.1);
    padding: 50px;
    border-radius: 20px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
    text-align: center;
    backdrop-filter: blur(10px);
}

#display {
    font-size: 72px;
    font-weight: bold;
    color: #fff;
    text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
    margin-bottom: 30px;
    letter-spacing: 5px;
}

#controls {
    display: flex;
    gap: 15px;
    justify-content: center;
}

button {
    padding: 15px 30px;
    font-size: 18px;
    font-weight: bold;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: all 0.3s ease;
    text-transform: uppercase;
}

#startBtn {
    background: #4CAF50;
    color: white;
}

#startBtn:hover {
    background: #45a049;
    transform: scale(1.05);
}

#stopBtn {
    background: #f44336;
    color: white;
}

#stopBtn:hover {
    background: #da190b;
    transform: scale(1.05);
}

#resetBtn {
    background: #2196F3;
    color: white;
}

#resetBtn:hover {
    background: #0b7dda;
    transform: scale(1.05);
}

button:active {
    transform: scale(0.95);
}
```

**Timestamp:** [07:18:45]

---

## 37.3 JavaScript Implementation

**Timestamp:** [07:19:30]

### Variable Setup

```javascript
const display = document.getElementById("display");
const startBtn = document.getElementById("startBtn");
const stopBtn = document.getElementById("stopBtn");
const resetBtn = document.getElementById("resetBtn");

let startTime = 0;
let elapsedTime = 0;
let timerInterval;
let isRunning = false;
```

**Timestamp:** [07:20:15]

---

## 37.4 Start Function

**Timestamp:** [07:20:45]

```javascript
function start() {
    if (!isRunning) {
        startTime = Date.now() - elapsedTime;
        timerInterval = setInterval(update, 10);
        isRunning = true;
    }
}

startBtn.addEventListener("click", start);
```

---

## 37.5 Stop Function

**Timestamp:** [07:21:30]

```javascript
function stop() {
    if (isRunning) {
        clearInterval(timerInterval);
        isRunning = false;
    }
}

stopBtn.addEventListener("click", stop);
```

---

## 37.6 Reset Function

**Timestamp:** [07:22:05]

```javascript
function reset() {
    clearInterval(timerInterval);
    startTime = 0;
    elapsedTime = 0;
    isRunning = false;
    display.textContent = "00:00:00:00";
}

resetBtn.addEventListener("click", reset);
```

---

## 37.7 Update Function

**Timestamp:** [07:22:50]

```javascript
function update() {
    const currentTime = Date.now();
    elapsedTime = currentTime - startTime;
    
    let hours = Math.floor(elapsedTime / (1000 * 60 * 60));
    let minutes = Math.floor(elapsedTime / (1000 * 60) % 60);
    let seconds = Math.floor(elapsedTime / 1000 % 60);
    let milliseconds = Math.floor(elapsedTime % 1000 / 10);
    
    hours = String(hours).padStart(2, "0");
    minutes = String(minutes).padStart(2, "0");
    seconds = String(seconds).padStart(2, "0");
    milliseconds = String(milliseconds).padStart(2, "0");
    
    display.textContent = `${hours}:${minutes}:${seconds}:${milliseconds}`;
}
```

**Timestamp:** [07:24:10]

---

## 37.8 Complete Code

**Timestamp:** [07:24:45]

```javascript
// Select elements
const display = document.getElementById("display");
const startBtn = document.getElementById("startBtn");
const stopBtn = document.getElementById("stopBtn");
const resetBtn = document.getElementById("resetBtn");

// Variables
let startTime = 0;
let elapsedTime = 0;
let timerInterval;
let isRunning = false;

// Start function
function start() {
    if (!isRunning) {
        startTime = Date.now() - elapsedTime;
        timerInterval = setInterval(update, 10);
        isRunning = true;
    }
}

// Stop function
function stop() {
    if (isRunning) {
        clearInterval(timerInterval);
        isRunning = false;
    }
}

// Reset function
function reset() {
    clearInterval(timerInterval);
    startTime = 0;
    elapsedTime = 0;
    isRunning = false;
    display.textContent = "00:00:00:00";
}

// Update display
function update() {
    const currentTime = Date.now();
    elapsedTime = currentTime - startTime;
    
    let hours = Math.floor(elapsedTime / (1000 * 60 * 60));
    let minutes = Math.floor(elapsedTime / (1000 * 60) % 60);
    let seconds = Math.floor(elapsedTime / 1000 % 60);
    let milliseconds = Math.floor(elapsedTime % 1000 / 10);
    
    hours = String(hours).padStart(2, "0");
    minutes = String(minutes).padStart(2, "0");
    seconds = String(seconds).padStart(2, "0");
    milliseconds = String(milliseconds).padStart(2, "0");
    
    display.textContent = `${hours}:${minutes}:${seconds}:${milliseconds}`;
}

// Event listeners
startBtn.addEventListener("click", start);
stopBtn.addEventListener("click", stop);
resetBtn.addEventListener("click", reset);
```

**Timestamp:** [07:26:20]

---

## 37.9 How It Works

**Timestamp:** [07:27:05]

### Time Calculation

1. **Start Time:** When "Start" is clicked, record `Date.now()`
2. **Elapsed Time:** Calculate difference between current time and start time
3. **Update Display:** Convert milliseconds to hours:minutes:seconds:milliseconds

### Example Calculation

```javascript
elapsedTime = 125743; // milliseconds

hours = 125743 / (1000 * 60 * 60) = 0.034 → floor → 0
minutes = 125743 / (1000 * 60) % 60 = 2.095 % 60 = 2
seconds = 125743 / 1000 % 60 = 125.743 % 60 = 5
milliseconds = 125743 % 1000 / 10 = 743 / 10 = 74

Result: 00:02:05:74
```

**Timestamp:** [07:28:30]

---

## 37.10 Enhanced Version with Lap Times

**Timestamp:** [07:29:15]

### HTML Addition

```html
<button id="lapBtn">Lap</button>
<div id="laps"></div>
```

### JavaScript Addition

```javascript
let lapCount = 0;

function recordLap() {
    if (isRunning) {
        lapCount++;
        const lapTime = display.textContent;
        const lapElement = document.createElement("div");
        lapElement.className = "lap";
        lapElement.textContent = `Lap ${lapCount}: ${lapTime}`;
        document.getElementById("laps").prepend(lapElement);
    }
}

document.getElementById("lapBtn").addEventListener("click", recordLap);

// Clear laps on reset
function reset() {
    clearInterval(timerInterval);
    startTime = 0;
    elapsedTime = 0;
    isRunning = false;
    display.textContent = "00:00:00:00";
    document.getElementById("laps").innerHTML = "";
    lapCount = 0;
}
```

---

## 37.11 Key Concepts Used

✅ **Date.now():** Get current timestamp  
✅ **setInterval/clearInterval:** Timer control  
✅ **Math.floor():** Round down time values  
✅ **Modulo operator (%):** Extract time components  
✅ **padStart():** Format with leading zeros  
✅ **Boolean flag:** Track running state  

---

## 37.12 Common Patterns

### Pattern 1: Preventing Multiple Intervals

```javascript
if (!isRunning) {
    // Only start if not already running
    timerInterval = setInterval(update, 10);
    isRunning = true;
}
```

### Pattern 2: Preserving Elapsed Time

```javascript
// When starting after pause
startTime = Date.now() - elapsedTime;
```

This ensures the stopwatch continues from where it stopped.

---

## Summary - Chapter 37

✅ Built stopwatch with start/stop/reset controls  
✅ Used `Date.now()` for precise timing  
✅ Implemented `setInterval` for updates  
✅ Calculated hours, minutes, seconds, milliseconds  
✅ Used `padStart()` for formatting  
✅ Prevented multiple intervals with boolean flag  
✅ Enhanced with lap time tracking (optional)  

---

## Practice Exercises

### Exercise 1: Countdown Timer
Create timer that counts down from specified time.

### Exercise 2: Pomodoro Timer
25-minute work timer with 5-minute breaks.

### Exercise 3: Alarm Clock
Set alarm for specific time with sound notification.

### Exercise 4: World Clock
Display time in multiple time zones.

---

## Quick Reference

```javascript
// Digital Clock
function updateClock() {
    const now = new Date();
    let hours = now.getHours();
    const minutes = now.getMinutes();
    const seconds = now.getSeconds();
    
    hours = hours % 12 || 12;
    const time = `${String(hours).padStart(2, "0")}:${String(minutes).padStart(2, "0")}:${String(seconds).padStart(2, "0")}`;
    
    document.getElementById("clock").textContent = time;
}
setInterval(updateClock, 1000);

// Stopwatch
let startTime = 0;
let elapsedTime = 0;
let timerInterval;

function start() {
    startTime = Date.now() - elapsedTime;
    timerInterval = setInterval(update, 10);
}

function stop() {
    clearInterval(timerInterval);
}

function reset() {
    clearInterval(timerInterval);
    elapsedTime = 0;
}

function update() {
    elapsedTime = Date.now() - startTime;
    // Format and display
}
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Closures & setTimeout](Chapters-34-35-Closures-and-setTimeout.md) | [📑 Index](../README.md) | [ES6 Modules & Async Code ▶️](Chapters-38-39-ES6-Modules-and-Async-Code.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-36--37-digital-clock--stopwatch-projects)**

Made with ❤️ for JavaScript learners

</div>
