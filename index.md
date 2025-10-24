# JavaScript Full Course Index

## Chapter 1: Introduction & Setup

* Introduction to the course and projects (Digital Clock, Stopwatch, Calculator, Rock Paper Scissors, Image Slider, Weather App) [00:00:04]
* What is JavaScript? (Dynamic/interactive web pages, runs on browser) [00:00:44]
* Role of HTML, CSS, and JavaScript in web development [00:00:59]
* Prerequisites (HTML/CSS recommended) [00:01:24]
* Required tools: Text Editor (VS Code recommended) [00:01:40]
* Setting up the project folder (website folder in VS Code) [00:02:00]
* Creating necessary files: `index.html`, `style.css`, `index.js` [00:02:22]
* Basic HTML structure (`index.html` boilerplate) [00:02:30]
* Linking CSS (`style.css`) to HTML [00:03:43]
* Linking JavaScript (`index.js`) to HTML (using `<script>` tag, best practice: place at bottom) [00:04:21], [00:06:39]
* Installing and using the Live Server extension in VS Code [00:04:39]
* Basic HTML elements (`h1`, `p`, lorem ipsum) [00:05:30]
* Basic CSS styling (body font, font size) [00:06:04]

---

## Chapter 2: JavaScript Basics & Output

* Basic output methods
    * `console.log()` (Using double quotes, single quotes, backticks/template literals) [00:07:06], [00:07:21]
    * Accessing Dev Tools Console [00:07:42]
    * `window.alert()` (Creating pop-up boxes) [00:08:21]
* Comments (Single line `//` and Multi-line `/* */`) [00:09:04]
* Manipulating HTML content with JavaScript
    * Adding IDs to HTML elements (`h1`, `p`) [00:09:59]
    * Selecting elements using `document.getElementById()` [00:10:37]
    * Changing text content using `.textContent` [00:11:06]

---

## Chapter 3: Variables

* What are variables? (Containers for values) [00:12:38]
* Steps to create variables: Declaration (`let`) and Assignment (`=`) [00:12:49]
* Variable naming rules (Unique names) [00:13:06]
* Combined declaration and assignment [00:13:58]
* Data Types:
    * **Numbers:** (Integers, decimals like age, price, GPA) [00:14:25]
    * Using variables in template literals (`${variableName}`) [00:15:28]
    * Finding the data type using `typeof` keyword [00:16:38]
    * **Strings:** (Series of characters using double/single quotes; e.g., firstName, favoriteFood, email) [00:17:02]
    * Strings can contain numbers but aren't used for math [00:19:07]
    * **Booleans:** (`true` or `false`; e.g., online status, forSale status, student status) [00:19:28]
    * Using booleans with `if` statements (preview) [00:21:34]
* Displaying variables on the web page (using `getElementById` and `.textContent`) [00:21:53]

---

## Chapter 4: Operators & User Input

* **Arithmetic Operators:** [00:25:28]
    * Operands and Operators defined [00:25:28]
    * Addition (`+`), Subtraction (`-`), Multiplication (`*`), Division (`/`) [00:26:16]
    * Exponents (`**`) [00:27:09]
    * Modulus (`%`) (Remainder of division, useful for even/odd check) [00:27:46]
    * Augmented Assignment Operators (`+=`, `-=`, `*=`, `/=`, `**=`, `%=`) [00:28:55]
    * Increment (`++`) and Decrement (`--`) Operators [00:30:19]
    * Operator Precedence (Parentheses, Exponents, Multiplication/Division/Modulo, Addition/Subtraction - PEMDAS) [00:30:47]
* **Accepting User Input:** [00:33:48]
    * Easy way: `window.prompt()` [00:34:08]
    * Professional way: HTML Text Box (`<input type="text">`) and Button [00:33:57], [00:35:26]
    * Using labels (`<label>`) for text boxes [00:35:56]
    * Getting button element by ID (`document.getElementById()`) [00:36:35]
    * Handling button clicks (`.onclick = function(){...}`) [00:36:56]
    * Getting value from a text box (`.value`) [00:37:46]
    * Updating HTML content based on input [00:38:11]

---

## Chapter 5: Type Conversion & Constants

* **Type Conversion:** [00:39:11]
    * Changing the data type of a value (String to Number, etc.) [00:39:11]
    * Why convert? (User input is string, needed for math) [00:39:26]
    * Example: Age input treated as string concatenation [00:39:36]
    * Using the `Number()` function to convert to a number [00:40:26]
    * Demonstrating `typeof` before and after conversion [00:40:56]
    * Converting non-numeric strings to Number results in `NaN` (Not a Number) [00:41:35]
    * Converting values to String using `String()` [00:41:56]
    * Converting values to Boolean using `Boolean()` [00:42:09]
        * Non-empty strings/numbers (except 0) convert to `true` [00:42:56]
        * Empty strings, 0, `undefined` convert to `false` [00:43:35]
        * Useful for checking empty user input [00:43:48]
* **Constants (`const`):** [00:44:52]
    * Variables that can't be changed after assignment [00:44:52]
    * Example: Calculating circle circumference [00:44:55]
    * Problem with `let`: Accidental reassignment (e.g., changing Pi) [00:46:36]
    * Using `const` prevents reassignment, provides security [00:47:12]
    * Good practice: Uppercase `const` names for primitive types (numbers, booleans) [00:47:20], [00:47:31]
    * Attempting to reassign `const` throws a TypeError [00:47:56]
    * Rewriting circumference program using HTML input and `const` for Pi [00:48:22]

---

## Chapter 6: Project 1: Counter Program

* Project goal: Create a counter with decrease, reset, increase buttons [00:52:33]
* HTML Structure:
    * Label (`<label>`) for count display (ID: `countLabel`) [00:53:04]
    * Div (`<div>`) for button container (ID: `buttonContainer`) [00:54:24]
    * Three buttons (`<button>`) with IDs (`decreaseBtn`, `resetBtn`, `increaseBtn`) and a common class (`buttons`) [00:53:26]
* CSS Styling:
    * Styling `countLabel` (display block, text align, font size/family) [00:54:52]
    * Styling `buttonContainer` (text align center) [00:55:48]
    * Styling `.buttons` class (padding, font size/color, background, border radius, cursor, transition) [00:56:15]
    * Adding hover effect (`.buttons:hover`) [00:57:47]
