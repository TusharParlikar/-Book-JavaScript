# Chapters 42 & 43: DOM Introduction + Element Selectors

---

# Chapter 42: DOM Introduction

## Overview
Learn what the Document Object Model (DOM) is and how JavaScript interacts with HTML elements.



---

## 42.1 What is the DOM?



**DOM = Document Object Model**

- Programming interface for HTML/XML documents
- Represents page structure as a tree of objects
- Allows JavaScript to:
  - Access HTML elements
  - Modify content
  - Change styles
  - Add/remove elements
  - Respond to events

---

## 42.2 DOM Tree Structure



```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    <h1>Welcome</h1>
    <p>Hello World</p>
  </body>
</html>
```

**Tree Representation:**

```
document
└── html
    ├── head
    │   └── title
    │       └── "My Page"
    └── body
        ├── h1
        │   └── "Welcome"
        └── p
            └── "Hello World"
```

Each box is a **node** (element, text, etc.)



---

## 42.3 The document Object



`document` is the entry point to the DOM:

```javascript
console.log(document); 
// Output: Entire HTML document
console.log(document.title); 
// Output: My Page
console.log(document.URL); 
// Output: https://example.com/
console.log(document.domain); 
// Output: example.com
```

### Common document Properties

```javascript
document.head       // <head> element
document.body       // <body> element
document.forms      // All <form> elements
document.links      // All <a> elements with href
document.images     // All <img> elements
document.scripts    // All <script> elements
```



---

## 42.4 Node Types



The DOM has different node types:

| Node Type | Description | Example |
|-----------|-------------|---------|
| Element Node | HTML tags | `<div>`, `<p>`, `<h1>` |
| Text Node | Text content | "Hello World" |
| Attribute Node | Element attributes | `class="box"` |
| Comment Node | HTML comments | `<!-- comment -->` |

---

## 42.5 Accessing Elements



Multiple ways to select elements:

```javascript
// By ID
document.getElementById("myId");

// By class name
document.getElementsByClassName("myClass");

// By tag name
document.getElementsByTagName("div");

// By CSS selector (modern)
document.querySelector(".myClass");
document.querySelectorAll("div.box");
```

We'll explore these in detail in the next chapter!

---

## 42.6 Modifying Content



### textContent

```html
<h1 id="title">Hello</h1>
```

```javascript
const title = document.getElementById("title");

console.log(title.textContent); // "Hello"

title.textContent = "Welcome!"; // Changes text
```

### innerHTML

```html
<div id="container">
    <p>Original</p>
</div>
```

```javascript
const container = document.getElementById("container");

// Get HTML content
console.log(container.innerHTML); // "<p>Original</p>"

// Set HTML content
container.innerHTML = "<p>New <strong>content</strong></p>";
```



---

## 42.7 Modifying Attributes



```html
<img id="myImage" src="old.jpg" alt="Old Image">
```

```javascript
const img = document.getElementById("myImage");

// Get attribute
console.log(img.src); // "old.jpg"
console.log(img.alt); // "Old Image"

// Set attribute
img.src = "new.jpg";
img.alt = "New Image";

// Alternative method
img.setAttribute("src", "new.jpg");
img.getAttribute("src"); // "new.jpg"
```

---

## 42.8 Modifying Styles



```html
<div id="box">Content</div>
```

```javascript
const box = document.getElementById("box");

// Modify inline styles
box.style.color = "blue";
box.style.backgroundColor = "yellow";
box.style.fontSize = "20px";
box.style.border = "2px solid black";
box.style.padding = "10px";

// Note: CSS property names become camelCase
// background-color → backgroundColor
// font-size → fontSize
```



---

## 42.9 Adding/Removing Classes



```html
<style>
    .highlight {
        background-color: yellow;
    }
    .large {
        font-size: 24px;
    }
</style>

<p id="text">Hello</p>
```

```javascript
const text = document.getElementById("text");

// Add class
text.classList.add("highlight");

// Remove class
text.classList.remove("highlight");

// Toggle class
text.classList.toggle("highlight");

// Check if has class
if (text.classList.contains("highlight")) {
    console.log("Element is highlighted");
}

// Add multiple classes
text.classList.add("highlight", "large");
```



---

## 42.10 Simple DOM Example



```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM Example</title>
    <style>
        .highlight {
            background-color: yellow;
            padding: 10px;
        }
    </style>
</head>
<body>
    <h1 id="title">Original Title</h1>
    <button id="changeBtn">Change Title</button>
    <button id="styleBtn">Add Style</button>
    
    <script>
        const title = document.getElementById("title");
        const changeBtn = document.getElementById("changeBtn");
        const styleBtn = document.getElementById("styleBtn");
        
        changeBtn.addEventListener("click", () => {
            title.textContent = "New Title!";
        });
        
        styleBtn.addEventListener("click", () => {
            title.classList.toggle("highlight");
        });
    </script>
</body>
</html>
```



---

## Summary - Chapter 42

