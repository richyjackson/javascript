# Lesson 5: Functions

## What are Functions?

Functions are reusable blocks of code that perform specific tasks. They help organize code and avoid repetition.

## Function Declaration

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

greet("Alice"); // Call the function
greet("Bob");
```

## Function Parameters and Arguments

```javascript
function add(a, b) {
  // a and b are parameters
  return a + b;
}

let result = add(5, 3); // 5 and 3 are arguments
console.log(result); // 8
```

## Return Values

Functions can return values using the `return` keyword:

```javascript
function multiply(x, y) {
  return x * y;
}

let product = multiply(4, 7);
console.log(product); // 28

function isEven(num) {
  return num % 2 === 0;
}

console.log(isEven(10)); // true
console.log(isEven(7));  // false
```

## Function Expressions

Store functions in variables:

```javascript
const square = function(num) {
  return num * num;
};

console.log(square(5)); // 25
```

## Arrow Functions

Modern, concise syntax (ES6+):

```javascript
// Traditional function
const add = function(a, b) {
  return a + b;
};

// Arrow function
const addArrow = (a, b) => {
  return a + b;
};

// Shorter arrow function (implicit return)
const addShort = (a, b) => a + b;

// Single parameter (parentheses optional)
const double = num => num * 2;

console.log(double(5)); // 10
```

## Default Parameters

Provide default values for parameters:

```javascript
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}

greet("Alice"); // "Hello, Alice!"
greet();        // "Hello, Guest!"
```

## Function Scope

Variables declared inside functions are only accessible within that function:

```javascript
function myFunction() {
  let localVar = "I'm local";
  console.log(localVar); // Works
}

myFunction();
// console.log(localVar); // Error: localVar is not defined

let globalVar = "I'm global";

function anotherFunction() {
  console.log(globalVar); // Works - can access global variables
}
```

## Higher-Order Functions

Functions that take other functions as arguments:

```javascript
function executeOperation(a, b, operation) {
  return operation(a, b);
}

const add = (x, y) => x + y;
const multiply = (x, y) => x * y;

console.log(executeOperation(5, 3, add));      // 8
console.log(executeOperation(5, 3, multiply)); // 15
```

## Practice Exercises

1. Create a function that calculates the area of a circle (πr²)
1. Write a function that takes a temperature in Celsius and converts it to Fahrenheit
1. Create an arrow function that checks if a string is longer than 5 characters
1. Write a function that takes an array of numbers and returns the largest number

## Next Lesson

In Lesson 6, we’ll dive into arrays and how to work with collections of data.
