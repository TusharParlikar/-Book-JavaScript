# Chapters 44 & 45: DOM Navigation + Adding/Changing HTML

---

# Chapter 44: DOM Navigation

## Overview
Learn how to navigate through the DOM tree using parent, child, and sibling relationships.



---

## 44.1 DOM Tree Relationships



```html
<div id="parent">
    <h1 id="first">Title</h1>
    <p id="second">Paragraph</p>
    <span id="third">Span</span>
</div>
```

**Relationships:**
- `parent` is the **parent** of `first`, `second`, `third`
- `first`, `second`, `third` are **children** of `parent`
- `first`, `second`, `third` are **siblings** to each other
- `first` is the **first child**
- `third` is the **last child**

---

## 44.2 Accessing Parent Element



### parentElement

```html
<div id="parent">
    <p id="child">Text</p>
</div>
```

```javascript
const child = document.getElementById("child");

console.log(child.parentElement); 
// Output: <div id="parent">...</div>

// Can chain
const grandparent = child.parentElement.parentElement;
```

### parentNode

```javascript
console.log(child.parentNode); 
// Output: Same as parentElement (usually)
```

**Difference:** `parentNode` can return any node type, `parentElement` only returns element nodes.



---

## 44.3 Accessing Children



```html
<ul id="list">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

### children

```javascript
const list = document.getElementById("list");

console.log(list.children); // HTMLCollection [li, li, li]
console.log(list.children[0]); // First <li>
console.log(list.children.length); // 3
```

### firstElementChild / lastElementChild

```javascript
console.log(list.firstElementChild); 
// Output: First <li>
console.log(list.lastElementChild); 
// Output: Last <li>
```



---

## 44.4 childNodes vs children



```html
<div id="container">
    <p>Paragraph</p>
    <span>Span</span>
</div>
```

### childNodes (includes text nodes)

```javascript
const container = document.getElementById("container");

console.log(container.childNodes);
// NodeList [text, p, text, span, text]
// Includes whitespace text nodes!
```

### children (elements only)

```javascript
console.log(container.children);
// HTMLCollection [p, span]
// Only element nodes
```

✅ **Use `children` for elements only**



---

## 44.5 Accessing Siblings



```html
<div>
    <h1 id="title">Title</h1>
    <p id="para">Paragraph</p>
    <span id="span">Span</span>
</div>
```

### nextElementSibling

```javascript
const para = document.getElementById("para");

console.log(para.nextElementSibling); // <span id="span">
```

### previousElementSibling

```javascript
console.log(para.previousElementSibling); // <h1 id="title">
```



---

## 44.6 Practical Navigation Example



```html
<div class="container">
    <div class="card">
        <h2>Card 1</h2>
        <p>Content 1</p>
        <button class="btn">Delete</button>
    </div>
    <div class="card">
        <h2>Card 2</h2>
        <p>Content 2</p>
        <button class="btn">Delete</button>
    </div>
</div>
```

```javascript
const buttons = document.querySelectorAll(".btn");

buttons.forEach(button => {
    button.addEventListener("click", (e) => {
        // Navigate to parent card and remove it
        const card = e.target.parentElement;
        card.remove();
    });
});
```



---

## 44.7 Traversing Up the Tree



```html
<div class="grandparent">
    <div class="parent">
        <button id="btn">Click</button>
    </div>
</div>
```

```javascript
const btn = document.getElementById("btn");

// Go up one level
const parent = btn.parentElement;
console.log(parent.className); // "parent"

// Go up two levels
const grandparent = btn.parentElement.parentElement;
console.log(grandparent.className); // "grandparent"

// Find closest ancestor matching selector
const closestParent = btn.closest(".parent");
const closestGrandparent = btn.closest(".grandparent");
```



---

## 44.8 closest() Method



Find the nearest ancestor matching a selector:

```html
<div class="container">
    <div class="box">
        <p>
            <span id="text">Text</span>
        </p>
    </div>
</div>
```

```javascript
const text = document.getElementById("text");

// Find nearest .box ancestor
const box = text.closest(".box");

// Find nearest .container ancestor
const container = text.closest(".container");

// Returns null if not found
const notFound = text.closest(".nonexistent"); // null
```

✅ **Very useful for event delegation!**



---

## 44.9 Complete Navigation Example



```html
<ul id="list">
    <li>Item 1</li>
    <li class="active">Item 2</li>
    <li>Item 3</li>
</ul>
```

```javascript
const list = document.getElementById("list");
const activeItem = document.querySelector(".active");

// Parent
console.log(activeItem.parentElement); // <ul>

// Children of list
console.log(list.children); // [li, li, li]
console.log(list.firstElementChild); // First <li>
console.log(list.lastElementChild); // Last <li>

// Siblings
console.log(activeItem.previousElementSibling); // <li>Item 1</li>
console.log(activeItem.nextElementSibling); // <li>Item 3</li>

