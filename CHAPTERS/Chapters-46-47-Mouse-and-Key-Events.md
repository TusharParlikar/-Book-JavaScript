# Chapters 46 & 47: Mouse Events + Key Events

---

# Chapter 46: Mouse Events

## Overview
Learn how to handle user mouse interactions like clicks, hovers, and movements.



---

## 46.1 What are Events?



**Events:**
- Actions that happen in the browser
- User interactions (clicks, typing, mouse movement)
- System events (page load, resize)
- JavaScript can "listen" for events and respond

---

## 46.2 addEventListener()



**Syntax:**
```javascript
element.addEventListener(event, callback);
```

**Example:**
```html
<button id="myBtn">Click Me</button>
```

```javascript
const btn = document.getElementById("myBtn");

btn.addEventListener("click", () => {
    console.log("Button clicked!");
});
// Output: Button clicked! (every time button is clicked)
```



---

## 46.3 The Event Object



Every event handler receives an **event object**:

```javascript
btn.addEventListener("click", (event) => {
    console.log(event); 
    // Output: PointerEvent object
    console.log(event.type); 
    // Output: click
    console.log(event.target); 
    // Output: <button id="myBtn">
    console.log(event.clientX); 
    // Output: 245
    console.log(event.clientY); 
    // Output: 120
});
```



---

## 46.4 Click Event



```html
<button id="btn">Click Me</button>
<p id="output"></p>
```

```javascript
const btn = document.getElementById("btn");
const output = document.getElementById("output");
let count = 0;

btn.addEventListener("click", () => {
    count++;
    output.textContent = `Clicked ${count} times`;
});
// Output: Display updates as "Clicked 1 times", "Clicked 2 times", etc.
```



---

## 46.5 Double Click Event



```javascript
const box = document.getElementById("box");

box.addEventListener("dblclick", () => {
    console.log("Double clicked!");
    box.style.backgroundColor = "red";
});
```

---

## 46.6 Mouse Enter & Mouse Leave



```html
<div id="box" style="width: 200px; height: 200px; background: lightblue;">
    Hover over me
</div>
```

### mouseenter

```javascript
const box = document.getElementById("box");

box.addEventListener("mouseenter", () => {
    box.style.backgroundColor = "lightgreen";
    console.log("Mouse entered!");
});
```

### mouseleave

```javascript
box.addEventListener("mouseleave", () => {
    box.style.backgroundColor = "lightblue";
    console.log("Mouse left!");
});
```



---

## 46.7 Mouse Over & Mouse Out



Similar to enter/leave but **bubble** (trigger on children too):

```javascript
// mouseover: Triggers when entering element OR its children
box.addEventListener("mouseover", () => {
    console.log("Mouse over");
});

// mouseout: Triggers when leaving element OR its children
box.addEventListener("mouseout", () => {
    console.log("Mouse out");
});
```

**Use mouseenter/mouseleave** for cleaner behavior!



---

## 46.8 Mouse Move Event



Track mouse position:

```html
<div id="coords"></div>
```

```javascript
const coords = document.getElementById("coords");

document.addEventListener("mousemove", (e) => {
    coords.textContent = `X: ${e.clientX}, Y: ${e.clientY}`;
});
```

### Create Mouse Follower

```html
<div id="follower" style="position: fixed; width: 20px; height: 20px; background: red; border-radius: 50%; pointer-events: none;"></div>
```

```javascript
const follower = document.getElementById("follower");

document.addEventListener("mousemove", (e) => {
    follower.style.left = e.clientX + "px";
    follower.style.top = e.clientY + "px";
});
```



---

## 46.9 Mouse Down & Mouse Up



```javascript
const btn = document.getElementById("btn");

btn.addEventListener("mousedown", () => {
    console.log("Mouse button pressed");
    btn.style.transform = "scale(0.9)";
});

btn.addEventListener("mouseup", () => {
    console.log("Mouse button released");
    btn.style.transform = "scale(1)";
});
```

---

