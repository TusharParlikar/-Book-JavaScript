# Chapters 32 & 33: Shuffling Arrays + Date Objects

---

# Chapter 32: Shuffling Arrays

## Overview
Learn how to properly randomize the order of elements in an array using the Fisher-Yates shuffle algorithm.



---

## 32.1 What is Array Shuffling?



**Shuffling** = Randomizing the order of elements in an array

Common uses:
- Card games
- Random quiz questions
- Playlist randomization
- Random selection pools

---

## 32.2 Incorrect Method (Don't Use This!)



```javascript
let cards = ["A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"];

// ❌ This is NOT truly random!
cards.sort(() => Math.random() - 0.5);
```

**Why it's wrong:**
- Not uniformly random
- Biased results
- Inefficient
- Inconsistent across browsers

---

## 32.3 Correct Method: Fisher-Yates Shuffle



Also known as the **Knuth Shuffle**, this is the proper algorithm:

```javascript
function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const random = Math.floor(Math.random() * (i + 1));
        [array[i], array[random]] = [array[random], array[i]];
    }
}
```

, [06:37:37]

---

## 32.4 Step-by-Step Explanation

### Step 1: Iterate Backwards



```javascript
for (let i = array.length - 1; i > 0; i--) {
    // Start from last element, go to second element
}
```

Start from the end and work backwards to the second element.

### Step 2: Pick Random Index



```javascript
const random = Math.floor(Math.random() * (i + 1));
```

For current position `i`, pick a random index from `0` to `i` (inclusive).

### Step 3: Swap Elements



```javascript
[array[i], array[random]] = [array[random], array[i]];
```

Swap the element at position `i` with the element at the random position.

---

## 32.5 Complete Shuffle Example



```javascript
// Fisher-Yates Shuffle Function
function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const random = Math.floor(Math.random() * (i + 1));
        [array[i], array[random]] = [array[random], array[i]];
    }
}

// Example: Shuffle deck of cards
let cards = ["A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"];

console.log("Before shuffle:", cards);
shuffle(cards);
console.log("After shuffle:", cards);

// Each run produces different random order
shuffle(cards);
console.log("After second shuffle:", cards);
```

---

## 32.6 Non-Mutating Shuffle

If you want to keep the original array unchanged:

```javascript
function shuffleCopy(array) {
    const copy = [...array]; // Create copy
    for (let i = copy.length - 1; i > 0; i--) {
        const random = Math.floor(Math.random() * (i + 1));
        [copy[i], copy[random]] = [copy[random], copy[i]];
    }
    return copy;
}

const original = [1, 2, 3, 4, 5];
const shuffled = shuffleCopy(original);

console.log("Original:", original);  
// Output: [1, 2, 3, 4, 5]
console.log("Shuffled:", shuffled);  
// Output: [randomized order like 3, 1, 5, 2, 4]
```

---

## 32.7 Practical Examples

### Example 1: Quiz Questions

```javascript
const questions = [
    "What is 2+2?",
    "What is the capital of France?",
    "Who wrote Hamlet?",
    "What is the speed of light?"
];

function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const random = Math.floor(Math.random() * (i + 1));
        [array[i], array[random]] = [array[random], array[i]];
    }
}

shuffle(questions);
questions.forEach((q, i) => {
    console.log(`Question ${i + 1}: ${q}`);
});
// Output: (randomized)
// Question 1: Who wrote Hamlet?
// Question 2: What is 2+2?
// Question 3: What is the speed of light?
// Question 4: What is the capital of France?
```

### Example 2: Random Team Assignment

```javascript
const players = ["Alice", "Bob", "Charlie", "David", "Eve", "Frank"];

function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const random = Math.floor(Math.random() * (i + 1));
        [array[i], array[random]] = [array[random], array[i]];
    }
}

shuffle(players);

const team1 = players.slice(0, 3);
const team2 = players.slice(3);

console.log("Team 1:", team1);
// Output: ["Frank", "Alice", "David"]
console.log("Team 2:", team2);
// Output: ["Bob", "Eve", "Charlie"]
```

### Example 3: Card Game

```javascript
const suits = ["♠", "♥", "♦", "♣"];
const ranks = ["A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"];

// Create full deck
const deck = [];
for (let suit of suits) {
    for (let rank of ranks) {
        deck.push(rank + suit);
    }
}

function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const random = Math.floor(Math.random() * (i + 1));
        [array[i], array[random]] = [array[random], array[i]];
    }
}

console.log("Original deck (52 cards):", deck.length);
shuffle(deck);
console.log("Shuffled:", deck.slice(0, 5)); // Show first 5 cards
```

