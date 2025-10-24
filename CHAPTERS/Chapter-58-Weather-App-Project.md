# Chapter 58: Weather App Project (Final Project)

---

## Overview
Build a complete Weather Application using everything you've learned - fetch API, async/await, DOM manipulation, and more!

---

## 58.1 Project Overview



**What we're building:**
- Weather app that fetches real-time data
- Search by city name
- Display temperature, conditions, humidity, wind speed
- Weather icons
- Error handling for invalid cities
- Responsive design

**Technologies:**
- HTML5
- CSS3
- JavaScript (ES6+)
- OpenWeatherMap API
- Fetch API
- Async/Await



---

## 58.2 Getting API Key



1. Go to [OpenWeatherMap](https://openweathermap.org/api)
2. Sign up for free account
3. Get your API key from dashboard
4. Wait 10-15 minutes for activation

**API Endpoint:**
```
https://api.openweathermap.org/data/2.5/weather?q={city}&appid={API_KEY}&units=metric
```



---

## 58.3 Project Structure



```
weather-app/
│
├── index.html
├── style.css
└── script.js
```

---

## 58.4 HTML Structure



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <div class="weather-app">
            <h1>Weather App</h1>
            
            <!-- Search Form -->
            <form id="weatherForm">
                <input 
                    type="text" 
                    id="cityInput" 
                    placeholder="Enter city name..."
                    required
                >
                <button type="submit">Get Weather</button>
            </form>
            
            <!-- Weather Display -->
            <div id="weatherDisplay" class="weather-display hidden">
                <div class="weather-icon">
                    <img id="weatherIcon" src="" alt="Weather Icon">
                </div>
                
                <div class="city-name">
                    <h2 id="cityName"></h2>
                    <p id="country"></p>
                </div>
                
                <div class="temperature">
                    <h1 id="temp"></h1>
                    <p id="description"></p>
                </div>
                
                <div class="weather-details">
                    <div class="detail">
                        <span class="label">Feels Like</span>
                        <span id="feelsLike" class="value"></span>
                    </div>
                    
                    <div class="detail">
                        <span class="label">Humidity</span>
                        <span id="humidity" class="value"></span>
                    </div>
                    
                    <div class="detail">
                        <span class="label">Wind Speed</span>
                        <span id="windSpeed" class="value"></span>
                    </div>
                    
                    <div class="detail">
                        <span class="label">Pressure</span>
                        <span id="pressure" class="value"></span>
                    </div>
                </div>
            </div>
            
            <!-- Error Message -->
            <div id="errorDisplay" class="error-display hidden">
                <p id="errorMessage"></p>
            </div>
            
            <!-- Loading Spinner -->
            <div id="loading" class="loading hidden">
                <div class="spinner"></div>
                <p>Loading weather data...</p>
            </div>
        </div>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```



---

## 58.5 CSS Styling



```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.container {
    width: 100%;
    max-width: 500px;
}

.weather-app {
    background: rgba(255, 255, 255, 0.95);
    border-radius: 20px;
    padding: 40px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
}

h1 {
    text-align: center;
    color: #333;
    margin-bottom: 30px;
    font-size: 2rem;
}

/* Search Form */
#weatherForm {
    display: flex;
    gap: 10px;
    margin-bottom: 30px;
}

#cityInput {
    flex: 1;
    padding: 15px;
    border: 2px solid #ddd;
    border-radius: 10px;
    font-size: 1rem;
    outline: none;
    transition: border-color 0.3s;
}

#cityInput:focus {
    border-color: #667eea;
}

button {
    padding: 15px 30px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    border-radius: 10px;
    font-size: 1rem;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
}

button:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
}

button:active {
    transform: translateY(0);
}

/* Weather Display */
.weather-display {
    text-align: center;
}

.weather-icon img {
    width: 120px;
    height: 120px;
    margin: 20px 0;
}

.city-name h2 {
    font-size: 2rem;
    color: #333;
    margin-bottom: 5px;
}

.city-name p {
    color: #666;
    font-size: 1.1rem;
}

