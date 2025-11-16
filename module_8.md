# Lesson 8: DOM Manipulation

## What is the DOM?

The Document Object Model (DOM) is a programming interface for HTML documents. It represents the page structure as a tree of objects that JavaScript can manipulate.

## Selecting Elements

### getElementById

```javascript
let header = document.getElementById("main-header");
console.log(header);
```

### querySelector

Select the first matching element:

```javascript
// By class
let button = document.querySelector(".btn");

// By ID
let header = document.querySelector("#main-header");

// By tag
let firstParagraph = document.querySelector("p");

// Complex selectors
let navLink = document.querySelector("nav .menu-item");
```

### querySelectorAll

Select all matching elements:

```javascript
let allButtons = document.querySelectorAll(".btn");
console.log(allButtons); // Returns a NodeList

// Convert to array if needed
let buttonsArray = Array.from(allButtons);
```

## Modifying Content

### textContent

```javascript
let heading = document.querySelector("h1");
heading.textContent = "New Heading"; // Changes text content
```

### innerHTML

```javascript
let container = document.querySelector(".container");
container.innerHTML = "<p>New <strong>HTML</strong> content</p>";

// Warning: innerHTML can be dangerous with user input (XSS vulnerability)
```

## Modifying Attributes

```javascript
let image = document.querySelector("img");

// Get attribute
console.log(image.getAttribute("src"));

// Set attribute
image.setAttribute("src", "new-image.jpg");
image.setAttribute("alt", "New description");

// Direct property access
image.src = "another-image.jpg";
image.alt = "Another description";
```

## Modifying Styles

```javascript
let box = document.querySelector(".box");

// Individual styles
box.style.color = "red";
box.style.backgroundColor = "yellow";
box.style.fontSize = "20px";

// Note: CSS properties with hyphens become camelCase
// background-color → backgroundColor
// font-size → fontSize
```

## Working with Classes

```javascript
let element = document.querySelector(".box");

// Add class
element.classList.add("active");

// Remove class
element.classList.remove("hidden");

// Toggle class
element.classList.toggle("highlight");

// Check if class exists
if (element.classList.contains("active")) {
  console.log("Element is active");
}
```

## Creating and Adding Elements

```javascript
// Create new element
let newDiv = document.createElement("div");
newDiv.textContent = "I'm a new div!";
newDiv.classList.add("box");

// Add to page
let container = document.querySelector(".container");
container.appendChild(newDiv); // Add as last child
container.prepend(newDiv);     // Add as first child

// Insert before/after
let existingElement = document.querySelector(".existing");
container.insertBefore(newDiv, existingElement);
```

## Removing Elements

```javascript
let element = document.querySelector(".remove-me");

// Modern way
element.remove();

// Older way
element.parentNode.removeChild(element);
```

## Event Listeners

Handle user interactions:

```javascript
let button = document.querySelector("#myButton");

button.addEventListener("click", function() {
  console.log("Button clicked!");
});

// With arrow function
button.addEventListener("click", () => {
  console.log("Button clicked!");
});

// Event object
button.addEventListener("click", (event) => {
  console.log(event.target); // The element that was clicked
});
```

## Common Events

```javascript
let input = document.querySelector("input");
let form = document.querySelector("form");

// Click
button.addEventListener("click", handleClick);

// Input change
input.addEventListener("input", (e) => {
  console.log(e.target.value);
});

// Form submit
form.addEventListener("submit", (e) => {
  e.preventDefault(); // Prevent page reload
  console.log("Form submitted");
});

// Mouse events
element.addEventListener("mouseenter", handleMouseEnter);
element.addEventListener("mouseleave", handleMouseLeave);

// Keyboard events
input.addEventListener("keydown", (e) => {
  console.log(`Key pressed: ${e.key}`);
});
```

## Example: Interactive Counter

```html
<!DOCTYPE html>
<html>
<head>
  <title>Counter</title>
</head>
<body>
  <h1 id="count">0</h1>
  <button id="increment">+</button>
  <button id="decrement">-</button>
  <button id="reset">Reset</button>

  <script>
    let count = 0;
    let countDisplay = document.getElementById("count");
    let incrementBtn = document.getElementById("increment");
    let decrementBtn = document.getElementById("decrement");
    let resetBtn = document.getElementById("reset");

    incrementBtn.addEventListener("click", () => {
      count++;
      countDisplay.textContent = count;
    });

    decrementBtn.addEventListener("click", () => {
      count--;
      countDisplay.textContent = count;
    });

    resetBtn.addEventListener("click", () => {
      count = 0;
      countDisplay.textContent = count;
    });
  </script>
</body>
</html>
```

## Practice Exercises

1. Create a button that changes the background color of the page when clicked
1. Build a simple todo list where users can add and remove items
1. Create a form that displays entered text in real-time as the user types
1. Make an image gallery where clicking on thumbnails displays a larger version

## Next Lesson

In Lesson 9, we’ll explore asynchronous JavaScript, including callbacks, promises, and async/await.