---

## Summary - Chapter 32

✅ **Fisher-Yates** is the correct shuffle algorithm  
✅ Iterate backwards through array  
✅ Pick random index from 0 to current position  
✅ Swap current element with random element  
✅ Truly random and unbiased  
✅ Don't use `.sort()` with random for shuffling  

---

# Chapter 33: Date Objects

## Overview
Date objects represent dates and times in JavaScript, providing methods to get and set date components.



---

## 33.1 What are Date Objects?



Date objects:
- Represent a specific point in time
- Store date and time information
- Provide methods to manipulate dates
- Based on milliseconds since January 1, 1970 (Unix Epoch)

---

## 33.2 Creating Date Objects

### Current Date and Time



```javascript
const now = new Date();
console.log(now);
// Example: Fri Dec 15 2023 14:30:45 GMT-0500 (Eastern Standard Time)
```

### Specific Date (Year, Month, Day, ...)



```javascript
// new Date(year, monthIndex, day, hours, minutes, seconds, milliseconds)
const date = new Date(2024, 0, 15, 10, 30, 0);
// January 15, 2024, 10:30:00 AM

console.log(date);
```

**Note:** Month is 0-indexed (0 = January, 11 = December)

### From ISO String



```javascript
const date = new Date("2024-01-15T10:30:00");
console.log(date);
```

### From Milliseconds (Epoch Time)



```javascript
const date = new Date(1705321800000);
console.log(date);
// Converts milliseconds since Jan 1, 1970 to date
```

---

## 33.3 Getting Date Components

### Get Year



```javascript
const date = new Date();
console.log(date.getFullYear()); // 2024 (4-digit year)
```

### Get Month



```javascript
console.log(date.getMonth()); // 0-11 (0 = January)

// To get month name:
const months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", 
                "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
console.log(months[date.getMonth()]); // "Jan"
```

### Get Day of Month



```javascript
console.log(date.getDate()); // 1-31
```

### Get Day of Week



```javascript
console.log(date.getDay()); // 0-6 (0 = Sunday, 6 = Saturday)

// To get day name:
const days = ["Sunday", "Monday", "Tuesday", "Wednesday", 
              "Thursday", "Friday", "Saturday"];
console.log(days[date.getDay()]); // "Monday"
```

### Get Time Components

, [06:44:53], [06:45:01]

```javascript
console.log(date.getHours());        // 0-23
console.log(date.getMinutes());      // 0-59
console.log(date.getSeconds());      // 0-59
console.log(date.getMilliseconds()); // 0-999
```

---

## 33.4 Setting Date Components



```javascript
const date = new Date();

date.setFullYear(2025);         // Set year
date.setMonth(11);              // Set month (December)
date.setDate(25);               // Set day
date.setHours(10);              // Set hours
date.setMinutes(30);            // Set minutes
date.setSeconds(0);             // Set seconds

console.log(date); // December 25, 2025, 10:30:00
```

, [06:46:15], [06:46:23], [06:46:37], [06:46:44]

---

## 33.5 Comparing Dates



```javascript
const date1 = new Date("2024-01-15");
const date2 = new Date("2024-12-25");

console.log(date1 < date2);  // true
console.log(date1 > date2);  // false
console.log(date1 <= date2); // true
console.log(date1 >= date2); // false

// Check if equal
console.log(date1.getTime() === date2.getTime()); // false
```

---

## 33.6 Date Formatting

### toDateString()

```javascript
const date = new Date();
console.log(date.toDateString());
// "Fri Dec 15 2023"
```

### toTimeString()

```javascript
console.log(date.toTimeString());
// "14:30:45 GMT-0500 (Eastern Standard Time)"
```

### toLocaleDateString()

```javascript
console.log(date.toLocaleDateString());
// "12/15/2023" (format depends on locale)

console.log(date.toLocaleDateString("en-US"));
// "12/15/2023"

console.log(date.toLocaleDateString("en-GB"));
// "15/12/2023"
```

### toLocaleTimeString()

```javascript
console.log(date.toLocaleTimeString());
// "2:30:45 PM"
```

### Custom Formatting

```javascript
const date = new Date();

const day = date.getDate().toString().padStart(2, '0');
const month = (date.getMonth() + 1).toString().padStart(2, '0');
const year = date.getFullYear();

console.log(`${month}/${day}/${year}`);
// "12/15/2023"
```

