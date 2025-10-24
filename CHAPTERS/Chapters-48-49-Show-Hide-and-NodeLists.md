# Chapters 48 & 49: Show/Hide Elements + NodeLists

---

# Chapter 48: Show/Hide HTML Elements

## Overview
Learn different techniques to show and hide HTML elements dynamically.

**Timestamp:** [09:24:54]

---

## 48.1 Display Property

**Timestamp:** [09:25:01]

The `display` CSS property controls element visibility:

```javascript
element.style.display = "none";  // Hide
element.style.display = "block"; // Show (block element)
element.style.display = "inline"; // Show (inline element)
element.style.display = "flex"; // Show (flex container)
```

**Timestamp:** [09:25:30]

---

## 48.2 Hide Element with display: none

**Timestamp:** [09:26:00]

```html
<button id="hideBtn">Hide Box</button>
<div id="box" style="width: 200px; height: 200px; background: lightblue;">
    Box Content
</div>
```

```javascript
const hideBtn = document.getElementById("hideBtn");
const box = document.getElementById("box");

hideBtn.addEventListener("click", () => {
    box.style.display = "none";
});
```

**Effect:** Element disappears and doesn't take up space.

**Timestamp:** [09:26:50]

---

## 48.3 Show Element

**Timestamp:** [09:27:20]

```javascript
const showBtn = document.getElementById("showBtn");

showBtn.addEventListener("click", () => {
    box.style.display = "block"; // or "inline", "flex", etc.
});
```

---

## 48.4 Toggle Visibility

**Timestamp:** [09:28:00]

```html
<button id="toggleBtn">Toggle Box</button>
<div id="box">Box Content</div>
```

```javascript
const toggleBtn = document.getElementById("toggleBtn");
const box = document.getElementById("box");

toggleBtn.addEventListener("click", () => {
    if (box.style.display === "none") {
        box.style.display = "block";
    } else {
        box.style.display = "none";
    }
});
```

### Better Toggle

```javascript
toggleBtn.addEventListener("click", () => {
    box.style.display = box.style.display === "none" ? "block" : "none";
});
```

**Timestamp:** [09:29:10]

---

## 48.5 Visibility Property

**Timestamp:** [09:29:40]

Alternative to `display`:

```javascript
// Hide but keep space
element.style.visibility = "hidden";

// Show
element.style.visibility = "visible";
```

**Difference:**
- `display: none` - Element removed from flow, no space
- `visibility: hidden` - Element invisible, **still takes up space**

### Example

```html
<div style="visibility: hidden;">Hidden but takes space</div>
<div>This is below</div>
```

**Timestamp:** [09:30:50]

---

## 48.6 Opacity Property

**Timestamp:** [09:31:20]

Make element transparent:

```javascript
// Invisible (0 = transparent, 1 = opaque)
element.style.opacity = "0";

// Half transparent
element.style.opacity = "0.5";

// Fully visible
element.style.opacity = "1";
```

**Still takes up space and can receive events!**

---

## 48.7 Comparison of Methods

**Timestamp:** [09:32:10]

| Method | Visible? | Takes Space? | Receives Events? |
|--------|----------|--------------|------------------|
| `display: none` | ❌ No | ❌ No | ❌ No |
| `visibility: hidden` | ❌ No | ✅ Yes | ❌ No |
| `opacity: 0` | ❌ No | ✅ Yes | ✅ Yes |

---

## 48.8 Practical Example: Dropdown Menu

**Timestamp:** [09:33:00]

```html
<button id="menuBtn">Menu</button>
<div id="dropdown" style="display: none;">
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
</div>
```

```javascript
const menuBtn = document.getElementById("menuBtn");
const dropdown = document.getElementById("dropdown");

menuBtn.addEventListener("click", () => {
    if (dropdown.style.display === "none") {
        dropdown.style.display = "block";
    } else {
        dropdown.style.display = "none";
    }
});
```

**Timestamp:** [09:34:20]

---

## 48.9 Modal Example

**Timestamp:** [09:34:50]

```html
<style>
    .modal {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
    }
    
    .modal-content {
        background: white;
        width: 400px;
        margin: 100px auto;
        padding: 20px;
        border-radius: 10px;
    }
</style>

<button id="openModal">Open Modal</button>

<div id="modal" class="modal">
    <div class="modal-content">
        <h2>Modal Title</h2>
        <p>Modal content here</p>
        <button id="closeModal">Close</button>
    </div>
</div>
```