## 46.10 Context Menu (Right Click)



```javascript
const box = document.getElementById("box");

box.addEventListener("contextmenu", (e) => {
    e.preventDefault(); // Prevent default right-click menu
    console.log("Right clicked!");
    alert("Custom context menu");
});
```



---

## 46.11 Practical Example: Hover Card



```html
<style>
    .card {
        width: 300px;
        padding: 20px;
        background: #f0f0f0;
        border-radius: 10px;
        transition: all 0.3s ease;
    }
    
    .card.hover {
        background: #e0e0e0;
        transform: translateY(-5px);
        box-shadow: 0 5px 15px rgba(0,0,0,0.3);
    }
</style>

<div class="card">
    <h3>Hover over me</h3>
    <p>I'll animate!</p>
</div>
```

```javascript
const card = document.querySelector(".card");

card.addEventListener("mouseenter", () => {
    card.classList.add("hover");
});

card.addEventListener("mouseleave", () => {
    card.classList.remove("hover");
});
```



---

## 46.12 Event Delegation



Handle events on multiple elements efficiently:

```html
<ul id="list">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
    <li>Item 5</li>
</ul>
```

### Bad Approach (Multiple Listeners)

```javascript
const items = document.querySelectorAll("li");

items.forEach(item => {
    item.addEventListener("click", () => {
        console.log(item.textContent);
    });
});
```

### Good Approach (Event Delegation)

```javascript
const list = document.getElementById("list");

list.addEventListener("click", (e) => {
    if (e.target.tagName === "LI") {
        console.log(e.target.textContent);
    }
});
```

✅ **One listener instead of many!**  
✅ **Works for dynamically added elements!**



---

## 46.13 Common Mouse Events Summary

| Event | Triggers When |
|-------|--------------|
| `click` | Left mouse button clicked and released |
| `dblclick` | Double clicked |
| `mousedown` | Mouse button pressed down |
| `mouseup` | Mouse button released |
| `mouseenter` | Mouse enters element (no bubble) |
| `mouseleave` | Mouse leaves element (no bubble) |
| `mouseover` | Mouse enters element or children |
| `mouseout` | Mouse leaves element or children |
| `mousemove` | Mouse moves over element |
| `contextmenu` | Right mouse button clicked |



---

## Summary - Chapter 46

✅ **addEventListener()** - Attach event handlers  
✅ **Event object** - Information about event  
✅ **click** - Most common event  
✅ **mouseenter/mouseleave** - Hover effects  
✅ **mousemove** - Track mouse position  
✅ **Event delegation** - Efficient event handling  

---

# Chapter 47: Key Events

## Overview
Learn how to handle keyboard input with JavaScript.



---

## 47.1 Keyboard Events



Three main keyboard events:

1. **keydown** - Key is pressed down
2. **keyup** - Key is released
3. **keypress** - Key is pressed (deprecated, avoid)

✅ **Use keydown and keyup**

---

## 47.2 keydown Event



Fires when key is first pressed:

```javascript
document.addEventListener("keydown", (e) => {
    console.log("Key pressed:", e.key);
});
```

**Try typing in the page!**



---

## 47.3 keyup Event



Fires when key is released:

```javascript
document.addEventListener("keyup", (e) => {
    console.log("Key released:", e.key);
});
```

---

## 47.4 The Key Property



```javascript
document.addEventListener("keydown", (e) => {
    console.log(e.key); // The actual key: "a", "Enter", "Shift", etc.
    console.log(e.code); // Physical key: "KeyA", "Enter", "ShiftLeft"
    console.log(e.keyCode); // Numeric code (deprecated)
});
```

### Examples

| Key | e.key | e.code |
|-----|-------|--------|
| A | "a" or "A" | "KeyA" |
| Enter | "Enter" | "Enter" |
| Space | " " | "Space" |
| Arrow Up | "ArrowUp" | "ArrowUp" |
| Shift | "Shift" | "ShiftLeft" or "ShiftRight" |