.temperature h1 {
    font-size: 4rem;
    color: #667eea;
    margin: 20px 0 10px;
}

.temperature p {
    font-size: 1.3rem;
    color: #666;
    text-transform: capitalize;
    margin-bottom: 30px;
}

/* Weather Details */
.weather-details {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
    margin-top: 30px;
}

.detail {
    background: #f8f9fa;
    padding: 20px;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.detail .label {
    color: #666;
    font-size: 0.9rem;
    text-transform: uppercase;
    letter-spacing: 1px;
}

.detail .value {
    color: #333;
    font-size: 1.3rem;
    font-weight: bold;
}

/* Error Display */
.error-display {
    background: #fee;
    border: 2px solid #fcc;
    border-radius: 10px;
    padding: 20px;
    text-align: center;
}

.error-display p {
    color: #c33;
    font-size: 1.1rem;
}

/* Loading Spinner */
.loading {
    text-align: center;
    padding: 40px;
}

.spinner {
    width: 50px;
    height: 50px;
    border: 5px solid #f3f3f3;
    border-top: 5px solid #667eea;
    border-radius: 50%;
    margin: 0 auto 20px;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

.loading p {
    color: #666;
    font-size: 1.1rem;
}

/* Hidden class */
.hidden {
    display: none;
}

/* Responsive */
@media (max-width: 500px) {
    .weather-app {
        padding: 20px;
    }
    
    h1 {
        font-size: 1.5rem;
    }
    
    .temperature h1 {
        font-size: 3rem;
    }
    
    .weather-details {
        grid-template-columns: 1fr;
    }
}
```



---

## 58.6 JavaScript - Setup



```javascript
// API Configuration
const API_KEY = "YOUR_API_KEY_HERE"; // Replace with your actual API key
const API_URL = "https://api.openweathermap.org/data/2.5/weather";

// Get DOM elements
const weatherForm = document.getElementById("weatherForm");
const cityInput = document.getElementById("cityInput");
const weatherDisplay = document.getElementById("weatherDisplay");
const errorDisplay = document.getElementById("errorDisplay");
const loading = document.getElementById("loading");

// Weather data elements
const cityName = document.getElementById("cityName");
const country = document.getElementById("country");
const temp = document.getElementById("temp");
const description = document.getElementById("description");
const weatherIcon = document.getElementById("weatherIcon");
const feelsLike = document.getElementById("feelsLike");
const humidity = document.getElementById("humidity");
const windSpeed = document.getElementById("windSpeed");
const pressure = document.getElementById("pressure");
const errorMessage = document.getElementById("errorMessage");
// Output: All elements and variables initialized, ready for event handling
```



---

## 58.7 Event Listener



```javascript
// Form submit event
weatherForm.addEventListener("submit", async (event) => {
    event.preventDefault();
    
    const city = cityInput.value.trim();
    
    if (city) {
        await fetchWeather(city);
    }
});
// Output: Listens for form submission and calls fetchWeather with entered city name
```



---

## 58.8 Fetch Weather Function



```javascript
async function fetchWeather(city) {
    try {
        // Show loading, hide others
        showLoading();
        
        // Build API URL
        const url = `${API_URL}?q=${city}&appid=${API_KEY}&units=metric`;
        
        // Fetch weather data
        const response = await fetch(url);
        
        // Check if response is OK
        if (!response.ok) {
            if (response.status === 404) {
                throw new Error("City not found. Please check the spelling.");
            } else if (response.status === 401) {
                throw new Error("Invalid API key. Please check your configuration.");
            } else {
                throw new Error("Failed to fetch weather data. Please try again.");
            }
        }
        
        // Parse JSON
        const data = await response.json();
        // Output: Weather data object {name, sys, main, weather, wind, ...}
        
        // Display weather
        displayWeather(data);
        
    } catch (error) {
        displayError(error.message);
        // Output: Error message displayed to user
    }
}
```



---

## 58.9 Display Weather Function



```javascript
function displayWeather(data) {
    // Hide loading and error
    hideLoading();
    errorDisplay.classList.add("hidden");
    
    // Extract data
    const { 
        name, 
        sys: { country: countryCode },
        main: { temp: temperature, feels_like, humidity: humidityValue, pressure: pressureValue },
        weather,
        wind: { speed }
    } = data;
    
    // Update DOM
    cityName.textContent = name;
    country.textContent = countryCode;
    temp.textContent = `${Math.round(temperature)}°C`;
    description.textContent = weather[0].description;
    feelsLike.textContent = `${Math.round(feels_like)}°C`;
    humidity.textContent = `${humidityValue}%`;
    windSpeed.textContent = `${speed} m/s`;
    pressure.textContent = `${pressureValue} hPa`;
    
    // Weather icon
    const iconCode = weather[0].icon;
    weatherIcon.src = `https://openweathermap.org/img/wn/${iconCode}@2x.png`;
    weatherIcon.alt = weather[0].description;
    
    // Show weather display
    weatherDisplay.classList.remove("hidden");
}
```



---

## 58.10 Display Error Function



```javascript
function displayError(message) {
    // Hide loading and weather display
    hideLoading();
    weatherDisplay.classList.add("hidden");
    
    // Show error
    errorMessage.textContent = message;
    errorDisplay.classList.remove("hidden");
}
```



---

## 58.11 Loading Functions



```javascript
function showLoading() {
    loading.classList.remove("hidden");
    weatherDisplay.classList.add("hidden");
    errorDisplay.classList.add("hidden");
}

function hideLoading() {
    loading.classList.add("hidden");
}
```



---

## 58.12 Complete JavaScript Code



```javascript
// ====================================
// WEATHER APP - FINAL PROJECT
// ====================================

// API Configuration
const API_KEY = "YOUR_API_KEY_HERE";
const API_URL = "https://api.openweathermap.org/data/2.5/weather";

// Get DOM elements
const weatherForm = document.getElementById("weatherForm");
const cityInput = document.getElementById("cityInput");
const weatherDisplay = document.getElementById("weatherDisplay");
const errorDisplay = document.getElementById("errorDisplay");
const loading = document.getElementById("loading");

const cityName = document.getElementById("cityName");
const country = document.getElementById("country");
const temp = document.getElementById("temp");
const description = document.getElementById("description");
const weatherIcon = document.getElementById("weatherIcon");
const feelsLike = document.getElementById("feelsLike");
const humidity = document.getElementById("humidity");
const windSpeed = document.getElementById("windSpeed");
const pressure = document.getElementById("pressure");
const errorMessage = document.getElementById("errorMessage");

// Event Listeners
weatherForm.addEventListener("submit", async (event) => {
    event.preventDefault();
    const city = cityInput.value.trim();
    
    if (city) {
        await fetchWeather(city);
    }
});

// Fetch Weather Data
async function fetchWeather(city) {
    try {
        showLoading();
        
        const url = `${API_URL}?q=${city}&appid=${API_KEY}&units=metric`;
        const response = await fetch(url);
        
        if (!response.ok) {
            if (response.status === 404) {
                throw new Error("City not found. Please check the spelling.");
            } else if (response.status === 401) {
                throw new Error("Invalid API key. Please check your configuration.");
            } else {
                throw new Error("Failed to fetch weather data. Please try again.");
            }
        }
        
        const data = await response.json();
        displayWeather(data);
        
    } catch (error) {
        displayError(error.message);
    }
}

// Display Weather
function displayWeather(data) {
    hideLoading();
    errorDisplay.classList.add("hidden");
    
    const { 
        name, 
        sys: { country: countryCode },
        main: { temp: temperature, feels_like, humidity: humidityValue, pressure: pressureValue },
        weather,
        wind: { speed }
    } = data;
    
    cityName.textContent = name;
    country.textContent = countryCode;
    temp.textContent = `${Math.round(temperature)}°C`;
    description.textContent = weather[0].description;
    feelsLike.textContent = `${Math.round(feels_like)}°C`;
    humidity.textContent = `${humidityValue}%`;
    windSpeed.textContent = `${speed} m/s`;
    pressure.textContent = `${pressureValue} hPa`;
    
    const iconCode = weather[0].icon;
    weatherIcon.src = `https://openweathermap.org/img/wn/${iconCode}@2x.png`;
    weatherIcon.alt = weather[0].description;
    
    weatherDisplay.classList.remove("hidden");
}

// Display Error
function displayError(message) {
    hideLoading();
    weatherDisplay.classList.add("hidden");
    
    errorMessage.textContent = message;
    errorDisplay.classList.remove("hidden");
}

// Loading Functions
function showLoading() {
    loading.classList.remove("hidden");
    weatherDisplay.classList.add("hidden");
    errorDisplay.classList.add("hidden");
}

function hideLoading() {
    loading.classList.add("hidden");
}
```



---

## 58.13 Enhanced Features (Optional)



### Feature 1: Save Recent Searches

```javascript
// Save to localStorage
function saveRecentSearch(city) {
    let recent = JSON.parse(localStorage.getItem("recentCities")) || [];
    
    if (!recent.includes(city)) {
        recent.unshift(city);
        recent = recent.slice(0, 5); // Keep only 5
        localStorage.setItem("recentCities", JSON.stringify(recent));
    }
}

// Display recent searches
function displayRecentSearches() {
    const recent = JSON.parse(localStorage.getItem("recentCities")) || [];
    const recentDiv = document.getElementById("recentSearches");
    
    recentDiv.innerHTML = recent.map(city => 
        `<button class="recent-btn" onclick="fetchWeather('${city}')">${city}</button>`
    ).join("");
}
```

### Feature 2: Current Location

```javascript
function getCurrentLocationWeather() {
    if (navigator.geolocation) {
        showLoading();
        
        navigator.geolocation.getCurrentPosition(
            async (position) => {
                const { latitude, longitude } = position.coords;
                const url = `${API_URL}?lat=${latitude}&lon=${longitude}&appid=${API_KEY}&units=metric`;
                
                try {
                    const response = await fetch(url);
                    const data = await response.json();
                    displayWeather(data);
                } catch (error) {
                    displayError("Failed to get weather for your location.");
                }
            },
            () => {
                displayError("Unable to get your location.");
            }
        );
    } else {
        displayError("Geolocation is not supported by your browser.");
    }
}
```

### Feature 3: Temperature Unit Toggle

```javascript
let isCelsius = true;

function toggleUnit() {
    const tempValue = parseFloat(temp.textContent);
    const feelsValue = parseFloat(feelsLike.textContent);
    
    if (isCelsius) {
        // Convert to Fahrenheit
        temp.textContent = `${Math.round(tempValue * 9/5 + 32)}°F`;
        feelsLike.textContent = `${Math.round(feelsValue * 9/5 + 32)}°F`;
    } else {
        // Convert to Celsius
        temp.textContent = `${Math.round((tempValue - 32) * 5/9)}°C`;
        feelsLike.textContent = `${Math.round((feelsValue - 32) * 5/9)}°C`;
    }
    
    isCelsius = !isCelsius;
}
```



---

## 58.14 Testing the App



### Test Cases

1. **Valid city:** Enter "London" → Should display weather
2. **Invalid city:** Enter "xyzabc123" → Should show error
3. **Empty input:** Submit empty → Validation should prevent
4. **Special characters:** Try "New York" → Should work
5. **Case insensitive:** Try "PARIS" or "paris" → Should work

### Common Issues

❌ **404 Error** → City name incorrect  
❌ **401 Error** → Invalid API key  
❌ **CORS Error** → Use proper API URL  
❌ **Network Error** → Check internet connection  



---

## 58.15 Deployment



### Option 1: GitHub Pages
1. Create GitHub repository
2. Push your code
3. Settings → Pages → Deploy

### Option 2: Netlify
1. Drag and drop folder
2. Instant deployment
3. Custom domain available

### Option 3: Vercel
1. Import from GitHub
2. Automatic deployments
3. Free hosting



---

## 58.16 What You've Learned



✅ **Fetch API** - Real HTTP requests  
✅ **Async/Await** - Clean asynchronous code  
✅ **Error Handling** - try/catch with meaningful messages  
✅ **DOM Manipulation** - Dynamic UI updates  
✅ **API Integration** - Working with real APIs  
✅ **JSON** - Parsing and extracting data  
✅ **Destructuring** - Clean data extraction  
✅ **Template Literals** - Dynamic strings  
✅ **Event Handling** - Form submission  
✅ **CSS** - Modern responsive design  



---

## 58.17 Next Steps



### Beginner Enhancements
- Add background based on weather
- Show sunrise/sunset times
- Add wind direction indicator
- Display weather alerts

### Intermediate Enhancements
- 5-day forecast
- Hourly forecast
- Weather maps
- Multiple cities comparison

### Advanced Enhancements
- Chart.js for temperature graphs
- Historical data
- Weather notifications
- PWA (Progressive Web App)
- Dark mode
- Multiple language support



---

## 58.18 Course Completion



🎉 **Congratulations!** You've completed the JavaScript full course!

### What You've Mastered

**Fundamentals:**
- Variables, operators, data types
- Control flow (if/else, switch, loops)
- Functions and scope
- Arrays and objects

**Intermediate:**
- Array methods (map, filter, reduce)
- ES6+ features (arrow functions, destructuring, spread/rest)
- Callbacks and higher-order functions
- Error handling

**Advanced:**
- Asynchronous JavaScript
- Promises and async/await
- Fetch API and HTTP requests
- JSON data handling

**DOM & Projects:**
- DOM manipulation
- Event handling
- Real-world projects
- API integration

### Keep Learning

1. **Practice** - Build more projects
2. **Read docs** - MDN Web Docs
3. **Learn frameworks** - React, Vue, Angular
4. **Backend** - Node.js, Express
5. **Database** - MongoDB, SQL
6. **TypeScript** - Typed JavaScript
7. **Testing** - Jest, Mocha
8. **Version Control** - Git/GitHub



---

## Summary - Final Project

✅ Built complete Weather App  
✅ Integrated OpenWeatherMap API  
✅ Implemented async/await patterns  
✅ Created responsive UI  
✅ Added error handling  
✅ Used modern JavaScript features  
✅ Applied all course concepts  

---

## Quick Reference - Weather App

```javascript
// API Setup
const API_KEY = "your_key";
const API_URL = "https://api.openweathermap.org/data/2.5/weather";

// Fetch Weather
async function fetchWeather(city) {
    try {
        const url = `${API_URL}?q=${city}&appid=${API_KEY}&units=metric`;
        const response = await fetch(url);
        
        if (!response.ok) throw new Error("City not found");
        
        const data = await response.json();
        displayWeather(data);
    } catch (error) {
        displayError(error.message);
    }
}

// Display Weather
function displayWeather(data) {
    const { name, main: { temp }, weather } = data;
    
    cityName.textContent = name;
    temperature.textContent = `${Math.round(temp)}°C`;
    description.textContent = weather[0].description;
    
    const iconCode = weather[0].icon;
    weatherIcon.src = `https://openweathermap.org/img/wn/${iconCode}@2x.png`;
}

// Error Handling
function displayError(message) {
    errorMessage.textContent = message;
    errorDisplay.classList.remove("hidden");
}
```

---

## 🎓 COURSE COMPLETE! 🎓

**Thank you for learning JavaScript!**

Now go build amazing things! 🚀

---

## 📚 Navigation

<div align="center">

| **Previous** | **Home** |
|:------------:|:--------:|
| [◀️ Chapters 56 & 57: JSON + Fetch API](Chapters-56-57-JSON-and-Fetch-API.md) | [📑 Index](../README.md) |

</div>

---

<div align="center">

**[⬆ Back to Top](#chapter-58-weather-app-project-final-project)**

🎉 **CONGRATULATIONS!** You've completed the entire JavaScript course! 🎉

Made with ❤️ for JavaScript learners

</div>

**End of Course**  
**Total Duration:** ~12 hours  
**Projects Completed:** 10+  
**Concepts Learned:** 58 chapters worth!