```javascript
const openModal = document.getElementById("openModal");
const closeModal = document.getElementById("closeModal");
const modal = document.getElementById("modal");

openModal.addEventListener("click", () => {
    modal.style.display = "block";
});

closeModal.addEventListener("click", () => {
    modal.style.display = "none";
});

// Close when clicking outside
modal.addEventListener("click", (e) => {
    if (e.target === modal) {
        modal.style.display = "none";
    }
});
```

**Timestamp:** [09:37:00]

---

## 48.10 Accordion Example

**Timestamp:** [09:37:30]

```html
<div class="accordion">
    <button class="accordion-btn">Section 1</button>
    <div class="accordion-content" style="display: none;">
        <p>Content for section 1</p>
    </div>
    
    <button class="accordion-btn">Section 2</button>
    <div class="accordion-content" style="display: none;">
        <p>Content for section 2</p>
    </div>
    
    <button class="accordion-btn">Section 3</button>
    <div class="accordion-content" style="display: none;">
        <p>Content for section 3</p>
    </div>
</div>
```

```javascript
const accordionBtns = document.querySelectorAll(".accordion-btn");

accordionBtns.forEach(btn => {
    btn.addEventListener("click", () => {
        // Get next element (the content)
        const content = btn.nextElementSibling;
        
        // Toggle visibility
        if (content.style.display === "block") {
            content.style.display = "none";
        } else {
            content.style.display = "block";
        }
    });
});
```

**Timestamp:** [09:39:20]

---

## 48.11 Fade Effect with Opacity

**Timestamp:** [09:39:50]

```html
<button id="fadeBtn">Fade Out</button>
<div id="box" style="opacity: 1; transition: opacity 0.5s;">
    Fading Box
</div>
```

```javascript
const fadeBtn = document.getElementById("fadeBtn");
const box = document.getElementById("box");

fadeBtn.addEventListener("click", () => {
    if (box.style.opacity === "0") {
        box.style.opacity = "1";
        fadeBtn.textContent = "Fade Out";
    } else {
        box.style.opacity = "0";
        fadeBtn.textContent = "Fade In";
    }
});
```

**Timestamp:** [09:41:00]

---

## Summary - Chapter 48

✅ **display: none** - Hide completely, no space  
✅ **visibility: hidden** - Hide but keep space  
✅ **opacity: 0** - Transparent but keep space  
✅ Toggle with if statement or ternary  
✅ Common uses: modals, dropdowns, accordions  
✅ Combine with CSS transitions for smooth effects  

---

# Chapter 49: NodeLists

## Overview
Understand NodeLists, how they differ from arrays, and how to work with them.

**Timestamp:** [09:41:32]

---

## 49.1 What is a NodeList?

**Timestamp:** [09:41:39]

**NodeList:**
- Collection of DOM nodes
- Returned by `querySelectorAll()`
- **Array-like** but not a true array
- Has `.length` property
- Can use `forEach()` (in modern browsers)

```javascript
const items = document.querySelectorAll("li");
console.log(items); // NodeList [li, li, li]
console.log(items.length); // 3
```

**Timestamp:** [09:42:30]

---

## 49.2 NodeList vs HTMLCollection

**Timestamp:** [09:43:00]

| Feature | NodeList | HTMLCollection |
|---------|----------|----------------|
| Returned by | `querySelectorAll()` | `getElementsByClassName()`, `getElementsByTagName()` |
| Static/Live | Static | Live |
| forEach() | ✅ Yes | ❌ No |
| Can contain | Any node type | Only elements |

### Example

```javascript
// NodeList (static)
const nodeList = document.querySelectorAll(".item");

// HTMLCollection (live)
const htmlCollection = document.getElementsByClassName("item");
```

**Timestamp:** [09:44:20]

---

## 49.3 Looping Through NodeList

**Timestamp:** [09:44:50]

### Method 1: forEach()

```javascript
const items = document.querySelectorAll("li");

items.forEach(item => {
    console.log(item.textContent);
});
```

✅ **Most common and recommended**

### Method 2: for loop

```javascript
for (let i = 0; i < items.length; i++) {
    console.log(items[i].textContent);
}
```

### Method 3: for...of loop