✅ DOM = Document Object Model  
✅ Represents HTML as tree of nodes  
✅ `document` object provides access  
✅ Can select, modify, style elements  
✅ `textContent` for text, `innerHTML` for HTML  
✅ `style` for inline CSS  
✅ `classList` for CSS classes  

---

# Chapter 43: Element Selectors

## Overview
Learn different methods to select HTML elements from the DOM.



---

## 43.1 getElementById()



Select element by its `id` attribute:

```html
<div id="myDiv">Content</div>
```

```javascript
const element = document.getElementById("myDiv");

console.log(element); // <div id="myDiv">Content</div>
console.log(element.textContent); // "Content"
```

✅ **Fast and efficient**  
✅ Returns **single element** (or `null`)  
❌ Only works with ID (must be unique)



---

## 43.2 getElementsByClassName()



Select elements by class name:

```html
<div class="box">Box 1</div>
<div class="box">Box 2</div>
<div class="box">Box 3</div>
```

```javascript
const boxes = document.getElementsByClassName("box");

console.log(boxes); // HTMLCollection [div.box, div.box, div.box]
console.log(boxes.length); // 3
console.log(boxes[0]); // First box
console.log(boxes[1]); // Second box
```

✅ Returns **HTMLCollection** (array-like)  
✅ Live collection (updates automatically)  
❌ Not a real array (limited methods)



---

## 43.3 Looping Through HTMLCollection



```javascript
const boxes = document.getElementsByClassName("box");

// Method 1: for loop
for (let i = 0; i < boxes.length; i++) {
    boxes[i].style.backgroundColor = "lightblue";
}

// Method 2: for...of loop
for (let box of boxes) {
    box.style.color = "red";
}

// Convert to array for array methods
const boxesArray = Array.from(boxes);
boxesArray.forEach(box => {
    box.textContent = "Modified";
});
```



---

## 43.4 getElementsByTagName()



Select elements by tag name:

```html
<p>Paragraph 1</p>
<p>Paragraph 2</p>
<p>Paragraph 3</p>
```

```javascript
const paragraphs = document.getElementsByTagName("p");

console.log(paragraphs); // HTMLCollection [p, p, p]
console.log(paragraphs.length); // 3

// Modify all paragraphs
for (let p of paragraphs) {
    p.style.color = "blue";
}
```

### Select All Elements

```javascript
const allElements = document.getElementsByTagName("*");
console.log(allElements.length); // Number of all elements
```



---

## 43.5 querySelector()



Select **first** element matching CSS selector:

```html
<div class="container">
    <p class="text">First</p>
    <p class="text">Second</p>
</div>
```

```javascript
// By class
const firstText = document.querySelector(".text");
console.log(firstText.textContent); // "First"

// By ID
const container = document.querySelector("#myId");

// By tag
const paragraph = document.querySelector("p");

// Complex selectors
const nestedElement = document.querySelector(".container .text");
const firstChild = document.querySelector("div > p:first-child");
```

✅ **Most flexible** (any CSS selector)  
✅ Returns **single element** (first match)  
✅ Returns `null` if not found



---

## 43.6 querySelectorAll()



Select **all** elements matching CSS selector:

```html
<div class="box">Box 1</div>
<div class="box">Box 2</div>
<div class="box">Box 3</div>
```

```javascript
const boxes = document.querySelectorAll(".box");

console.log(boxes); // NodeList [div.box, div.box, div.box]
console.log(boxes.length); // 3

// Loop through NodeList
boxes.forEach(box => {
    box.style.backgroundColor = "lightgreen";
});
```