// Navigate to specific child
console.log(list.children[1]); // Second <li>
```

---

## Summary - Chapter 44

✅ **parentElement** - Access parent  
✅ **children** - Get child elements  
✅ **firstElementChild / lastElementChild** - First/last child  
✅ **nextElementSibling / previousElementSibling** - Siblings  
✅ **closest()** - Find nearest ancestor  
✅ Use **Element** versions (not Node versions)  

---

# Chapter 45: Adding & Changing HTML

## Overview
Learn how to create, add, modify, and remove HTML elements dynamically.



---

## 45.1 Creating Elements



### createElement()

```javascript
// Create new element
const newDiv = document.createElement("div");
const newPara = document.createElement("p");
const newButton = document.createElement("button");

console.log(newDiv); // <div></div> (not yet in DOM)
```

**Note:** Element is created but not yet visible on page!



---

## 45.2 Adding Content to Elements



```javascript
const para = document.createElement("p");

// Method 1: textContent
para.textContent = "This is a paragraph";

// Method 2: innerHTML
para.innerHTML = "This is <strong>bold</strong> text";

// Method 3: innerText (similar to textContent)
para.innerText = "Simple text";
```

**textContent vs innerHTML:**
- `textContent`: Plain text only, faster, safer
- `innerHTML`: Can include HTML tags



---

## 45.3 Adding Attributes



```javascript
const link = document.createElement("a");

// Method 1: Direct property
link.href = "https://example.com";
link.target = "_blank";

// Method 2: setAttribute()
link.setAttribute("href", "https://example.com");
link.setAttribute("target", "_blank");

// Add class
link.className = "btn btn-primary";

// Add ID
link.id = "myLink";

// Add text
link.textContent = "Click here";
```



---

## 45.4 Appending Elements to DOM



### appendChild()

```javascript
const para = document.createElement("p");
para.textContent = "New paragraph";

// Append to body
document.body.appendChild(para);

// Append to specific element
const container = document.getElementById("container");
container.appendChild(para);
```



---

## 45.5 append() vs appendChild()



### appendChild()
- Appends **single element node**
- Returns appended element
- Older method

```javascript
const div = document.createElement("div");
document.body.appendChild(div);
```

### append()
- Can append **multiple items**
- Can append **text** directly
- Doesn't return anything
- Newer method

```javascript
const div = document.createElement("div");
const span = document.createElement("span");

// Append multiple elements
document.body.append(div, span, "Some text");
```



---

## 45.6 prepend() - Add at Beginning



```html
<ul id="list">
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

```javascript
const list = document.getElementById("list");
const newItem = document.createElement("li");
newItem.textContent = "Item 1";

// Add at the beginning
list.prepend(newItem);

// Result:
// <li>Item 1</li>
// <li>Item 2</li>
// <li>Item 3</li>
```

---

## 45.7 Inserting Elements



### insertBefore()

```html
<ul id="list">
    <li id="item1">Item 1</li>
    <li id="item3">Item 3</li>
</ul>
```

```javascript
const list = document.getElementById("list");
const item3 = document.getElementById("item3");

const newItem = document.createElement("li");
newItem.textContent = "Item 2";

// Insert before item3
list.insertBefore(newItem, item3);
```

### insertAdjacentElement()

```javascript
const reference = document.getElementById("item1");
const newItem = document.createElement("li");
newItem.textContent = "New Item";

// beforebegin: Before the element
reference.insertAdjacentElement("beforebegin", newItem);

// afterbegin: First child of element
reference.insertAdjacentElement("afterbegin", newItem);

// beforeend: Last child of element
reference.insertAdjacentElement("beforeend", newItem);

// afterend: After the element
reference.insertAdjacentElement("afterend", newItem);
```



---

## 45.8 Removing Elements



### remove()

```html
<div id="myDiv">Remove me</div>
```

```javascript
const div = document.getElementById("myDiv");
div.remove(); // Element removed from DOM
```

### removeChild()

```html
<ul id="list">
    <li id="item1">Item 1</li>
    <li id="item2">Item 2</li>
</ul>
```

```javascript
const list = document.getElementById("list");
const item1 = document.getElementById("item1");

list.removeChild(item1); // Remove item1 from list
```



---

## 45.9 Replacing Elements



### replaceWith()

```html
<p id="oldPara">Old paragraph</p>
```

```javascript
const oldPara = document.getElementById("oldPara");
const newPara = document.createElement("p");
newPara.textContent = "New paragraph";

oldPara.replaceWith(newPara);
```

### replaceChild()

```javascript
const parent = document.getElementById("parent");
const oldChild = document.getElementById("oldChild");
const newChild = document.createElement("div");

parent.replaceChild(newChild, oldChild);
```



---

## 45.10 Practical Example: To-Do List



```html
<!DOCTYPE html>
<html>
<head>
    <title>To-Do List</title>
</head>
<body>
    <input type="text" id="taskInput" placeholder="Enter task">
    <button id="addBtn">Add Task</button>
    <ul id="taskList"></ul>
    
    <script src="script.js"></script>
</body>
</html>
```