```javascript
for (let item of items) {
    console.log(item.textContent);
}
```

**Timestamp:** [09:46:00]

---

## 49.4 NodeList Doesn't Have Array Methods

**Timestamp:** [09:46:30]

```javascript
const items = document.querySelectorAll("li");

// ❌ These DON'T work on NodeList:
items.map(item => item.textContent);      // ERROR
items.filter(item => item.className);     // ERROR
items.reduce((acc, item) => acc + 1, 0);  // ERROR
```

**Solution:** Convert to array first!

**Timestamp:** [09:47:20]

---

## 49.5 Converting NodeList to Array

**Timestamp:** [09:47:50]

### Method 1: Array.from()

```javascript
const items = document.querySelectorAll("li");
const itemsArray = Array.from(items);

// Now you can use array methods
const texts = itemsArray.map(item => item.textContent);
```

### Method 2: Spread Operator

```javascript
const itemsArray = [...items];

const texts = itemsArray.map(item => item.textContent);
```

### Method 3: Array.prototype.slice.call()

```javascript
const itemsArray = Array.prototype.slice.call(items);
```

**Timestamp:** [09:49:10]

---

## 49.6 Practical Example: Using Array Methods

**Timestamp:** [09:49:40]

```html
<ul>
    <li class="active">Item 1</li>
    <li>Item 2</li>
    <li class="active">Item 3</li>
    <li>Item 4</li>
</ul>
```

```javascript
const items = document.querySelectorAll("li");
const itemsArray = Array.from(items);

// Filter active items
const activeItems = itemsArray.filter(item => {
    return item.classList.contains("active");
});

console.log(activeItems); // [li.active, li.active]

// Get text of all items
const texts = itemsArray.map(item => item.textContent);
console.log(texts); // ["Item 1", "Item 2", "Item 3", "Item 4"]

// Count items
const count = itemsArray.reduce((acc) => acc + 1, 0);
console.log(count); // 4
```

**Timestamp:** [09:51:20]

---

## 49.7 Static vs Live Collections

**Timestamp:** [09:51:50]

### NodeList (Static)

```html
<div class="box">Box 1</div>
<div class="box">Box 2</div>
```

```javascript
const boxes = document.querySelectorAll(".box");
console.log(boxes.length); // 2

// Add new box
const newBox = document.createElement("div");
newBox.className = "box";
document.body.appendChild(newBox);

console.log(boxes.length); // Still 2 (not updated)
```

### HTMLCollection (Live)

```javascript
const boxes = document.getElementsByClassName("box");
console.log(boxes.length); // 2

// Add new box
const newBox = document.createElement("div");
newBox.className = "box";
document.body.appendChild(newBox);

console.log(boxes.length); // 3 (automatically updated!)
```

**Timestamp:** [09:53:30]

---

## 49.8 Modifying Elements in NodeList

**Timestamp:** [09:54:00]

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

### Change All Elements

```javascript
const items = document.querySelectorAll("li");

items.forEach(item => {
    item.style.color = "red";
    item.style.fontWeight = "bold";
});
```

### Change by Index

```javascript
items[0].textContent = "First Item";
items[1].textContent = "Second Item";
items[2].textContent = "Third Item";
```

**Timestamp:** [09:55:20]

---

## 49.9 Adding Event Listeners to NodeList

**Timestamp:** [09:55:50]

```html
<button class="btn">Button 1</button>
<button class="btn">Button 2</button>
<button class="btn">Button 3</button>
```

```javascript
const buttons = document.querySelectorAll(".btn");

buttons.forEach(button => {
    button.addEventListener("click", () => {
        console.log(button.textContent);
    });
});
```

### Better: Event Delegation

```javascript
document.addEventListener("click", (e) => {
    if (e.target.classList.contains("btn")) {
        console.log(e.target.textContent);
    }
});
```

**Timestamp:** [09:57:10]

---

## 49.10 Practical Example: Checkbox Selection

**Timestamp:** [09:57:40]

```html
<input type="checkbox" class="item-check" value="1"> Item 1<br>
<input type="checkbox" class="item-check" value="2"> Item 2<br>
<input type="checkbox" class="item-check" value="3"> Item 3<br>
<button id="getSelected">Get Selected</button>
<p id="result"></p>
```