✅ Returns **NodeList** (array-like)  
✅ Can use `forEach` directly  
✅ Any CSS selector works  
❌ Static collection (doesn't auto-update)



---

## 43.7 Complex Selectors



```html
<div class="container">
    <p class="text highlight">Paragraph 1</p>
    <p class="text">Paragraph 2</p>
    <div>
        <p class="text">Nested paragraph</p>
    </div>
</div>
```

```javascript
// Multiple classes
const highlighted = document.querySelector(".text.highlight");

// Descendant selector (any level)
const allTexts = document.querySelectorAll(".container .text");

// Child selector (direct children only)
const directChildren = document.querySelectorAll(".container > p");

// Attribute selector
const links = document.querySelectorAll('a[href^="https"]');

// Pseudo-class
const firstItem = document.querySelector("li:first-child");
const lastItem = document.querySelector("li:last-child");
const evenItems = document.querySelectorAll("li:nth-child(even)");
```



---

## 43.8 Comparison of Methods



| Method | Returns | Live? | Selector |
|--------|---------|-------|----------|
| `getElementById` | Element or null | N/A | ID only |
| `getElementsByClassName` | HTMLCollection | Yes | Class only |
| `getElementsByTagName` | HTMLCollection | Yes | Tag only |
| `querySelector` | Element or null | N/A | Any CSS |
| `querySelectorAll` | NodeList | No | Any CSS |



---

## 43.9 Live vs Static Collections



### Live Collection (getElementsByClassName)

```html
<div class="box">Box 1</div>
<div class="box">Box 2</div>
```

```javascript
const boxes = document.getElementsByClassName("box");
console.log(boxes.length); // 2

// Add new element
const newBox = document.createElement("div");
newBox.className = "box";
document.body.appendChild(newBox);

console.log(boxes.length); // 3 (automatically updated!)
```

### Static Collection (querySelectorAll)

```javascript
const boxes = document.querySelectorAll(".box");
console.log(boxes.length); // 2

// Add new element
const newBox = document.createElement("div");
newBox.className = "box";
document.body.appendChild(newBox);

console.log(boxes.length); // Still 2 (not updated)
```



---

## 43.10 Practical Examples



### Example 1: Change All Button Colors

```html
<button class="btn">Button 1</button>
<button class="btn">Button 2</button>
<button class="btn">Button 3</button>
```

```javascript
const buttons = document.querySelectorAll(".btn");

buttons.forEach(button => {
    button.style.backgroundColor = "blue";
    button.style.color = "white";
    button.style.padding = "10px 20px";
    button.style.border = "none";
    button.style.borderRadius = "5px";
});
```

### Example 2: Toggle Visibility

```html
<button id="toggleBtn">Toggle</button>
<div class="content">Content to toggle</div>
```

```javascript
const toggleBtn = document.getElementById("toggleBtn");
const content = document.querySelector(".content");

toggleBtn.addEventListener("click", () => {
    if (content.style.display === "none") {
        content.style.display = "block";
    } else {
        content.style.display = "none";
    }
});
```

### Example 3: Highlight Active Item

```html
<ul>
    <li class="item">Item 1</li>
    <li class="item">Item 2</li>
    <li class="item">Item 3</li>
</ul>
```

```javascript
const items = document.querySelectorAll(".item");

items.forEach(item => {
    item.addEventListener("click", () => {
        // Remove active class from all
        items.forEach(i => i.classList.remove("active"));
        
        // Add active class to clicked item
        item.classList.add("active");
    });
});
```



---

## 43.11 When to Use Which?



### Use getElementById()
- ✅ Single element with ID
- ✅ Need best performance

### Use getElementsByClassName()
- ✅ Multiple elements by class
- ✅ Need live collection

### Use getElementsByTagName()
- ✅ Select all of specific tag
- ✅ Need live collection

### Use querySelector()
- ✅ Complex CSS selector
- ✅ Need first match only
- ✅ Modern syntax preference

### Use querySelectorAll()
- ✅ Complex CSS selector
- ✅ Need all matches
- ✅ Want to use forEach
- ✅ **Most commonly used today**

---

## 43.12 Performance Considerations



**Fastest to Slowest:**

1. `getElementById()` - O(1)
2. `getElementsByClassName()` / `getElementsByTagName()` - Fast
3. `querySelector()` - Slower
4. `querySelectorAll()` - Slowest

**Recommendation:** Use `querySelector/querySelectorAll` unless performance is critical.

---

## Summary - Chapter 43

✅ **getElementById()** - Single element by ID  
✅ **getElementsByClassName()** - Multiple by class (live)  
✅ **getElementsByTagName()** - Multiple by tag (live)  
✅ **querySelector()** - First match, any CSS selector  
✅ **querySelectorAll()** - All matches, any CSS selector  
✅ querySelector methods are most flexible  
✅ HTMLCollection vs NodeList differences  

---

## Practice Exercises

### Exercise 1: Color Changer
Select all paragraphs and change their color on button click.

### Exercise 2: List Filter
Filter list items based on search input.

### Exercise 3: Tab Navigation
Create tabbed interface with active state.

### Exercise 4: Image Gallery
Select and display images dynamically.

---

## Quick Reference

```javascript
// Select single element
document.getElementById("myId");
document.querySelector(".myClass");
document.querySelector("#myId");

// Select multiple elements
document.getElementsByClassName("myClass");
document.getElementsByTagName("div");
document.querySelectorAll(".myClass");
document.querySelectorAll("div");

// Complex selectors
document.querySelector(".parent .child");
document.querySelectorAll("div > p");
document.querySelectorAll("[data-id]");
document.querySelectorAll("li:first-child");

// Loop through elements
const elements = document.querySelectorAll(".item");
elements.forEach(el => {
    el.style.color = "red";
});

// Convert HTMLCollection to Array
const collection = document.getElementsByClassName("box");
const array = Array.from(collection);
array.forEach(el => { /* ... */ });
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Error Handling & Calculator](Chapters-40-41-Error-Handling-and-Calculator.md) | [📑 Index](../README.md) | [DOM Navigation & Manipulation ▶️](Chapters-44-45-DOM-Navigation-and-Manipulation.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-42--43-dom-introduction--element-selectors)**

Made with ❤️ for JavaScript learners

</div>
