# Lesson 9: Asynchronous JavaScript

## Understanding Synchronous vs Asynchronous

**Synchronous:** Code executes line by line, waiting for each operation to complete.

**Asynchronous:** Code can start an operation and continue executing without waiting for it to finish.

```javascript
// Synchronous
console.log("First");
console.log("Second");
console.log("Third");
// Output: First, Second, Third

// Asynchronous
console.log("First");
setTimeout(() => {
  console.log("Second");
}, 1000);
console.log("Third");
// Output: First, Third, Second (after 1 second)
```

## Callbacks

Functions passed as arguments to be executed later:

```javascript
function fetchData(callback) {
  setTimeout(() => {
    let data = { name: "Alice", age: 25 };
    callback(data);
  }, 2000);
}

fetchData((data) => {
  console.log("Data received:", data);
});
```

### Callback Hell

Multiple nested callbacks become hard to read:

```javascript
// Avoid this!
getData((data) => {
  processData(data, (processed) => {
    saveData(processed, (result) => {
      console.log("Done:", result);
    });
  });
});
```

## Promises

A cleaner way to handle asynchronous operations:

```javascript
let promise = new Promise((resolve, reject) => {
  let success = true;
  
  setTimeout(() => {
    if (success) {
      resolve("Operation successful!");
    } else {
      reject("Operation failed!");
    }
  }, 2000);
});

promise
  .then((result) => {
    console.log(result); // Runs if resolved
  })
  .catch((error) => {
    console.error(error); // Runs if rejected
  });
```

## Promise Chaining

```javascript
function fetchUser() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve({ id: 1, name: "Alice" });
    }, 1000);
  });
}

function fetchPosts(userId) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(["Post 1", "Post 2", "Post 3"]);
    }, 1000);
  });
}

fetchUser()
  .then((user) => {
    console.log("User:", user.name);
    return fetchPosts(user.id);
  })
  .then((posts) => {
    console.log("Posts:", posts);
  })
  .catch((error) => {
    console.error("Error:", error);
  });
```

## Async/Await

Modern syntax that makes asynchronous code look synchronous:

```javascript
async function getData() {
  try {
    let user = await fetchUser();
    console.log("User:", user.name);
    
    let posts = await fetchPosts(user.id);
    console.log("Posts:", posts);
  } catch (error) {
    console.error("Error:", error);
  }
}

getData();
```

### Key Points About Async/Await

- `async` keyword makes a function return a Promise
- `await` can only be used inside `async` functions
- `await` pauses execution until the Promise resolves
- Use `try/catch` for error handling

```javascript
async function example() {
  let result = await someAsyncOperation();
  return result; // Automatically wrapped in a Promise
}

// Calling an async function
example().then(result => console.log(result));
```

## Fetch API

Make HTTP requests to APIs:

```javascript
// GET request
async function getUsers() {
  try {
    let response = await fetch("https://api.example.com/users");
    
    if (!response.ok) {
      throw new Error("Network response was not ok");
    }
    
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Fetch error:", error);
  }
}

getUsers();
```

### POST Request

```javascript
async function createUser(userData) {
  try {
    let response = await fetch("https://api.example.com/users", {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(userData)
    });
    
    let data = await response.json();
    console.log("User created:", data);
  } catch (error) {
    console.error("Error:", error);
  }
}

createUser({ name: "Alice", email: "alice@example.com" });
```

## Promise.all()

Run multiple promises in parallel:

```javascript
async function loadMultipleResources() {
  try {
    let [users, posts, comments] = await Promise.all([
      fetch("/api/users").then(r => r.json()),
      fetch("/api/posts").then(r => r.json()),
      fetch("/api/comments").then(r => r.json())
    ]);
    
    console.log("All data loaded:", users, posts, comments);
  } catch (error) {
    console.error("Error loading resources:", error);
  }
}
```

## Promise.race()

Get the result of the first promise that completes:

```javascript
let promise1 = new Promise((resolve) => {
  setTimeout(() => resolve("First"), 1000);
});

let promise2 = new Promise((resolve) => {
  setTimeout(() => resolve("Second"), 2000);
});

Promise.race([promise1, promise2]).then((result) => {
  console.log(result); // "First"
});
```

## Real-World Example: Weather App

```javascript
async function getWeather(city) {
  const API_KEY = "your-api-key";
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}`;
  
  try {
    let response = await fetch(url);
    
    if (!response.ok) {
      throw new Error("City not found");
    }
    
    let data = await response.json();
    
    return {
      city: data.name,
      temperature: Math.round(data.main.temp - 273.15), // Convert to Celsius
      description: data.weather[0].description
    };
  } catch (error) {
    console.error("Weather fetch error:", error);
    return null;
  }
}

// Usage
async function displayWeather() {
  let weather = await getWeather("London");
  
  if (weather) {
    console.log(`${weather.city}: ${weather.temperature}°C, ${weather.description}`);
  }
}

displayWeather();
```

## Practice Exercises

1. Create a function that simulates an API call with a random delay and returns user data
1. Build a promise chain that fetches data, processes it, and saves the result
1. Use async/await to fetch data from a public API (like JSONPlaceholder)
1. Create a function that races multiple API calls and returns the fastest result

## Next Lesson

In Lesson 10, we’ll explore ES6+ features and modern JavaScript best practices.