---

## 47.5 Detecting Specific Keys



```javascript
document.addEventListener("keydown", (e) => {
    if (e.key === "Enter") {
        console.log("Enter pressed!");
    }
    
    if (e.key === " ") { // Space
        console.log("Space pressed!");
    }
    
    if (e.key === "Escape") {
        console.log("Escape pressed!");
    }
    
    if (e.key === "ArrowUp") {
        console.log("Up arrow pressed!");
    }
});
```



---

## 47.6 Modifier Keys



Detect Shift, Ctrl, Alt:

```javascript
document.addEventListener("keydown", (e) => {
    console.log("Key:", e.key);
    console.log("Shift:", e.shiftKey); // true/false
    console.log("Ctrl:", e.ctrlKey);   // true/false
    console.log("Alt:", e.altKey);     // true/false
    console.log("Meta:", e.metaKey);   // Command (Mac) / Windows key
});
```

### Keyboard Shortcuts

```javascript
document.addEventListener("keydown", (e) => {
    // Ctrl + S (Save)
    if (e.ctrlKey && e.key === "s") {
        e.preventDefault(); // Stop browser default
        console.log("Save triggered!");
    }
    
    // Ctrl + Z (Undo)
    if (e.ctrlKey && e.key === "z") {
        e.preventDefault();
        console.log("Undo triggered!");
    }
});
```



---

## 47.7 Input Field Events



```html
<input type="text" id="textInput" placeholder="Type here">
<p id="output"></p>
```

### Display Typed Text

```javascript
const input = document.getElementById("textInput");
const output = document.getElementById("output");

input.addEventListener("keyup", (e) => {
    output.textContent = `You typed: ${e.target.value}`;
});
```

### Character Counter

```javascript
input.addEventListener("keyup", () => {
    const length = input.value.length;
    output.textContent = `Characters: ${length}`;
});
```



---

## 47.8 Practical Example: Character Movement



```html
<style>
    #player {
        position: absolute;
        width: 50px;
        height: 50px;
        background: red;
        border-radius: 5px;
    }
</style>

<div id="player"></div>
```

```javascript
const player = document.getElementById("player");

let x = 0;
let y = 0;
const speed = 10;

document.addEventListener("keydown", (e) => {
    if (e.key === "ArrowLeft") {
        x -= speed;
    } else if (e.key === "ArrowRight") {
        x += speed;
    } else if (e.key === "ArrowUp") {
        y -= speed;
    } else if (e.key === "ArrowDown") {
        y += speed;
    }
    
    // Update position
    player.style.left = x + "px";
    player.style.top = y + "px";
});
```



---

## 47.9 Preventing Default Behavior



```javascript
// Prevent spacebar from scrolling page
document.addEventListener("keydown", (e) => {
    if (e.key === " ") {
        e.preventDefault();
        console.log("Space pressed but page didn't scroll");
    }
});

// Prevent F5 refresh
document.addEventListener("keydown", (e) => {
    if (e.key === "F5") {
        e.preventDefault();
        console.log("Refresh prevented");
    }
});
```



---

## 47.10 Key Event Example: Search Filter



```html
<input type="text" id="search" placeholder="Search items...">
<ul id="list">
    <li>Apple</li>
    <li>Banana</li>
    <li>Cherry</li>
    <li>Date</li>
    <li>Elderberry</li>
</ul>
```

```javascript
const search = document.getElementById("search");
const listItems = document.querySelectorAll("#list li");

search.addEventListener("keyup", () => {
    const searchTerm = search.value.toLowerCase();
    
    listItems.forEach(item => {
        const text = item.textContent.toLowerCase();
        
        if (text.includes(searchTerm)) {
            item.style.display = "block";
        } else {
            item.style.display = "none";
        }
    });
});
```



---

## 47.11 Complete Game Controls Example