```javascript
const getSelected = document.getElementById("getSelected");
const result = document.getElementById("result");

getSelected.addEventListener("click", () => {
    const checkboxes = document.querySelectorAll(".item-check");
    const checkboxArray = Array.from(checkboxes);
    
    // Filter checked boxes
    const selected = checkboxArray
        .filter(cb => cb.checked)
        .map(cb => cb.value);
    
    result.textContent = `Selected: ${selected.join(", ")}`;
});
```

**Timestamp:** [09:59:30]

---

## 49.11 Complete Example: List Manager

**Timestamp:** [10:00:00]

```html
<button id="selectAll">Select All</button>
<button id="deselectAll">Deselect All</button>
<button id="deleteSelected">Delete Selected</button>

<ul id="list">
    <li><input type="checkbox"> Item 1</li>
    <li><input type="checkbox"> Item 2</li>
    <li><input type="checkbox"> Item 3</li>
    <li><input type="checkbox"> Item 4</li>
</ul>
```

```javascript
const selectAll = document.getElementById("selectAll");
const deselectAll = document.getElementById("deselectAll");
const deleteSelected = document.getElementById("deleteSelected");

selectAll.addEventListener("click", () => {
    const checkboxes = document.querySelectorAll("#list input[type='checkbox']");
    checkboxes.forEach(cb => cb.checked = true);
});

deselectAll.addEventListener("click", () => {
    const checkboxes = document.querySelectorAll("#list input[type='checkbox']");
    checkboxes.forEach(cb => cb.checked = false);
});

deleteSelected.addEventListener("click", () => {
    const listItems = document.querySelectorAll("#list li");
    
    listItems.forEach(li => {
        const checkbox = li.querySelector("input[type='checkbox']");
        if (checkbox.checked) {
            li.remove();
        }
    });
});
```

**Timestamp:** [10:02:30]

---

## 49.12 Common NodeList Operations

**Timestamp:** [10:03:00]

```javascript
const items = document.querySelectorAll("li");

// Get count
console.log(items.length);

// Access by index
console.log(items[0]);
console.log(items[items.length - 1]);

// Check if empty
if (items.length === 0) {
    console.log("No items found");
}

// Loop
items.forEach((item, index) => {
    console.log(`Item ${index}: ${item.textContent}`);
});

// Convert to array
const array = Array.from(items);
const array2 = [...items];

// Use array methods
const texts = Array.from(items).map(item => item.textContent);
```

---

## Summary - Chapter 49

✅ **NodeList** - Collection of nodes  
✅ Returned by `querySelectorAll()`  
✅ Array-like but not true array  
✅ Has `forEach()` method  
✅ **Static** (doesn't auto-update)  
✅ Convert to array with `Array.from()` or `[...]`  
✅ Use array methods after conversion  

---

## Practice Exercises

### Exercise 1: Bulk Actions
Create interface to select and delete multiple items.

### Exercise 2: Filter List
Implement search filter for list items.

### Exercise 3: Sort List
Sort list items by text content.

### Exercise 4: Move Items
Move selected items between two lists.

---

## Quick Reference

```javascript
// Show/Hide Elements

// Display
element.style.display = "none";  // Hide
element.style.display = "block"; // Show

// Visibility
element.style.visibility = "hidden"; // Hide, keep space
element.style.visibility = "visible"; // Show

// Opacity
element.style.opacity = "0"; // Transparent
element.style.opacity = "1"; // Opaque

// Toggle
element.style.display = element.style.display === "none" ? "block" : "none";

// NodeLists

// Get NodeList
const items = document.querySelectorAll("li");

// Loop through
items.forEach(item => {
    console.log(item);
});

// Convert to array
const array = Array.from(items);
const array2 = [...items];

// Use array methods
const texts = Array.from(items).map(item => item.textContent);
const filtered = Array.from(items).filter(item => item.classList.contains("active"));

// Access by index
items[0] // First item
items[items.length - 1] // Last item

// Check length
if (items.length === 0) {
    console.log("Empty");
}
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Mouse & Key Events](Chapters-46-47-Mouse-and-Key-Events.md) | [📑 Index](../README.md) | [ClassList & Rock Paper Scissors ▶️](Chapters-50-51-ClassList-and-Rock-Paper-Scissors.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-48--49-showhide-elements--nodelists)**

Made with ❤️ for JavaScript learners

</div>