---

## 33.7 Practical Examples

### Example 1: Age Calculator

```javascript
function calculateAge(birthDate) {
    const today = new Date();
    const birth = new Date(birthDate);
    
    let age = today.getFullYear() - birth.getFullYear();
    const monthDiff = today.getMonth() - birth.getMonth();
    
    if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < birth.getDate())) {
        age--;
    }
    
    return age;
}

console.log(calculateAge("1990-05-15")); // Current age
```

### Example 2: Days Until Event

```javascript
function daysUntil(targetDate) {
    const today = new Date();
    const target = new Date(targetDate);
    
    const diffTime = target - today;
    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
    
    return diffDays;
}

console.log(daysUntil("2024-12-25")); // Days until Christmas
```

### Example 3: Greeting Based on Time

```javascript
function getGreeting() {
    const now = new Date();
    const hour = now.getHours();
    
    if (hour < 12) {
        return "Good morning!";
    } else if (hour < 18) {
        return "Good afternoon!";
    } else {
        return "Good evening!";
    }
}

console.log(getGreeting());
```

### Example 4: Format Date Display

```javascript
function formatDate(date) {
    const days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
    const months = ["January", "February", "March", "April", "May", "June",
                    "July", "August", "September", "October", "November", "December"];
    
    const dayName = days[date.getDay()];
    const monthName = months[date.getMonth()];
    const day = date.getDate();
    const year = date.getFullYear();
    
    return `${dayName}, ${monthName} ${day}, ${year}`;
}

const today = new Date();
console.log(formatDate(today));
// "Friday, December 15, 2023"
```

---

## 33.8 Common Date Operations

### Add Days

```javascript
function addDays(date, days) {
    const result = new Date(date);
    result.setDate(result.getDate() + days);
    return result;
}

const today = new Date();
const nextWeek = addDays(today, 7);
console.log(nextWeek);
```

### Get Difference in Days

```javascript
function daysBetween(date1, date2) {
    const diffTime = Math.abs(date2 - date1);
    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
    return diffDays;
}

const start = new Date("2024-01-01");
const end = new Date("2024-12-31");
console.log(daysBetween(start, end)); // 365
```

### Is Leap Year

```javascript
function isLeapYear(year) {
    return (year % 4 === 0 && year % 100 !== 0) || (year % 400 === 0);
}

console.log(isLeapYear(2024)); // true
console.log(isLeapYear(2023)); // false
```

---

## Summary - Chapter 33

✅ **Date objects** represent dates and times  
✅ `new Date()` creates current date/time  
✅ `.getFullYear()`, `.getMonth()`, `.getDate()` get components  
✅ `.getDay()` gets day of week (0-6)  
✅ `.getHours()`, `.getMinutes()`, `.getSeconds()` get time  
✅ `.setFullYear()`, `.setMonth()`, etc. modify dates  
✅ Can compare dates with `<`, `>`, etc.  
✅ Month is 0-indexed (0 = January)  

---

## Practice Exercises

### Exercise 1: Birthday Countdown
Calculate days until next birthday.

### Exercise 2: Time Zone Converter
Convert date/time between time zones.

### Exercise 3: Meeting Scheduler
Check if meeting time is within business hours.

### Exercise 4: Date Validator
Check if entered date is valid.

---

## Quick Reference

```javascript
// Create dates
const now = new Date();
const specific = new Date(2024, 0, 15); // Jan 15, 2024

// Get components
now.getFullYear()  // Year (4-digit)
now.getMonth()     // Month (0-11)
now.getDate()      // Day (1-31)
now.getDay()       // Day of week (0-6)
now.getHours()     // Hours (0-23)
now.getMinutes()   // Minutes (0-59)
now.getSeconds()   // Seconds (0-59)

// Set components
now.setFullYear(2025)
now.setMonth(11)
now.setDate(25)

// Compare
date1 < date2
date1.getTime() === date2.getTime()

// Format
now.toDateString()
now.toLocaleDateString()
```

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** | **Next** |
|:------------:|:--------:|:--------:|
| [◀️ Arrays of Objects & Sorting](Chapters-30-31-Arrays-of-Objects-and-Sorting.md) | [📑 Index](../README.md) | [Closures & setTimeout ▶️](Chapters-34-35-Closures-and-setTimeout.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapters-32--33-shuffling-arrays--date-objects)**

Made with ❤️ for JavaScript learners

</div>