```javascript
const player = document.getElementById("player");

let x = 100;
let y = 100;
const speed = 5;
const keys = {};

// Track which keys are pressed
document.addEventListener("keydown", (e) => {
    keys[e.key] = true;
});

document.addEventListener("keyup", (e) => {
    keys[e.key] = false;
});

// Game loop
function gameLoop() {
    // Move based on pressed keys
    if (keys["ArrowLeft"] || keys["a"]) x -= speed;
    if (keys["ArrowRight"] || keys["d"]) x += speed;
    if (keys["ArrowUp"] || keys["w"]) y -= speed;
    if (keys["ArrowDown"] || keys["s"]) y += speed;
    
    // Update position
    player.style.left = x + "px";
    player.style.top = y + "px";
    
    // Repeat
    requestAnimationFrame(gameLoop);
}

gameLoop();
```



---

## 47.12 Input Validation Example



```html
<input type="text" id="numberInput" placeholder="Numbers only">
<p id="error" style="color: red;"></p>
```

```javascript
const numberInput = document.getElementById("numberInput");
const error = document.getElementById("error");

numberInput.addEventListener("keydown", (e) => {
    // Allow: backspace, delete, tab, escape, enter
    const allowedKeys = ["Backspace", "Delete", "Tab", "Escape", "Enter", "ArrowLeft", "ArrowRight"];
    
    // Allow if special key
    if (allowedKeys.includes(e.key)) {
        error.textContent = "";
        return;
    }
    
    // Allow only numbers
    if (!/^[0-9]$/.test(e.key)) {
        e.preventDefault();
        error.textContent = "Only numbers allowed!";
    } else {
        error.textContent = "";
    }
});
```



---

## 47.13 Common Key Values



```javascript
// Letters: "a", "b", "c", ... "z" (lowercase)
// Numbers: "0", "1", "2", ... "9"
// Special:
"Enter"
"Escape"
"Backspace"
"Delete"
"Tab"
" " // Space
"ArrowUp"
"ArrowDown"
"ArrowLeft"
"ArrowRight"
"Shift"
"Control"
"Alt"
"Meta" // Command/Windows key
```

---

## Summary - Chapter 47

✅ **keydown** - Key pressed  
✅ **keyup** - Key released  
✅ **e.key** - Key value  
✅ **e.shiftKey, e.ctrlKey, e.altKey** - Modifier keys  
✅ **e.preventDefault()** - Stop default behavior  
✅ Common uses: shortcuts, game controls, validation  

---

## Practice Exercises

### Exercise 1: Keyboard Calculator
Create calculator controlled by keyboard.

### Exercise 2: Snake Game
Build snake game with arrow key controls.

### Exercise 3: Autocomplete
Implement autocomplete search with keyboard navigation.

### Exercise 4: Modal Control
Open/close modal with Escape key.

---

## Quick Reference

```javascript
// Mouse Events
element.addEventListener("click", () => {});
element.addEventListener("dblclick", () => {});
element.addEventListener("mouseenter", () => {});
element.addEventListener("mouseleave", () => {});
element.addEventListener("mousemove", (e) => {
    console.log(e.clientX, e.clientY);
});

// Keyboard Events
document.addEventListener("keydown", (e) => {
    console.log(e.key);
    
    if (e.key === "Enter") {}
    if (e.ctrlKey && e.key === "s") {
        e.preventDefault();
    }
});

document.addEventListener("keyup", (e) => {
    console.log("Released:", e.key);
});

// Event Object Properties
e.target        // Element that triggered
e.type          // Event type
e.key           // Key pressed
e.clientX       // Mouse X
e.clientY       // Mouse Y
e.shiftKey      // Shift pressed?
e.ctrlKey       // Ctrl pressed?
e.preventDefault() // Stop default
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ DOM Navigation & Manipulation](Chapters-44-45-DOM-Navigation-and-Manipulation.md) | [📑 Index](../README.md) | [Show/Hide & NodeLists ▶️](Chapters-48-49-Show-Hide-and-NodeLists.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-46--47-mouse-events--key-events)**

Made with ❤️ for JavaScript learners

</div>