```javascript
const taskInput = document.getElementById("taskInput");
const addBtn = document.getElementById("addBtn");
const taskList = document.getElementById("taskList");

addBtn.addEventListener("click", addTask);

function addTask() {
    const taskText = taskInput.value.trim();
    
    if (taskText === "") {
        alert("Please enter a task!");
        return;
    }
    
    // Create list item
    const li = document.createElement("li");
    li.textContent = taskText;
    
    // Create delete button
    const deleteBtn = document.createElement("button");
    deleteBtn.textContent = "Delete";
    deleteBtn.style.marginLeft = "10px";
    
    // Add delete functionality
    deleteBtn.addEventListener("click", () => {
        li.remove();
    });
    
    // Append button to li
    li.appendChild(deleteBtn);
    
    // Append li to list
    taskList.appendChild(li);
    
    // Clear input
    taskInput.value = "";
}

// Allow Enter key to add task
taskInput.addEventListener("keypress", (e) => {
    if (e.key === "Enter") {
        addTask();
    }
});
```



---

## 45.11 Creating Complex Structures



```javascript
function createCard(title, content) {
    // Create card container
    const card = document.createElement("div");
    card.className = "card";
    
    // Create title
    const h2 = document.createElement("h2");
    h2.textContent = title;
    
    // Create content
    const p = document.createElement("p");
    p.textContent = content;
    
    // Create button
    const button = document.createElement("button");
    button.textContent = "Read More";
    button.className = "btn";
    
    // Assemble card
    card.appendChild(h2);
    card.appendChild(p);
    card.appendChild(button);
    
    return card;
}

// Use the function
const myCard = createCard("Card Title", "Card content goes here");
document.body.appendChild(myCard);
```



---

## 45.12 innerHTML vs createElement



### Using innerHTML (simpler but slower)

```javascript
const container = document.getElementById("container");

container.innerHTML = `
    <div class="card">
        <h2>Title</h2>
        <p>Content</p>
        <button>Click</button>
    </div>
`;
```

### Using createElement (faster, more control)

```javascript
const container = document.getElementById("container");

const card = document.createElement("div");
card.className = "card";

const h2 = document.createElement("h2");
h2.textContent = "Title";

const p = document.createElement("p");
p.textContent = "Content";

const button = document.createElement("button");
button.textContent = "Click";

card.append(h2, p, button);
container.appendChild(card);
```

**When to use:**
- `innerHTML`: Quick, simple HTML creation
- `createElement`: Better performance, more control, safer

---

## 45.13 Cloning Elements



```html
<div id="original">
    <h2>Original</h2>
    <p>Content</p>
</div>
```

```javascript
const original = document.getElementById("original");

// Shallow clone (element only, no children)
const shallowClone = original.cloneNode(false);

// Deep clone (element + all children)
const deepClone = original.cloneNode(true);

// Modify and append
deepClone.id = "clone";
deepClone.querySelector("h2").textContent = "Clone";
document.body.appendChild(deepClone);
```

---

## Summary - Chapter 45

✅ **createElement()** - Create new element  
✅ **appendChild() / append()** - Add to end  
✅ **prepend()** - Add to beginning  
✅ **insertBefore()** - Insert at position  
✅ **remove() / removeChild()** - Remove element  
✅ **replaceWith()** - Replace element  
✅ **cloneNode()** - Clone element  
✅ **textContent / innerHTML** - Add content  

---

## Practice Exercises

### Exercise 1: Dynamic Menu
Create navigation menu from array of links.

### Exercise 2: Comment System
Build comment section with add/delete functionality.

### Exercise 3: Image Gallery
Generate image grid from array of image URLs.

### Exercise 4: Shopping Cart
Create cart with add/remove item functionality.

---

## Quick Reference

```javascript
// Create element
const div = document.createElement("div");
div.textContent = "Content";
div.className = "box";
div.id = "myDiv";

// Add to DOM
document.body.appendChild(div);
document.body.append(div);
document.body.prepend(div);

// Insert
parent.insertBefore(newNode, referenceNode);
element.insertAdjacentElement("beforeend", newElement);

// Remove
element.remove();
parent.removeChild(child);

// Replace
oldElement.replaceWith(newElement);
parent.replaceChild(newChild, oldChild);

// Clone
const clone = element.cloneNode(true);

// Navigation
element.parentElement
element.children
element.firstElementChild
element.lastElementChild
element.nextElementSibling
element.previousElementSibling
element.closest(".selector")
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ DOM Introduction & Selectors](Chapters-42-43-DOM-Introduction-and-Selectors.md) | [📑 Index](../README.md) | [Mouse & Key Events ▶️](Chapters-46-47-Mouse-and-Key-Events.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-44--45-dom-navigation--addigchanging-html)**

Made with ❤️ for JavaScript learners

</div>