* JavaScript Functionality:
    * Getting elements by ID (`decreaseBtn`, `resetBtn`, `increaseBtn`, `countLabel`) [00:58:25]
    * Using `const` for elements (won't be reassigned) [00:59:47]
    * Using `let` for the count variable (will be reassigned) [00:59:34]
    * Assigning functions to button `.onclick` events [01:00:05]
    * Increase function: Increment count, update `countLabel.textContent` [01:00:05]
    * Decrease function: Decrement count, update `countLabel.textContent` [01:00:53]
    * Reset function: Set count to 0, update `countLabel.textContent` [01:01:21]

---

## Chapter 7: Math Object & Random Numbers

* **Math Object:** [01:01:45]
    * Built-in object with math properties and methods [01:01:53]
    * Properties: `Math.PI`, `Math.E` (Euler's number) [01:01:54]
    * Methods:
        * `Math.round()` (Rounds to nearest integer) [01:02:47]
        * `Math.floor()` (Rounds down) [01:03:16]
        * `Math.ceil()` (Rounds up) [01:03:34]
        * `Math.trunc()` (Removes decimal part) [01:03:53]
        * `Math.pow(base, exponent)` (Raises base to power) [01:04:04]
        * `Math.sqrt()` (Square root) [01:04:23]
        * `Math.log()` (Natural logarithm) [01:04:36]
        * Trigonometry: `Math.sin()`, `Math.cos()`, `Math.tan()` (Uses radians) [01:04:52]
        * `Math.abs()` (Absolute value) [01:05:24]
        * `Math.sign()` (Returns sign: -1, 0, or 1) [01:05:52]
        * `Math.max()` (Finds maximum value from arguments) [01:06:12]
        * `Math.min()` (Finds minimum value from arguments) [01:06:45]
* **Random Number Generation:** [01:07:24]
    * `Math.random()` (Generates pseudo-random number between 0 [inclusive] and 1 [exclusive]) [01:07:35]
    * Generating a random integer (e.g., rolling a dice 1-6):
        * Multiply `Math.random()` by the maximum desired value (exclusive) `* 6` [01:08:15]
        * Use `Math.floor()` to remove decimal [01:08:30]
        * Add 1 to shift range from 0-5 to 1-6 `+ 1` [01:08:54]
    * Generating a random integer within a range (min, max):
        * Formula: `Math.floor(Math.random() * (max - min + 1)) + min` [01:09:23] - *(Note: Video uses a slightly different but equivalent formula structure)*
* **Project 2: Random Number Generator:** [01:10:23]
    * HTML: Button (ID: `myButton`, Text: Roll), Labels (ID: `label1`, `label2`, `label3`, Class: `myLabels`) [01:10:23]
    * CSS: Styling body, button, labels [01:10:43]
    * JavaScript:
        * Get button and label elements [01:12:02]
        * Define min/max constants [01:12:24]
        * Declare random number variables [01:12:45]
        * Assign function to button `.onclick` [01:12:52]
        * Generate random numbers within the function using the formula [01:13:01]
        * Update label `.textContent` with random numbers [01:13:23]
        * Modifying to roll multiple dice (3 labels, 3 random numbers) [01:14:01]

---

## Chapter 8: Control Flow: If Statements & Checked Property

* **If Statements:** [01:16:02]
    * Execute code based on a condition (`true` or `false`) [01:16:02]
    * Syntax: `if (condition) { // code to run if true }` [01:16:23]
    * Comparison Operators (`>`, `<`, `>=`, `<=`) [01:16:29]
    * `else` Clause (Code to run if condition is `false`) [01:17:16]
    * Using boolean variables directly as conditions [01:18:54]
    * Nested `if` statements (Checking multiple conditions sequentially) [01:20:01]
    * `else if` Clause (Checking multiple alternative conditions) [01:22:59]
    * Importance of `else if` order [01:25:04]
    * Equality Comparison (`==` vs `===` mentioned later) - Using `==` here [01:26:08]
    * Exercise: Age submission form using HTML input and button [01:27:07]
        * Getting input value, converting to Number [01:29:46]
        * Using `if/else if/else` to display messages in a paragraph element (`resultElement`) [01:30:13]
* **Checked Property:** [01:31:51]
    * Determines the checked state of HTML checkboxes or radio buttons [01:32:00]
    * Returns `true` if checked/selected, `false` otherwise [01:32:08]
    * HTML Setup:
        * Checkbox (`<input type="checkbox">`) with ID and Label (`<label for="...">`) [01:32:21]
        * Radio buttons (`<input type="radio">`) with IDs, common `name` attribute (for grouping), and Labels [01:33:16]
        * Submit button and paragraph elements for results [01:34:59]
    * JavaScript:
        * Get references to checkbox, radio buttons, submit button, and result paragraphs [01:36:40]
        * Add `.onclick` handler to submit button [01:38:15]
        * Inside handler, use `if` statement with `.checked` property to determine state [01:38:34]
        * Update result paragraph `.textContent` based on checked state [01:38:59]
        * Using `if/else if/else` for radio button group selection [01:39:52]

---

## Chapter 9: Ternary Operator & Switches

* **Ternary Operator:** [01:42:07]
    * Shortcut for `if/else` statements [01:42:13]
    * Syntax: `condition ? codeIfTrue : codeIfFalse` [01:42:20]
    * Useful for assigning a variable based on a condition [01:42:13]
    * Example: Checking age for adult/minor status [01:42:43]
    * Example: Greeting based on time (morning/afternoon) [01:44:37]
    * Example: Checking student status (boolean) [01:45:39]
    * Example: Calculating purchase discount based on amount [01:46:35]
* **Switches:** [01:48:50]
    * Efficient replacement for many `else if` statements [01:48:50]
    * Compares a value against matching `case`s [01:49:50]
    * Syntax: `switch (value) { case match1: // code; break; case match2: // code; break; default: // code; }` [01:49:39]
    * Example: Determining day of the week based on number (1-7) [01:49:03]
    * `break` statement: Exits the switch after a match is found [01:50:28]
    * Importance of `break` (fall-through behavior without it) [01:52:19]
    * `default` case: Executes if no other cases match [01:51:36]
    * Using expressions/conditions in cases (comparing against `true`) [01:53:13]
    * Example: Assigning letter grade based on test score ranges [01:53:13]

---

## Chapter 10: String Methods & Slicing

* **String Methods:** [01:55:33]
    * Manipulating and working with text (strings) [01:55:40]
    * `.charAt(index)`: Returns the character at a specific index [01:56:02]
    * `.indexOf(substring)`: Returns index of the first occurrence [01:57:14]
    * `.lastIndexOf(substring)`: Returns index of the last occurrence [01:57:39]
    * `.length`: Property (not method) returning the string length [01:57:55]
    * `.trim()`: Removes whitespace from beginning and end [01:58:14]
    * `.toUpperCase()`: Converts string to uppercase [01:58:49]
    * `.toLowerCase()`: Converts string to lowercase [01:58:59]
    * `.repeat(n)`: Repeats the string `n` times [01:59:09]
    * `.startsWith(substring)`: Returns boolean if string starts with substring [01:59:19]
    * `.endsWith(substring)`: Returns boolean if string ends with substring [02:00:38]
    * `.includes(substring)`: Returns boolean if string contains substring [02:00:58]
    * `.replaceAll(oldSubstring, newSubstring)`: Replaces all occurrences [02:01:19]
    * `.padStart(targetLength, padString)`: Pads start with `padString` until `targetLength` [02:02:29]
    * `.padEnd(targetLength, padString)`: Pads end with `padString` until `targetLength` [02:03:14]
* **String Slicing:** [02:03:35]
    * Creating a substring from a portion of another string [02:03:43]
    * Does not alter the original string [02:03:43]
    * `.slice(startIndex, endIndex)`: Extracts a section [02:04:10]
        * `startIndex`: Included in the slice [02:04:26]
        * `endIndex`: Excluded from the slice (exclusive) [02:04:48]
        * `endIndex` is optional; if omitted, slices to the end [02:05:53]
    * Using negative indices (count from the end) [02:06:32]
    * Making slicing dynamic using `.indexOf()` to find split points (e.g., space in full name, '@' in email) [02:07:06]
    * Example: Extracting first and last names from a full name [02:07:28]
    * Example: Extracting username and domain from an email address [02:09:28]

---

## Chapter 11: Method Chaining

* **Method Chaining:** [02:11:36]
    * Calling one method after another in a continuous line [02:11:43]
    * Avoids creating intermediate variables [02:14:43]
    * Example without chaining: Capitalizing the first letter of a username (trim, get char, uppercase, get rest, lowercase, combine) [02:11:58]
    * Example with chaining: `username.trim().charAt(0).toUpperCase()` and `username.trim().slice(1).toLowerCase()` [02:14:55]
    * Pros: Less code, avoids temporary variables [02:16:47]
    * Cons: Can become difficult to read if the chain is too long [02:16:47]

---

## Chapter 12: Logical Operators & Strict Equality

* **Logical Operators:** [02:17:02]
    * Combine or manipulate boolean values (`true`/`false`) [02:17:10]
    * `&&` (AND): Returns `true` only if **both** operands are `true` [02:18:57]
        * Example: Checking temperature range (`temp > 0 && temp <= 30`) [02:18:47]
    * `||` (OR): Returns `true` if **at least one** operand is `true` [02:19:55]
        * Example: Checking if weather is bad (`temp <= 0 || temp > 30`) [02:20:26]
    * `!` (NOT): Inverts a boolean value (`true` becomes `false`, `false` becomes `true`) [02:21:03]
        * Example: Checking if it's NOT sunny (`!isSunny`) [02:21:47]
* **Strict Equality (`===`) vs Loose Equality (`==`):** [02:22:47]
    * Assignment (`=`): Assigns a value [02:22:54]
    * Comparison (`==`): Compares values, **allows type coercion** (e.g., `3.14 == "3.14"` is `true`) [02:23:00]
    * Strict Equality (`===`): Compares values **AND data types**, no type coercion (e.g., `3.14 === "3.14"` is `false`) [02:23:06]
    * Recommended to use `===` for clarity and safety [02:26:27]
    * Strict Inequality (`!==`): Checks if values or types are different [02:25:46]
    * Inequality (`!=`): Checks if values are different, allows type coercion [02:25:09]

---

## Chapter 13: Loops: While & For

* **While Loops:** [02:26:42]
    * Repeat code while a condition is `true` [02:26:46]
    * Can run infinitely if the condition never becomes `false` (Infinite Loop) [02:27:16]
    * Need a way to eventually make the condition `false` within the loop [02:28:16]
    * Example: Prompting for username until it's not empty or null [02:28:21]
    * **Do While Loops:** [02:30:03]
        * Syntax: `do { // code } while (condition);` [02:30:03]
        * Executes the code block **at least once**, then checks the condition [02:30:16]
        * Useful when the first iteration must happen regardless of the condition [02:30:31]
    * Example: Login prompt loop (using `while (!loggedIn)`) [02:31:09]
* **For Loops:** [02:34:54]
    * Repeat code a **limited** amount of times [02:34:54]
    * Syntax: `for (initialization; condition; finalExpression) { // code }` [02:35:16]
        * `initialization`: Runs once before the loop starts (e.g., `let i = 0`) [02:35:22]
        * `condition`: Checked before each iteration; loop continues if `true` (e.g., `i < 10`) [02:35:46]
        * `finalExpression`: Runs after each iteration (e.g., `i++`) [02:36:04]
    * Example: Counting 1 to 10 [02:37:08]
    * Example: Counting down from 10 to 1 [02:37:45]
    * Changing the increment/decrement value (e.g., `i += 2`, `i -= 2`) [02:37:22]
    * `continue`: Skips the rest of the current iteration and moves to the next [02:38:34]
    * `break`: Exits the loop entirely [02:39:53]

---

## Chapter 14: Project 3: Number Guessing Game

* Project Goal: Guess a random number within a range [02:40:38]
* Setup:
    * Define `minNum` and `maxNum` constants [02:40:49]
    * Generate the `answer` using `Math.random()` and the range formula [02:41:11]
    * Initialize `attempts`, `guess`, and `running` (boolean) variables [02:43:06]
* Game Loop (`while (running)`): [02:43:35]
    * Prompt user for guess using `window.prompt` [02:44:09]
    * Validate Input:
        * Convert guess to `Number` [02:44:59]
        * Check if `isNaN(guess)` [02:45:42]
        * Check if guess is outside the allowed range (`minNum`, `maxNum`) [02:46:15]
        * Provide feedback using `window.alert` for invalid input [02:45:54]
    * Process Valid Guess:
        * Increment `attempts` [02:47:01]
        * Compare `guess` to `answer`:
            * If `guess < answer`, alert "Too low" [02:47:13]
            * If `guess > answer`, alert "Too high" [02:47:31]
            * If `guess === answer`, alert "Correct!", display attempts, set `running = false` to end loop [02:47:45]

---

## Chapter 15: Functions

* **Functions:** [02:49:33]
    * Reusable section of code [02:49:33]
    * Declare once, use whenever needed by calling the function [02:49:41]
    * **Function Declaration:** `function functionName(parameters) { // code }` [02:49:51]
    * **Calling a Function:** `functionName(arguments)` [02:50:44]
* **Parameters vs Arguments:**
    * **Parameters:** Variables defined in the function declaration (placeholders) [02:52:44]
    * **Arguments:** Values passed into the function when it's called [02:52:39]
    * Order matters [02:53:51]
    * Example: `happyBirthday(username, age)` function [02:51:35]
* **Return Keyword:** [02:54:13]
    * Sends a value back from the function to where it was called [02:54:53]
    * Function call effectively becomes the returned value [02:55:08]
    * Example: `add(x, y)` function returning `x + y` [02:54:23]
    * Can store returned value in a variable or use directly [02:55:14]
* More Function Examples:
    * `subtract`, `multiply`, `divide` functions [02:56:02]
    * `isEven(number)` function using modulus and `if/else` or ternary operator [02:57:07]
    * `isValidEmail(email)` function using `.includes('@')` and `if/else` or ternary operator [02:59:07]

---

## Chapter 16: Variable Scope

* **Variable Scope:** Where a variable is recognized and accessible [02:48:51]
* **Local Scope:**
    * Variables declared inside a function (or block `{}`) [03:03:02]
    * Only accessible within that function/block [03:03:10]
    * Allows reusing variable names in different scopes without conflict [03:02:20]
    * Functions cannot see variables inside other functions [03:03:28]
* **Global Scope:**
    * Variables declared outside any function [03:04:14]
    * Accessible from anywhere in the program [03:04:51]
    * Generally discouraged in large programs due to potential naming conflicts [03:05:30]
* Scope Precedence: If a local variable has the same name as a global variable, the local variable takes precedence within its scope [03:05:55]

---

## Chapter 17: Project 4: Temperature Conversion Program

* Project Goal: Convert temperature between Celsius and Fahrenheit [03:07:12]
* HTML Structure (`<form>`):
    * H1 heading [03:07:35]
    * Input (`<input type="number">`) for temperature (ID: `textbox`) [03:07:55]
    * Radio buttons for conversion direction (to Fahrenheit/to Celsius) with common `name="unit"` and unique IDs (`toFahrenheit`, `toCelsius`) [03:08:30]
    * Labels for radio buttons [03:09:10]
    * Submit button (`<button type="button">`) calling `convert()` function on click [03:10:32]
    * Paragraph element for result (ID: `result`) [03:11:13]
* CSS Styling:
    * Styling body, H1, form, textbox, labels, button (including `:hover`) and result paragraph [03:11:29]
* JavaScript Functionality:
    * Get references to textbox, radio buttons, and result paragraph using IDs [03:17:58]
    * Declare `temp` variable [03:19:12]
    * `convert()` function:
        * Check which radio button is `.checked` using `if/else if/else` [03:19:28]
        * If `toFahrenheit` checked:
            * Get `temp` from `textbox.value`, convert to `Number` [03:21:04]
            * Apply Celsius to Fahrenheit formula: `temp = temp * 9 / 5 + 32` [03:21:26]
            * Update `result.textContent` with formatted temperature (using `.toFixed(1)`) + "°F" [03:21:42]
        * If `toCelsius` checked:
            * Get `temp` from `textbox.value`, convert to `Number` [03:22:51]
            * Apply Fahrenheit to Celsius formula: `temp = (temp - 32) * 5 / 9` [03:22:51]
            * Update `result.textContent` with formatted temperature + "°C" [03:23:06]
        * Else (neither checked): Update `result.textContent` to "Select a unit" [03:19:56]

---

## Chapter 18: Arrays

* **Arrays:** [03:23:24]
    * Variable-like structure holding multiple values [03:23:33]
    * Syntax: `let arrayName = [value1, value2, ...];` [03:23:53]
    * Values are called **elements** [03:24:27]
    * Accessing elements using zero-based **index**: `arrayName[0]`, `arrayName[1]`, etc. [03:24:39]
    * Modifying elements: `arrayName[index] = newValue;` [03:25:11]
* **Array Methods & Properties:**
    * `.push(element)`: Adds element to the end [03:25:48]
    * `.pop()`: Removes element from the end [03:26:06]
    * `.unshift(element)`: Adds element to the beginning [03:26:11]
    * `.shift()`: Removes element from the beginning [03:26:31]
    * `.length`: Property (not method) returns number of elements [03:26:37]
    * `.indexOf(element)`: Returns index of first occurrence (-1 if not found) [03:27:11]
* **Looping Through Arrays:**
    * Standard `for` loop using `.length`: `for (let i = 0; i < array.length; i++) { console.log(array[i]); }` [03:28:05]
    * Looping backwards [03:29:15]
    * **Enhanced `for` loop (for...of):** `for (let element of array) { console.log(element); }` [03:30:03]
* **Sorting Arrays:**
    * `.sort()`: Sorts elements **as strings** (lexicographically) in place [03:30:48]
    * `.reverse()`: Reverses the order of elements in place [03:30:58]
    * Sorting numbers correctly requires a compare function (covered later) [03:30:06] - *(See Chapter 29)*

---

## Chapter 19: Spread & Rest Operators

* **Spread Operator (`...`):** [03:31:39]
    * Expands an iterable (array, string) into individual elements [03:31:41]
    * "Unpacks" the elements [03:31:48]
    * Use cases:
        * Passing array elements as arguments to functions like `Math.max(...numbers)` [03:32:10]
        * Converting a string into an array of characters: `[...username]` [03:33:26]
        * Creating shallow copies of arrays: `let newArray = [...oldArray];` [03:34:24]
        * Combining arrays: `let combinedArray = [...array1, ...array2, element1, ...];` [03:35:10]
* **Rest Parameters (`...`):** [03:36:27]
    * Used in function parameters [03:36:34]
    * Bundles separate arguments into an array [03:36:40]
    * Allows functions to accept a variable number of arguments [03:36:34]
    * Opposite of spread operator [03:36:53]
    * Syntax: `function functionName(...arrayName) { // arrayName is an array }` [03:37:40]
    * Use cases:
        * Collecting multiple food items into a `foods` array parameter [03:37:31]
        * Creating a `sum(...numbers)` function to sum any number of arguments [03:40:22]
        * Creating a `getAverage(...numbers)` function [03:41:40]
        * Creating a `combineStrings(...strings)` function using `.join()` [03:42:40]

---

## Chapter 20: Project 5: Dice Roller

* Project Goal: Simulate rolling a specified number of dice [03:44:31]
* Prerequisites: Dice images (1-6) [03:44:40]
* HTML Structure (`<div id="container">`):
    * H1 heading [03:45:19]
    * Label and Input (`<input type="number">`) for number of dice (ID: `numOfDice`, default value 1, min 1) [03:45:32]
    * Button to roll (onclick calls `rollDice()`) [03:46:40]
    * Div for numerical result (ID: `diceResult`) [03:46:58]
    * Div for images (ID: `diceImages`) [03:47:09]
* CSS Styling:
    * Styling container, button (including `:hover`, `:active`), input, result text, and images [03:47:18]
* JavaScript Functionality (`rollDice()` function):
    * Get references to input, result div, images div [03:50:39]
    * Get `numOfDice` value from input [03:50:46]
    * Initialize empty arrays: `values` (for numbers) and `images` (for HTML image strings) [03:52:09]
    * `for` loop (runs `numOfDice` times): [03:52:28]
        * Generate random dice value (1-6) [03:52:54]
        * Push value to `values` array [03:54:01]
        * Create image HTML string (`<img src="dice_images/${value}.png" alt="Dice ${value}">`) and push to `images` array [03:54:38]
    * Update `diceResult.textContent` with joined `values` array (`values.join(", ")`) [03:55:40]
    * Update `diceImages.innerHTML` with joined `images` array (`images.join("")`) [03:56:33]

---

## Chapter 21: Project 6: Random Password Generator

* Project Goal: Generate random passwords based on user-defined criteria [03:58:43]
* Setup:
    * Define constants for options: `passwordLength`, `includeLowercase`, `includeUppercase`, `includeNumbers`, `includeSymbols` [03:59:03]
* `generatePassword()` Function (Main Logic): [04:00:09]
    * Parameters match the option constants [04:00:09]
    * Define character sets (lowercase, uppercase, numbers, symbols) as constant strings [04:02:08]
    * Initialize `allowedChars` string and `password` string (empty) [04:03:31]
    * Conditionally concatenate character sets to `allowedChars` based on boolean parameters (using ternary operator) [04:03:53]
    * Input Validation:
        * Check if `length <= 0`, return error message [04:06:00]
        * Check if `allowedChars.length === 0`, return error message [04:06:57]
    * Password Generation Loop (`for i < length`): [04:07:51]
        * Generate random index within `allowedChars` length: `Math.floor(Math.random() * allowedChars.length)` [04:08:24]
        * Get character at random index from `allowedChars` [04:09:07]
        * Concatenate character to `password` string [04:09:07]
    * Return the generated `password` [04:09:26]
* Calling the Function:
    * Call `generatePassword()` with the option constants as arguments [04:00:38]
    * Store the returned password [04:01:08]
    * Display the generated password using `console.log` [04:01:35]

---

## Chapter 22: Callbacks

* **Callbacks:** [04:10:48]
    * A function passed as an argument to another function [04:10:55]
    * Used to handle asynchronous operations (operations that take time) [04:11:03]
    * Ensures code runs *after* an asynchronous task completes [04:11:30]
* Synchronous vs Asynchronous Example:
    * Synchronous: `hello()`, `goodbye()` run in order [04:11:54]
    * Asynchronous (simulated with `setTimeout`): `goodbye()` might run before `hello()` finishes [04:12:28]
* Using Callbacks for Order:
    * Pass the second function (`goodbye`) as an argument to the first (`hello(goodbye)`) [04:13:07]
    * The first function defines a parameter (e.g., `callback`) to receive the function [04:13:33]
    * Call the `callback()` inside the first function *after* its main task is done [04:13:37]
    * Example: `sum(x, y, callback)` function that calls `callback(result)` after calculating sum [04:14:52]
    * Callback function (`displayConsole` or `displayPage`) receives the result [04:15:24]

---

## Chapter 23: Array Methods: forEach, map, filter, reduce

* **Recap:** Callbacks are functions passed as arguments.
* **`.forEach(callback)`:** [04:18:06]
    * Executes a callback function once for each array element [04:18:13]
    * Does **not** return a new array; modifies in place (if callback does so) or used for side effects (like logging) [04:18:13]
    * Callback signature: `function(element, index, array)` (index and array are optional) [04:19:25]
    * Example: Displaying each number `numbers.forEach(display)` [04:19:01]
    * Example: Doubling each number in place `numbers.forEach(double)` [04:19:52]
    * Example: Uppercasing each fruit string in place `fruits.forEach(uppercase)` [04:23:06]
    * Example: Capitalizing first letter of each fruit `fruits.forEach(capitalize)` [04:24:30]
* **`.map(callback)`:** [04:26:07]
    * Executes a callback function once for each array element [04:26:13]
    * **Returns a new array** containing the results of the callback function [04:26:20]
    * Does **not** modify the original array [04:28:14]
    * Callback signature: `function(element, index, array)` (usually only `element` is needed) [04:28:57]
    * Callback **must return** the new value for the element in the new array [04:26:46]
    * Example: Squaring numbers `const squares = numbers.map(square)` [04:27:11]
    * Example: Uppercasing student names `const studentsUpper = students.map(uppercase)` [04:29:17]
    * Example: Formatting dates `const formattedDates = dates.map(formatDates)` [04:30:53]
* **`.filter(callback)`:** [04:33:07]
    * Executes a callback function once for each array element [04:33:13]
    * **Returns a new array** containing only the elements for which the callback returns `true` [04:33:13]
    * Does **not** modify the original array [04:33:13]
    * Callback signature: `function(element, index, array)` (usually only `element` is needed) [04:33:42]
    * Callback **must return a boolean** (`true` to keep, `false` to discard) [04:34:05]
    * Example: Filtering even numbers `const evenNums = numbers.filter(isEven)` [04:34:17]
    * Example: Filtering adults from ages `const adults = ages.filter(isAdult)` [04:35:50]
    * Example: Filtering short words `const shortWords = words.filter(getShortWords)` [04:37:42]
* **`.reduce(callback, initialValue)`:** [04:39:36]
    * Executes a callback function for each element, resulting in a **single output value** [04:39:43]
    * Callback signature: `function(accumulator, element, index, array)` [04:40:45]
        * `accumulator`: The value resulting from the previous callback invocation (or `initialValue` if provided). [04:41:43]
        * `element`: The current element being processed. [04:41:43]
    * Callback **must return** the updated accumulator value [04:40:55]
    * `initialValue` (optional): Value to use as the first accumulator. If not provided, the first element is used as the initial accumulator, and iteration starts from the second element. [04:42:02] - *(Note: video implicitly starts accumulator at 0 for sum)*
    * Example: Summing prices `const total = prices.reduce(sum)` [04:40:23]
    * Example: Finding max grade `const maximum = grades.reduce(getMax)` [04:43:04]
    * Example: Finding min grade `const minimum = grades.reduce(getMin)` [04:44:15]

---

## Chapter 24: Function Expressions & Arrow Functions

* **Function Declarations (Recap):** `function name() {}` [04:45:21]
* **Function Expressions:** [04:45:13]
    * Defining a function as a value or assigning it to a variable [04:45:13]
    * Syntax: `const variableName = function(parameters) { // code };` [04:45:50]
    * Can be anonymous (no name after `function` keyword) [04:47:10]
    * Can be passed as arguments to other functions (like callbacks) [04:46:31]
    * Example: Assigning `hello` function to a constant [04:45:50]
    * Example: Passing an anonymous function expression to `setTimeout` [04:47:01]
    * Example: Using anonymous function expressions with `.map()`, `.filter()`, `.reduce()` [04:47:34]
    * Benefits: No need for names (less namespace pollution), useful for callbacks, closures, etc. [04:52:03]
* **Arrow Functions (`=>`):** [04:52:42]
    * Concise way to write function expressions [04:52:42]
    * Good for simple, single-use functions [04:52:49]
    * Syntax Variations:
        * ` (param1, param2) => { statements; return value; }` [04:54:52]
        * ` (param1, param2) => expression` (Implicit return of the expression value) [04:57:40]
        * ` param => { statements; }` (Parentheses optional for single parameter) [04:58:41] - *(Video uses parentheses even for single param often)*
        * ` () => expression` (Parentheses required for no parameters) [04:53:59]
    * Example: `hello` arrow function [04:53:59]
    * Example: Passing arrow function to `setTimeout` [04:56:49]
    * Example: Using arrow functions with `.map()`, `.filter()`, `.reduce()` [04:57:17]
    * **Note:** `this` keyword behaves differently in arrow functions (lexical scoping) - covered later [05:11:24]

---

## Chapter 25: Objects & `this` Keyword

* **Objects:** [05:00:39]
    * Collection of related properties and/or methods [05:00:46]
    * Represent real-world things (people, products) [05:01:09]
    * Syntax: `const objectName = { key1: value1, key2: value2, ... };` [05:01:24]
    * **Properties:** Key-value pairs (what an object *has*) [05:00:54]
    * **Methods:** Functions belonging to an object (what an object *can do*) [05:00:54], [05:04:32]
    * Accessing properties: `objectName.propertyName` [05:02:26]
    * Calling methods: `objectName.methodName()` [05:05:20]
    * Methods can be function expressions or arrow functions (but `this` behaves differently) [05:05:56]
    * Example: `person` object with `firstName`, `lastName`, `age`, `isEmployed` properties and `sayHello`, `eat` methods [05:01:24]
* **`this` Keyword:** [05:07:40]
    * Reference to the object **where `this` is used** [05:07:46]
    * Depends on the immediate context [05:07:53]
    * Inside an object's method (defined with `function`), `this` refers to that object [05:09:02]
    * Allows methods to access the object's own properties (`this.propertyName`) [05:09:02]
    * Makes methods reusable across different objects of the same structure [05:10:12]
    * `this` outside of any object (in global scope) refers to the `window` object (in browsers) [05:10:51]
    * **Important:** `this` does **not** work as expected inside **arrow functions** used as methods; it refers to the `window` object instead [05:11:24]

---

## Chapter 26: Constructors & Classes

* **Problem:** Manually creating many similar objects is repetitive [05:12:19]
* **Constructors (Traditional):** [05:12:11]
    * Special function to define properties/methods for objects [05:12:11]
    * Uses `function` keyword, capitalized name convention (`function Car(...)`) [05:12:45]
    * Uses `this` keyword to assign properties based on parameters (`this.make = make`) [05:13:10]
    * Creates new objects using the `new` keyword (`const car1 = new Car(...)`) [05:13:46]
    * Example: `Car` constructor [05:12:45]
* **Classes (ES6):** [05:17:40]
    * More structured and cleaner way to work with objects (syntactic sugar over constructors) [05:17:40]
    * Syntax: `class ClassName { constructor(params) { // assignments } method1() {} method2() {} }` [05:18:21]
    * `constructor` method: Special method for initializing object properties [05:18:32]
    * Methods are defined directly within the class body (no `function` keyword needed) [05:19:01]
    * Still use `new` keyword to create instances (`const product1 = new Product(...)`) [05:19:31]
    * Example: `Product` class with `name`, `price` properties and `displayProduct`, `calculateTotal` methods [05:18:21]

---

## Chapter 27: Static Keyword, Inheritance & Super Keyword

* **Static Keyword:** [05:23:40]
    * Defines properties or methods that belong to the **class itself**, not to instances (objects) created from it [05:23:53]
    * Accessed via the class name: `ClassName.staticProperty`, `ClassName.staticMethod()` [05:24:30]
    * Do not need to create an object instance to use static members [05:24:50]
    * Example: `MathUtil` class with `static PI` property and `static getDiameter()`, `static getCircumference()`, `static getArea()` methods [05:24:08]
    * Example: `User` class with `static userCount` property and `static getUserCount()` method to track instances [05:27:32]
* **Inheritance:** [05:31:53]
    * Allows a new class (child/subclass) to inherit properties and methods from an existing class (parent/superclass) [05:31:53]
    * Promotes code reusability (DRY - Don't Repeat Yourself) [05:32:07], [05:38:41]
    * Uses the `extends` keyword: `class ChildClass extends ParentClass {}` [05:33:17]
    * Child class automatically gets parent's properties and methods [05:34:09]
    * Child classes can have their own unique properties and methods [05:36:10]
    * Example: `Animal` parent class with `alive` property, `eat()`, `sleep()` methods; `Rabbit`, `Fish`, `Hawk` child classes inheriting from `Animal` and adding unique methods (`run()`, `swim()`, `fly()`) [05:32:19]
* **Super Keyword:** [05:38:59]
    * Used in child classes to call the constructor or access methods of the parent (superclass) [05:38:59]
    * Similar to `this` (refers to current object), `super` refers to the parent object [05:39:05]
    * `super()`: **Must** be called in the child class constructor **before** using `this` if the child has its own constructor; calls the parent constructor [05:41:43]
    * Passes necessary arguments up to the parent constructor (`super(name, age)`) [05:42:58]
    * `super.methodName()`: Calls a method from the parent class [05:46:57]
    * Example: `Animal` constructor takes `name`, `age`; `Rabbit` constructor takes `name`, `age`, `runSpeed`, calls `super(name, age)`, then assigns `this.runSpeed` [05:42:29]
    * Example: `Rabbit`'s `run()` method calls `super.move(this.runSpeed)` to reuse/extend the parent's `move()` method [05:46:57]

---

## Chapter 28: Getters & Setters

* **Getters (`get`):** [05:48:22]
    * Special methods that make a property readable [05:48:22]
    * Accessed like a regular property (no parentheses `()`) [05:53:45]
    * Allows adding logic when reading a property (formatting, calculation) [05:53:35]
    * Syntax: `get propertyName() { return this._backingProperty; }` [05:52:37]
    * Example: `get width()` returning formatted width [05:52:37]
    * Example: `get area()` calculating and returning area [05:53:45]
* **Setters (`set`):** [05:48:22]
    * Special methods that make a property writable [05:48:22]
    * Called automatically when assigning a value to the property [05:50:05]
    * Allows validation or modification before assigning the value [05:48:28]
    * Syntax: `set propertyName(newValue) { // validation logic; this._backingProperty = newValue; }` [05:50:13]
    * Convention: Use a backing property (e.g., `_width`) to store the actual value to avoid infinite loops with the setter calling itself [05:50:46]
    * Example: `set width(newWidth)` validating `newWidth > 0` before assigning to `this._width` [05:50:13]
* Use Case: Input validation and controlled access/formatting of object properties [05:48:28]
* Example: `Rectangle` class with getters/setters for `width`, `height`, and getter for calculated `area` [05:48:44]
* Example: `Person` class with getters/setters for `firstName`, `lastName`, `age`, validating types and non-emptiness/non-negativity [05:55:36]

---

## Chapter 29: Destructuring

* **Destructuring:** [06:01:28]
    * Extracting values from arrays or properties from objects into distinct variables [06:01:34]
    * Convenient way to unpack values [06:01:41]
* **Array Destructuring (`[]`):** [06:01:49]
    * Syntax: `const [var1, var2, ...] = array;` [06:04:11]
    * Assigns elements based on position [06:04:11]
    * Use Case 1: Swapping variable values: `[a, b] = [b, a];` [06:01:57]
    * Use Case 2: Swapping array elements: `[colors[0], colors[4]] = [colors[4], colors[0]];` [06:02:43]
    * Use Case 3: Assigning elements to variables: `const [first, second, third] = colors;` [06:04:04]
    * Combining with Rest (`...`): Collects remaining elements into a new array: `const [first, second, ...rest] = colors;` [06:04:53]
* **Object Destructuring (`{}`):** [06:01:49]
    * Syntax: `const {prop1, prop2, ...} = object;` [06:06:24]
    * Assigns properties based on **name** (variable name must match property key) [06:06:24]
    * Use Case 1: Extracting properties into variables: `const {firstName, lastName, age, job} = person1;` [06:06:24]
    * Default Values: Provide a fallback if property doesn't exist: `const {job="Unemployed"} = person2;` [06:07:16]
    * Use Case 2: Destructuring in function parameters: `function displayPerson({firstName, lastName, age, job="Unemployed"}) { ... }` [06:07:44]

---

## Chapter 30: Nested Objects & Arrays of Objects

* **Nested Objects:** [06:10:07]
    * Objects inside other objects [06:10:14]
    * Represent more complex data structures [06:10:14]
    * Child object enclosed by parent object [06:10:23]
    * Example: `person` object containing an `address` object [06:11:55]
    * Accessing nested properties: `parentObject.childObject.propertyName` [06:13:26]
    * Iterating through nested object properties: `for (const prop in person.address) { console.log(person.address[prop]); }` [06:14:02]
    * Using classes with nested objects: `Person` class constructor creates a `new Address(...)` [06:14:44]
* **Arrays of Objects:** [06:19:25]
    * Arrays where each element is an object [06:19:25]
    * Common data structure [06:19:25]
    * Example: `fruits` array where each element is `{name: "...", color: "...", calories: ...}` [06:19:33]
    * Accessing properties: `arrayName[index].propertyName` [06:20:51]
    * Manipulating the array: `.push()`, `.pop()`, `.splice()` work as usual [06:21:46]
    * Using array methods with objects:
        * `.forEach()`: Iterate and access properties (`fruit.name`) [06:22:57]
        * `.map()`: Create new arrays of specific properties (`fruitNames = fruits.map(fruit => fruit.name)`) [06:23:34]
        * `.filter()`: Create new array based on property conditions (`yellowFruits = fruits.filter(fruit => fruit.color === "yellow")`) [06:24:47]
        * `.reduce()`: Find single object based on property (e.g., fruit with max calories) [06:26:33]

---

## Chapter 31: Sorting Arrays & Objects

* **`.sort()` Method (Recap & Details):** [06:29:24]
    * Sorts array elements **in place** [06:29:31]
    * Default sort is **lexicographic (string-based)**, not numerical [06:29:31]
    * Leads to incorrect results for numbers (e.g., `[1, 10, 2]` -> `[1, 10, 2]`) [06:30:19]
* **Sorting Numbers:** [06:30:46]
    * Requires a custom **compare function** passed to `.sort()` [06:30:53]
    * Compare function takes two arguments (`a`, `b`) representing elements being compared [06:31:07]
    * Ascending order: `(a, b) => a - b` [06:31:16]
    * Descending order: `(a, b) => b - a` [06:31:47]
* **Sorting Objects:** [06:32:02]
    * Sort based on a specific object property [06:32:02]
    * Use a compare function accessing the property:
        * Numerical property (ascending): `(a, b) => a.propertyName - b.propertyName` (e.g., `a.age - b.age`) [06:33:17]
        * Numerical property (descending): `(a, b) => b.propertyName - a.propertyName` (e.g., `b.gpa - a.gpa`) [06:34:03]
        * String property (ascending): `(a, b) => a.propertyName.localeCompare(b.propertyName)` (e.g., `a.name.localeCompare(b.name)`) [06:35:00]
        * String property (descending): `(a, b) => b.propertyName.localeCompare(a.propertyName)` [06:35:25]
    * Example: Sorting `people` array by `age`, `gpa`, `name` [06:33:17]

---

## Chapter 32: Shuffling Arrays

* **Shuffling Arrays:** [06:36:02]
    * Randomizing the order of elements [06:36:02]
* **Incorrect Method (Avoid):** Using `.sort(() => Math.random() - 0.5)` is **not truly random** and inefficient [06:36:44]
* **Correct Method: Fisher-Yates (Knuth) Shuffle Algorithm:** [06:37:16]
    * Iterate backwards through the array (from last element to second) [06:37:37]
    * For each element `i`, pick a random index `random` between 0 and `i` (inclusive) [06:38:24]
    * Swap the element at index `i` with the element at the random index `random` [06:39:01]
    * Implementation using a `shuffle` function with a `for` loop and destructuring for swapping [06:37:25]
    * Example: Shuffling a deck of cards array [06:36:18]

---

## Chapter 33: Date Objects

* **Date Objects:** [06:40:08]
    * Represent dates and times [06:40:14]
* **Creating Dates:**
    * `new Date()`: Current date and time [06:40:30]
    * `new Date(year, monthIndex, day, hours, minutes, seconds, ms)`: Specific date/time (month is 0-indexed) [06:41:04]
    * `new Date("YYYY-MM-DDTHH:mm:ssZ")`: Using ISO date string [06:41:53]
    * `new Date(millisecondsSinceEpoch)`: Milliseconds since Jan 1, 1970 UTC (Epoch time) [06:42:23]
* **Getting Components:**
    * `.getFullYear()`: Get the year (4 digits) [06:43:24]
    * `.getMonth()`: Get the month (0-11) [06:43:43]
    * `.getDate()`: Get the day of the month (1-31) [06:44:04]
    * `.getDay()`: Get the day of the week (0=Sunday, 6=Saturday) [06:45:18]
    * `.getHours()`: Get the hour (0-23) [06:44:23]
    * `.getMinutes()`: Get the minute (0-59) [06:44:53]
    * `.getSeconds()`: Get the second (0-59) [06:45:01]
    * `.getMilliseconds()`: Get the millisecond (0-999)
* **Setting Components:**
    * `.setFullYear(year)` [06:45:53]
    * `.setMonth(monthIndex)` [06:46:06]
    * `.setDate(day)` [06:46:15]
    * `.setHours(hour)` [06:46:23]
    * `.setMinutes(minute)` [06:46:37]
    * `.setSeconds(second)` [06:46:44]
* **Comparing Dates:** Can use comparison operators (`>`, `<`, `>=`, `<=`) directly on Date objects [06:46:53]

---

## Chapter 34: Closures

* **Closures:** [06:48:08]
    * A function defined inside another function (inner function) [06:48:15]
    * The inner function has access to the variables and scope of the outer function, even after the outer function has finished executing [06:48:15]
    * Allows for:
        * **Private Variables:** Variables in the outer scope are not accessible from outside [06:49:53]
        * **State Maintenance:** Inner functions can maintain and modify variables from the outer scope across multiple calls [06:50:30]
* Basic Example: `outer()` function with `message` variable and `inner()` function accessing `message` [06:48:49]
* State Maintenance Example:
    * Problem: Simple `increment()` function resets `count` each time [06:50:37]
    * Solution using Closure: `createCounter()` outer function holds `count`; returns an object with an `increment` method (the inner function) that modifies the outer `count`. The `count` persists between calls to the returned object's `increment` method. [06:51:22]
    * Adding `getCount` method to access the private `count` [06:54:15]
* Game Score Example: `createGame()` closure manages a private `score` variable, returning methods `increaseScore`, `decreaseScore`, `getScore` [06:55:13]

---

## Chapter 35: setTimeout & clearTimeout

* **`setTimeout(callback, delay)`:** [06:59:08]
    * Schedules a function (callback) to run **once** after a specified delay (in milliseconds) [06:59:13]
    * Asynchronous: Does not block other code execution [06:59:13]
    * Delay is approximate, not guaranteed precise [06:59:22]
    * Callback can be a function name, anonymous function, or arrow function [06:59:59]
    * Returns a **timeout ID** (a number) [07:00:59]
* **`clearTimeout(timeoutID)`:** [07:00:59]
    * Cancels a scheduled timeout before it executes [07:00:59]
    * Requires the timeout ID returned by `setTimeout` [07:00:59]
* Example: Scheduling an alert after 3 seconds [06:59:43]
* Example: Using buttons to start (`setTimeout`) and clear (`clearTimeout`) a timer [07:01:40]

---

## Chapter 36: Project 7: Digital Clock

* Project Goal: Display a continuously updating digital clock [07:05:21]
* HTML Structure: Nested divs (`clock-container` > `clock`) [07:05:29]
* CSS Styling:
    * Centering clock using Flexbox [07:06:22]
    * Styling clock text (monospace font, size, weight) [07:07:33]
    * Optional: Background image styling (`background-image`, `position`, `repeat`, `size`, `attachment`) [07:08:05]
    * Optional: Glass/blur effect (`backdrop-filter: blur(...)`, transparent `background-color`) [07:09:58]
* JavaScript Functionality:
    * `updateClock()` function: [07:11:22]
        * Get current time: `const now = new Date();` [07:11:36]
        * Extract hours, minutes, seconds using `.getHours()`, `.getMinutes()`, `.getSeconds()` [07:11:51]
        * Convert to 12-hour format (optional): [07:14:34]
            * Determine AM/PM (`meridiem = hours >= 12 ? "PM" : "AM";`) [07:14:41]
            * Convert hour using modulus (`hours = hours % 12 || 12;`) [07:15:10]
        * Pad numbers with leading zero (convert to string, use `.padStart(2, "0")`) [07:13:16]
        * Format time string using template literal [07:12:21]
        * Update clock element's `.textContent` [07:12:51]
    * Initial Call & Interval:
        * Call `updateClock()` once immediately [07:11:29]
        * Use `setInterval(updateClock, 1000)` to call `updateClock` every second [07:14:09]

---

## Chapter 37: Project 8: Stopwatch

* Project Goal: Create a functional stopwatch with start, stop, reset buttons [07:16:08]
* HTML Structure: H1, container div (`container` > `display` div + `controls` div with buttons) [07:16:20]
* CSS Styling: Styling body, H1, container, display, controls, and buttons (including `:hover`, `:active`, specific colors for each button) [07:18:09]
* JavaScript Functionality:
    * Variables: `display` element reference, `timer` (for interval ID), `startTime`, `elapsedTime`, `isRunning` boolean [07:24:34]
    * `start()` function: [07:25:50]
        * Check if `!isRunning` [07:26:00]
        * Calculate `startTime = Date.now() - elapsedTime` [07:26:17]
        * Start interval: `timer = setInterval(update, 10)` [07:26:50]
        * Set `isRunning = true` [07:27:22]
    * `stop()` function: [07:32:07]
        * Check if `isRunning` [07:32:16]
        * Clear interval: `clearInterval(timer)` [07:32:27]
        * Record final `elapsedTime = Date.now() - startTime` [07:32:38]
        * Set `isRunning = false` [07:32:50]
    * `reset()` function: [07:33:05]
        * Clear interval `clearInterval(timer)` [07:33:14]
        * Reset `startTime`, `elapsedTime` to 0 [07:33:27]
        * Set `isRunning = false` [07:33:27]
        * Reset `display.textContent` to "00:00:00:00" [07:33:41]
    * `update()` function: [07:25:50]
        * Calculate current `elapsedTime = Date.now() - startTime` [07:28:01]
        * Convert `elapsedTime` (milliseconds) into hours, minutes, seconds, milliseconds (using division, modulus, `Math.floor`) [07:28:17]
        * Format components with leading zeros (`.toString().padStart(2, "0")`) [07:31:14]
        * Update `display.textContent` [07:30:26]

---

## Chapter 38: ES6 Modules

* **Modules:** [07:34:19]
    * External files containing reusable code (variables, functions, classes) [07:34:19]
    * Import code into other JavaScript files [07:34:26]
    * Introduced in ECMAScript 2015 (ES6) [07:34:40]
* **Exporting:** [07:36:48]
    * Use the `export` keyword before declarations in the module file (`export const PI = ...;`, `export function getCircumference(...) {}`) [07:37:01]
* **Importing:** [07:37:10]
    * In the consuming file, use the `import` statement [07:37:10]
    * Syntax (Named Imports): `import { name1, name2, ... } from "./moduleFileName.js";` [07:37:19]
    * File path is relative to the importing file [07:37:27]
* **HTML Setup:**
    * **Crucial:** Add `type="module"` to the `<script>` tag that loads the main JavaScript file: `<script src="index.js" type="module"></script>` [07:35:15]
* Example: Creating `math_util.js` module with `PI`, `getCircumference`, `getArea`, `getVolume`; importing and using them in `index.js` [07:34:56]

---

## Chapter 39: Asynchronous Code

* **Synchronous Code:** [07:40:18]
    * Executes line by line, sequentially [07:40:25]
    * Waits for an operation to complete before moving to the next line [07:40:25]
    * Example: `console.log` tasks run in order [07:40:41]
* **Asynchronous Code:** [07:41:02]
    * Allows multiple operations to run concurrently without waiting [07:41:12]
    * Does **not** block the execution flow; program continues while async task runs [07:41:12]
    * Common with I/O operations, network requests, timers (`setTimeout`) [07:41:32]
    * Example: `setTimeout` task runs *after* subsequent synchronous tasks [07:41:48]
* **Handling Asynchronous Code:**
    * **Callbacks (Recap):** Pass a function to run after the async task completes [07:42:38]
    * **Promises (Preview):** Objects representing eventual completion/failure [07:42:38]
    * **Async/Await (Preview):** Syntactic sugar for working with promises [07:42:38]
    * Demonstrating callback solution to maintain order with asynchronous `setTimeout` tasks [07:42:48]

---

## Chapter 40: Error Handling (try, catch, finally, throw)

* **Errors:** [07:45:03]
    * Objects representing problems that occur during execution (e.g., `TypeError`, `ReferenceError`) [07:45:09]
    * Uncaught errors interrupt the program flow [07:46:02]
* **`try...catch` Statement:** [07:46:45]
    * Handles potential errors gracefully [07:46:45]
    * `try { // Code that might throw an error }`: Encloses the risky code [07:46:55]
    * `catch (error) { // Code to run if an error occurs }`: Catches the error object, allowing you to log it or handle it [07:47:18]
    * Prevents program interruption [07:47:35]
    * Use `console.error(error)` instead of `console.log(error)` for better visibility [07:47:48]
* **`finally` Block (Optional):** [07:48:02]
    * `finally { // Code that always runs }`: Executes regardless of whether an error occurred or not [07:48:10]
    * Used for cleanup (closing files/connections) [07:48:17]
* **`throw` Statement:** [07:51:36]
    * Manually create and throw your own error objects [07:51:36]
    * `throw new Error("Custom error message");` [07:51:47]
    * Useful for input validation or specific error conditions [07:51:47]
    * Thrown errors can be caught by a `catch` block [07:51:47]
* Example: Handling division by zero and non-numeric input using `try...catch` and `throw` [07:49:29]

---

## Chapter 41: Project 9: Calculator

* Project Goal: Create a basic calculator interface [07:54:08]
* HTML Structure (`<div id="calculator">`):
    * Display input (`<input id="display" readonly>`) [07:54:33]
    * Keys container (`<div id="keys">`) [07:54:56]
    * Buttons for numbers (0-9), operators (+, -, *, /), decimal (.), equals (=), clear (C) [07:55:02]
    * Buttons call JavaScript functions via `onclick`:
        * `appendToDisplay('char')` for numbers, operators, decimal [07:55:17]
        * `calculate()` for equals button [07:56:48]
        * `clearDisplay()` for clear button [07:57:02]
    * Operator buttons given a class (`operator-btn`) [08:03:52]
* CSS Styling:
    * Styling calculator container, display, keys (using `display: grid`), buttons (general, `:hover`, `:active`), and operator buttons (specific color) [07:57:12]
* JavaScript Functionality:
    * Get reference to `display` element [08:05:30]
    * `appendToDisplay(input)`: Appends input character to `display.value` [08:06:12]
    * `clearDisplay()`: Sets `display.value` to empty string `""` [08:07:11]
    * `calculate()`: [08:06:28]
        * Use `try...catch` to handle potential errors from invalid expressions [08:08:32]
        * Inside `try`: Evaluate the expression using `eval(display.value)` and set `display.value` to the result [08:07:34]
        * Inside `catch`: Set `display.value` to "Error" [08:08:47]
    * **Caution:** `eval()` can be a security risk if used with untrusted input, but is simple for this calculator example. [08:07:34]

---

## Chapter 42: DOM Introduction

* **DOM (Document Object Model):** [08:09:25]
    * JavaScript object representation of the HTML page [08:09:31]
    * Provides an API (Application Programming Interface) to interact with the page [08:09:38]
    * Browser constructs the DOM when loading HTML [08:09:43]
    * Tree-like structure of elements (HTML -> HEAD, BODY -> H1, DIV, etc.) [08:09:46]
* **`document` Object:** [08:10:05]
    * Entry point to access the DOM [08:10:05]
    * Contains properties and methods to select and manipulate elements [08:10:23]
    * `console.log(document)` shows HTML structure [08:10:34]
    * `console.dir(document)` shows object properties/methods [08:10:44]
* **Manipulating the DOM:**
    * Accessing/Changing properties: `document.title = "New Title";` [08:11:01]
    * Changing styles: `document.body.style.backgroundColor = "black";` [08:11:34]
    * Selecting elements (e.g., `document.getElementById()`) and changing their content (`.textContent`) [08:12:16]

---

## Chapter 43: Element Selectors

* **Element Selectors:** Methods to target and manipulate HTML elements from the DOM [08:14:32]
* **`document.getElementById("idName")`:** [08:15:08]
    * Selects **one** element with the specified ID [08:15:08]
    * Returns the **element object** or `null` if not found [08:17:11]
    * Fastest selector [08:17:11]
* **`document.getElementsByClassName("className")`:** [08:17:23]
    * Selects **all** elements with the specified class name [08:17:23]
    * Returns a **live HTMLCollection** (array-like, limited methods, updates automatically) [08:17:30], [08:29:14]
    * Access elements by index (e.g., `fruits[0]`) [08:19:11]
    * Iterate with `for...of` loop [08:19:53]
    * Cannot use `.forEach()` directly; convert to array first: `Array.from(collection).forEach(...)` [08:20:30]
* **`document.getElementsByTagName("tagName")`:** [08:21:51]
    * Selects **all** elements with the specified tag name (e.g., "h4", "li") [08:21:51]
    * Returns a **live HTMLCollection** [08:23:03]
    * Similar usage to `getElementsByClassName` [08:23:38]
* **`document.querySelector("cssSelector")`:** [08:27:14]
    * Selects the **first** element matching the specified CSS selector (e.g., "#id", ".class", "tag", "tag.class[attribute=value]") [08:27:14]
    * Returns the **element object** or `null` if not found [08:27:21]
    * Very versatile [08:27:21]
* **`document.querySelectorAll("cssSelector")`:** [08:29:05]
    * Selects **all** elements matching the specified CSS selector [08:29:05]
    * Returns a **static NodeList** (array-like, has `.forEach()`, does **not** update automatically) [08:29:05]
    * Can use `.forEach()` directly [08:30:44]
* Personal Preference: Often use `getElementById` and `querySelectorAll` [08:31:33]

---

## Chapter 44: DOM Navigation

* **DOM Navigation:** Traversing the structure (tree) of the HTML document [08:32:11]
* **Node Relationships:** Parent, Child, Sibling [08:32:11]
* **Properties for Navigation:** (Focus on `Element` versions to skip text/comment nodes)
    * `.firstElementChild`: Selects the first child **element** of a parent [08:33:37]
    * `.lastElementChild`: Selects the last child **element** of a parent [08:36:40]
    * `.nextElementSibling`: Selects the next sibling **element** [08:39:09]
    * `.previousElementSibling`: Selects the previous sibling **element** [08:42:13]
    * `.parentElement`: Selects the direct parent **element** [08:44:00]
    * `.children`: Returns a **live HTMLCollection** of all direct child **elements** [08:45:07]
* Example Setup: Unordered lists (fruits, vegetables, desserts) with list items [08:32:36]
* Demonstrations:
    * Selecting first/last children of lists [08:34:31], [08:37:13]
    * Using `querySelectorAll` and `.forEach` to select first/last children of *all* lists [08:35:23], [08:38:01]
    * Selecting next/previous siblings of list items and lists themselves [08:40:13], [08:42:42]
    * Selecting the parent element of a list item [08:44:14]
    * Selecting all children of a list and iterating through them [08:45:21]

---

## Chapter 45: Adding & Changing HTML Elements

* **Creating Elements:** [08:47:36]
    * `document.createElement("tagName")`: Creates a new element object (e.g., "h1", "li") [08:48:47]
* **Modifying Elements:**
    * `.textContent`: Set text content [08:49:12]
    * `.id`: Set ID attribute [08:50:12]
    * `.style.property`: Set CSS styles [08:50:41]
    * Other attributes can often be set directly (e.g., `img.src = ...`)
* **Appending Elements (Adding to DOM):**
    * Select the **parent** element where you want to add the new element [08:49:32]
    * `.append(newElement)`: Adds the `newElement` as the **last child** of the parent [08:49:42]
    * `.prepend(newElement)`: Adds the `newElement` as the **first child** of the parent [08:49:55]
    * `.insertBefore(newElement, referenceElement)`: Adds `newElement` **before** the `referenceElement` within the same parent [08:52:56]
* **Removing Elements:** [08:55:37]
    * Select the **parent** element containing the element to remove [08:56:18]
    * `.removeChild(elementToRemove)`: Removes the specified child element [08:55:49]
* Examples:
    * Creating an H1, styling it, appending/prepending to body or specific divs [08:48:47]
    * Inserting H1 between existing divs using `.insertBefore()` [08:52:56]
    * Creating a list item ("coconut"), styling it, appending/prepending/inserting into an ordered list [08:58:01]
    * Removing created elements [08:55:37], [09:02:37]

---

## Chapter 46: Events: Mouse Events & Event Listeners

* **Event Listeners:** [09:03:11]
    * Listen for specific events (user actions, browser actions) to make pages interactive [09:03:18]
    * Method: `element.addEventListener(eventType, callback)` [09:03:36]
        * `eventType`: String specifying the event (e.g., "click", "mouseover") [09:03:36]
        * `callback`: Function to execute when event occurs (can be function name, anonymous function, or arrow function) [09:03:36], [09:08:08]
* **Event Object:** [09:05:58]
    * Automatically passed as an argument to the callback function [09:05:58]
    * Contains information about the event (type, target, timestamp, coordinates, etc.) [09:05:58]
    * `event.target`: Refers to the HTML element that triggered the event [09:07:10]
* **Mouse Events:**
    * `"click"`: User clicks the element [09:03:23]
    * `"mouseover"`: Cursor moves onto the element [09:03:23]
    * `"mouseout"`: Cursor moves off the element [09:03:23]
* Example: Changing box background/text on click, mouseover, mouseout using `addEventListener` and accessing `event.target` [09:05:02]
* Example: Attaching listeners to a button that modifies a separate box element [09:11:30]

---

## Chapter 47: Events: Key Events

* **Key Events:** Listen for keyboard interactions [09:13:37]
* Attach listener usually to `document` or specific input fields [09:14:16]
* Event Types:
    * `"keydown"`: Key is pressed down (fires repeatedly if held) [09:14:00]
    * `"keyup"`: Key is released [09:14:00]
    * `"keypress"` (Avoid - deprecated/inconsistent browser support) [09:14:00]
* **Keyboard Event Object:** [09:15:10]
    * Passed to callback function [09:15:10]
    * `event.key`: String representing the key pressed (e.g., "Q", " ", "ArrowUp") [09:15:18]
    * `event.code`: String representing physical key code (e.g., "KeyQ", "Space", "ArrowUp")
    * Other properties: `altKey`, `ctrlKey`, `shiftKey` (booleans) [09:15:25]
* Example 1: Changing box text/color on keydown and reverting on keyup [09:16:51]
* Example 2: Moving a box element using arrow keys [09:19:39]
    * Check `event.key.startsWith("Arrow")` to filter for arrow keys [09:20:55]
    * Use `switch (event.key)` to determine direction [09:21:16]
    * Update X/Y coordinate variables [09:21:40]
    * Update element's `style.top` and `style.left` properties (requires `position: relative` or `absolute` on element) [09:22:33]
    * `event.preventDefault()`: Prevent default browser behavior associated with the key (e.g., arrow keys scrolling the page) [09:23:27]

---

## Chapter 48: Show/Hide HTML Elements

* **Methods to Show/Hide:** [09:24:54]
* **Method 1: `display` Property:** [09:27:15]
    * `element.style.display = "none";`: Hides element, removes it from layout flow (space collapses) [09:27:15]
    * `element.style.display = "block"` (or `"flex"`, `"inline"`, etc.): Shows element [09:28:08]
    * Effect: Elements around it may shift [09:28:58]
* **Method 2: `visibility` Property:** [09:29:16]
    * `element.style.visibility = "hidden";`: Hides element, but **reserves its space** in the layout [09:29:16]
    * `element.style.visibility = "visible";`: Shows element [09:29:38]
    * Effect: Elements around it do not shift [09:29:44]
* Example: Toggling image visibility using a button and an `if` statement checking the current style property [09:26:09]

---

## Chapter 49: NodeLists

* **NodeList (Recap):** [09:30:05]
    * Collection of HTML elements, often created using `document.querySelectorAll()` [09:30:08]
    * **Static:** Does NOT automatically update if the DOM changes (unlike HTMLCollection) [09:30:25]
    * Array-like: Has `.length`, can access elements by index (`nodeList[i]`) [09:30:08]
    * Has `.forEach()` method (unlike HTMLCollection) [09:30:15]
    * Does NOT have `.map()`, `.filter()`, `.reduce()` (convert to array if needed: `Array.from(nodeList)`) [09:30:15]
* Example Setup: Multiple buttons with a common class "my-buttons" [09:30:39]
* Using `.forEach()` with NodeLists:
    * Changing styles of all elements [09:33:04]
    * Adding event listeners to all elements [09:34:27], [09:35:46], [09:36:51]
* Adding Elements to DOM vs NodeList:
    * Creating a new button and appending to DOM [09:37:19]
    * Original NodeList **does not** contain the new button [09:39:15]
    * Need to re-run `querySelectorAll()` to get an updated NodeList including the new element [09:39:42]
* Removing Elements from DOM vs NodeList:
    * Adding click listener to remove button from DOM (`event.target.remove()`) [09:40:42]
    * Original NodeList **still contains** the removed button [09:41:55]
    * Need to re-run `querySelectorAll()` to get updated NodeList excluding the removed element [09:42:16]

---

## Chapter 50: ClassList Property

* **`element.classList`:** [09:43:28]
    * Property providing access to an element's list of CSS classes [09:43:28]
    * Returns a `DOMTokenList` object [09:43:28]
* **`classList` Methods:**
    * `.add("className")`: Adds the specified class [09:45:33]
    * `.remove("className")`: Removes the specified class [09:46:06]
    * `.toggle("className")`: Adds class if not present, removes if present [09:48:24]
    * `.replace("oldClass", "newClass")`: Replaces an existing class with a new one [09:48:53]
    * `.contains("className")`: Returns `true` or `false` indicating if the class is present [09:50:30]
* Use Case: Dynamically applying/removing CSS styles based on events or state changes [09:43:35]
* Example 1 (Single Button):
    * Defining CSS classes `.enabled`, `.hover`, `.disabled` [09:44:45]
    * Adding `.enabled` class initially [09:49:36]
    * Adding/removing (or toggling) `.hover` class on `mouseover`/`mouseout` events [09:47:22]
    * Replacing `.enabled` with `.disabled` on `click` event [09:49:44]
    * Using `.contains()` within click handler to check state [09:50:47]
* Example 2 (Multiple Buttons using NodeList):
    * Applying methods to all buttons using `buttons.forEach(button => button.classList.add(...))` etc. [09:54:17]

---

## Chapter 51: Project 10: Rock Paper Scissors Game

* Project Goal: Functional Rock Paper Scissors game against the computer [09:59:18]
* HTML Structure:
    * H1 title [09:59:32]
    * Choice buttons (Rock, Paper, Scissors emojis) calling `playGame('choice')` onclick [09:59:45]
    * Divs to display player choice, computer choice, and result (with IDs `playerDisplay`, `computerDisplay`, `resultDisplay`) [10:01:05]
    * Divs/Spans for score display (IDs `playerScoreDisplay`, `computerScoreDisplay`) [10:14:42]
* CSS Styling: Styling body, title, choice buttons (including `:hover`), display texts, result text, scores [10:02:07]
    * Defining `.greenText` and `.redText` classes for win/loss result [10:12:37]
* JavaScript Functionality:
    * Constants: `choices` array [`rock`, `paper`, `scissors`], element references (displays, scores) [10:05:57]
    * Variables: `playerScore`, `computerScore` [10:17:02]
    * `playGame(playerChoice)` function: [10:07:03]
        * Get `computerChoice`: Random selection from `choices` array [10:07:29]
        * Determine `result`:
            * Check for tie (`playerChoice === computerChoice`) [10:08:55]
            * Else use `switch (playerChoice)` with nested ternary operators to check win/loss conditions based on `computerChoice` [10:09:23]
        * Update display elements (`playerDisplay`, `computerDisplay`, `resultDisplay`) `.textContent` [10:11:23]
        * Update result display color:
            * Remove previous `.greenText`, `.redText` classes [10:14:12]
            * Use `switch (result)` to add `.greenText` for "You Win!" or `.redText` for "You Lose!" [10:13:13]
        * Update score:
            * Increment `playerScore` or `computerScore` based on result within the result switch [10:17:13]
            * Update score display elements' `.textContent` [10:17:27]

---

## Chapter 52: Project 11: Image Slider

* Project Goal: Create an automatic and manually navigable image slider [10:18:18]
* Prerequisites: 3+ images [10:18:18]
* HTML Structure:
    * Outer container (`<div class="slider">`) [10:18:34]
    * Inner slides container (`<div class="slides">`) [10:18:42]
    * Image elements (`<img class="slide" src="..." alt="...">`) for each image [10:18:51]
    * Previous/Next buttons (`<button class="prev" onclick="prevSlide()">`, `<button class="next" onclick="nextSlide()">`) with arrow characters (&amp;#10094; / &amp;#10095;) [10:19:54]
* CSS Styling:
    * `.slider`: `position: relative`, `overflow: hidden` [10:21:22]
    * `.slider img`: `width: 100%`, `display: none` (initially hide all) [10:21:48]
    * `.displaySlide` class: `display: block` (class to show the active slide) [10:24:01]
    * Buttons (`.prev`, `.next`): `position: absolute`, positioning/styling [10:30:34]
    * Fade Animation (`@keyframes fade`, applied via `animation` properties on `.displaySlide`) [10:32:46]
* JavaScript Functionality:
    * Get NodeList of slides: `const slides = document.querySelectorAll(".slides img");` [10:22:11]
    * Variables: `slideIndex` (current index), `intervalId` (for `setInterval`) [10:22:31]
    * `initializeSlider()`: [10:22:56]
        * Check if `slides.length > 0` [10:26:01]
        * Show first slide: Add `.displaySlide` class to `slides[slideIndex]` [10:23:33]
        * Start automatic sliding: `intervalId = setInterval(nextSlide, 5000)` [10:25:03]
    * `showSlide(index)`: [10:23:11]
        * Handle index wrapping (if index goes beyond bounds, reset to 0 or last index) [10:28:09]
        * Update `slideIndex` variable [10:28:09]
        * Remove `.displaySlide` from all slides using `forEach` [10:26:46]
        * Add `.displaySlide` to `slides[slideIndex]` [10:27:33]
    * `prevSlide()`: [10:23:20]
        * Clear automatic interval: `clearInterval(intervalId)` [10:30:03]
        * Decrement `slideIndex` [10:29:31]
        * Call `showSlide(slideIndex)` [10:29:33]
    * `nextSlide()`: [10:23:20]
        * Increment `slideIndex` [10:26:30]
        * Call `showSlide(slideIndex)` [10:26:33]
    * Initial Setup: Use `document.addEventListener("DOMContentLoaded", initializeSlider);` to start after HTML loads [10:24:29]

---

## Chapter 53: Callback Hell

* **Callback Hell:** [10:34:03]
    * Situation where callbacks are nested deeply within other callbacks [10:34:08]
    * Code becomes difficult to read and maintain (pyramid shape) [10:34:16]
    * Older pattern for handling asynchronous operations [10:34:28]
* Example: Simulating asynchronous tasks (`task1` to `task4`) using `setTimeout` [10:35:47]
    * Running them sequentially without callbacks results in incorrect order [10:36:42]
    * Achieving correct order requires nesting: `task1(() => { task2(() => { task3(() => { task4(() => {...}); }); }); });` [10:43:01]
* Modern Alternatives: Promises, Async/Await (discussed next) help avoid callback hell [10:34:28]

---

## Chapter 54: Promises

* **Promises:** [10:39:49]
    * Objects representing the eventual completion (or failure) of an asynchronous operation [10:39:56]
    * Manages async operations like fetching data, file access, etc. [10:39:56]
    * States:
        * **Pending:** Initial state, operation not yet complete. [10:40:17]
        * **Fulfilled (Resolved):** Operation completed successfully. [10:40:17]
        * **Rejected:** Operation failed. [10:40:17]
* **Creating a Promise:** [10:40:30]
    * `new Promise((resolve, reject) => { // Async code... if (success) { resolve(value); } else { reject(error); } });` [10:44:08]
    * `resolve(value)`: Called on success, passing the result value. [10:44:56]
    * `reject(error)`: Called on failure, passing an error reason. [10:49:02]
* **Consuming a Promise:**
    * `.then(onFulfilled)`: Attaches a callback function that runs when the promise is **resolved**. Receives the resolved value as an argument. [10:46:24]
    * `.catch(onRejected)`: Attaches a callback function that runs when the promise is **rejected**. Receives the rejection reason (error) as an argument. [10:50:53]
    * **Chaining `.then()`:** Allows running asynchronous operations sequentially without deep nesting. Return a new promise from within a `.then()` callback to chain. [10:47:01]
* Example: Refactoring the asynchronous chore functions (walk dog, clean kitchen, take out trash) to return Promises instead of using callbacks [10:44:08]
* Example: Consuming the chore promises using `.then()` chaining and `.catch()` for error handling [10:46:08]

---

## Chapter 55: Async / Await

* **Async/Await:** [10:52:26]
    * Keywords providing syntactic sugar for working with Promises [10:52:31]
    * Make asynchronous code look and behave more like synchronous code [10:52:31]
* **`async` Keyword:** [10:52:45]
    * Placed before a function declaration (`async function myFunc() {}`) [10:53:49]
    * Makes the function automatically return a Promise [10:52:37]
    * If the function returns a value, the promise resolves with that value.
    * If the function throws an error, the promise rejects with that error.
* **`await` Keyword:** [10:53:15]
    * **Can only be used inside an `async` function** [10:55:43]
    * Placed before a Promise (`await promise;`) [10:54:09]
    * Pauses the execution of the `async` function until the Promise settles (resolves or rejects) [10:54:09]
    * If the Promise resolves, `await` returns the resolved value [10:54:17]
    * If the Promise rejects, `await` throws the rejection reason (error) [10:55:52]
* **Error Handling:** Use standard `try...catch` blocks within `async` functions to handle rejected Promises from `await` expressions [10:56:07]
* Example: Refactoring the promise-based chore execution using an `async function doChores()` with `await` and `try...catch` [10:53:49]

---

## Chapter 56: JSON (JavaScript Object Notation)

* **JSON:** [10:57:01]
    * JavaScript Object Notation [10:57:01]
    * Data interchange format (text-based) [10:57:09]
    * Used for exchanging data between server and web app (APIs) [10:57:16]
    * Human-readable [10:57:16]
* **JSON Syntax Rules:**
    * Data is in key/value pairs (like JS objects).
    * Keys **must** be strings in double quotes (`"key"`).
    * Values can be string (in double quotes), number, boolean, array, or another JSON object.
    * Data is separated by commas.
    * Objects use curly braces `{}`. [10:58:16]
    * Arrays use square brackets `[]`. [10:57:43]
* Examples:
    * `names.json`: Array of strings [10:57:43]
    * `person.json`: Single object with various value types (string, number, boolean, array) [10:58:16]
    * `people.json`: Array of objects [10:59:18]
* **Working with JSON in JavaScript:**
    * **`JSON.stringify(jsObjectOrArray)`:** Converts a JavaScript object or array into a JSON **string** [11:00:30]
    * **`JSON.parse(jsonString)`:** Converts a JSON **string** into a JavaScript object or array [11:02:30]
* **Fetching JSON Files:** [11:04:15]
    * Use the `fetch()` API [11:04:15]
    * `fetch("fileName.json")`: Returns a Promise resolving to a Response object [11:04:29]
    * `response.json()`: Method on the Response object that reads the body and parses it as JSON (also returns a Promise) [11:04:57]
    * Chain `.then()` to access the parsed JavaScript data [11:05:00]
    * Handle errors with `.catch()` [11:06:18]

---

## Chapter 57: Fetch API

* **`fetch()` Function:** [11:07:13]
    * Modern standard for making network requests (HTTP requests) in JavaScript [11:07:24]
    * Used to fetch resources (JSON data, images, files, etc.) from APIs or servers [11:07:30]
    * Simplifies asynchronous data fetching [11:07:39]
    * Promise-based (returns a Promise) [11:09:15]
* **Basic Usage (GET Request):**
    * `fetch(url)`: Takes the URL of the resource as an argument [11:08:21]
    * Returns a Promise that resolves to a `Response` object [11:09:15]
* **`Response` Object:** [11:09:51]
    * Represents the response to a request.
    * Properties:
        * `ok`: Boolean indicating if request was successful (status code 200-299) [11:10:05]
        * `status`: HTTP status code (e.g., 200, 404) [11:09:59]
        * `statusText`: Status message (e.g., "OK", "Not Found")
        * `url`: URL of the response [11:10:11]
    * Methods (return Promises):
        * `.json()`: Parses response body as JSON [11:10:17]
        * `.text()`: Reads response body as text [11:10:17]
        * `.blob()`: Reads response body as a Blob (binary data) [11:10:17]
        * `.arrayBuffer()`: Reads response body as an ArrayBuffer [11:10:17]
* **Handling the Response:**
    * Chain `.then()` after `fetch()` to access the `Response` object [11:09:29]
    * **Check `response.ok`**: If `false`, throw an error to handle non-successful responses (like 404) [11:12:05]
    * Call appropriate method (e.g., `response.json()`) to read the body [11:12:29]
    * Chain another `.then()` to access the parsed data (e.g., the JSON object) [11:10:38]
    * Use `.catch()` at the end to handle network errors or errors thrown manually [11:09:25]
* **Using with Async/Await:** [11:13:42]
    * Wrap `fetch` call in an `async` function [11:13:42]
    * Use `await` before `fetch(url)` to get the `Response` object [11:14:20]
    * Check `response.ok` and `throw` if necessary [11:14:55]
    * Use `await` before `response.json()` (or other body-reading methods) to get the data [11:15:23]
    * Use `try...catch` for error handling [11:14:00]
* Example Project: Fetching Pokémon data (name, ID, sprites) from PokéAPI based on user input [11:07:13]

---

## Chapter 58: Project 12: Weather App

* Project Goal: Fetch and display weather data for a user-input city using OpenWeatherMap API [11:21:24]
* Prerequisites: OpenWeatherMap API Key [11:21:34]
* HTML Structure:
    * Form (`<form class="weather-form">`) with city input (`<input class="city-input">`) and submit button (`<button type="submit">`) [11:22:18]
    * Card div (`<div class="card">`) to display weather info (initially `display: none`) [11:23:18]
* CSS Styling: Styling body, form, input, button, card (using `linear-gradient`, `box-shadow`, Flexbox), and elements inside card (city, temp, humidity, description, emoji, error message) [11:25:24]
* JavaScript Functionality:
    * Get references to form, input, card, and store API key [11:35:25]
    * Add `submit` event listener to the form: [11:36:55]
        * Mark callback as `async` [11:42:13]
        * `event.preventDefault()` [11:38:27]
        * Get `city` from input value [11:38:44]
        * If `city` exists:
            * Use `try...catch` for error handling [11:41:27]
            * `const weatherData = await getWeatherData(city);` [11:41:51]
            * `displayWeatherInfo(weatherData);` [11:42:26]
        * Else (no city):
            * `displayError("Please enter a city");` [11:39:06]
    * `async getWeatherData(city)` function: [11:37:27]
        * Construct API URL using template string, city, and API key [11:42:57]
        * `const response = await fetch(apiUrl);` [11:43:55]
        * Check `!response.ok`, throw error if not ok [11:44:56]
        * Return `await response.json();` [11:45:09]
    * `displayWeatherInfo(data)` function: [11:37:37]
        * Destructure needed info from `data` object (`name`, `main.temp`, `main.humidity`, `weather[0].description`, `weather[0].id`) [11:46:27]
        * Reset card content (`card.textContent = ""`) and make visible (`card.style.display = "flex"`) [11:48:05]
        * Create elements dynamically (`document.createElement`) for city, temp, humidity, description, emoji [11:48:46]
        * Set `.textContent` for each element (format temperature from Kelvin to C/F, add units/labels) [11:49:56]
        * Add appropriate CSS classes using `.classList.add()` [11:50:32]
        * Append elements to the card (`card.appendChild()`) [11:50:13]
        * Call `getWeatherEmoji(weatherId)` to get emoji [11:54:52]
    * `getWeatherEmoji(weatherId)` function: [11:37:57]
        * Use `switch (true)` based on weather ID ranges (from OpenWeatherMap docs) to return appropriate emoji [11:56:03]
    * `displayError(message)` function: [11:38:06]
        * Create error paragraph element [11:39:38]
        * Set `.textContent` and add `.error-display` class [11:39:46]
        * Reset card content, make card visible, append error message [11:40:19]