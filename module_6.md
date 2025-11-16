# Lesson 6: Arrays

## What are Arrays?

Arrays are ordered collections that can store multiple values in a single variable.

## Creating Arrays

```javascript
// Array literal (most common)
let fruits = ["apple", "banana", "orange"];

// Empty array
let numbers = [];

// Mixed types (possible but not recommended)
let mixed = [1, "hello", true, null];
```

## Accessing Array Elements

Arrays use zero-based indexing:

```javascript
let colors = ["red", "green", "blue"];

console.log(colors[0]); // "red"
console.log(colors[1]); // "green"
console.log(colors[2]); // "blue"

// Get array length
console.log(colors.length); // 3

// Last element
console.log(colors[colors.length - 1]); // "blue"
```

## Modifying Arrays

```javascript
let numbers = [1, 2, 3];

// Change an element
numbers[1] = 20;
console.log(numbers); // [1, 20, 3]

// Add to the end
numbers.push(4);
console.log(numbers); // [1, 20, 3, 4]

// Remove from the end
let last = numbers.pop();
console.log(last);    // 4
console.log(numbers); // [1, 20, 3]

// Add to the beginning
numbers.unshift(0);
console.log(numbers); // [0, 1, 20, 3]

// Remove from the beginning
let first = numbers.shift();
console.log(first);   // 0
console.log(numbers); // [1, 20, 3]
```

## Array Methods

### Finding Elements

```javascript
let fruits = ["apple", "banana", "orange", "banana"];

// Find index of element
console.log(fruits.indexOf("banana"));     // 1
console.log(fruits.lastIndexOf("banana")); // 3

// Check if element exists
console.log(fruits.includes("apple"));  // true
console.log(fruits.includes("grape"));  // false
```

### Adding and Removing Elements

```javascript
let numbers = [1, 2, 3, 4, 5];

// Remove 2 elements starting at index 1
let removed = numbers.splice(1, 2);
console.log(removed); // [2, 3]
console.log(numbers); // [1, 4, 5]

// Insert elements at index 1
numbers.splice(1, 0, 2, 3);
console.log(numbers); // [1, 2, 3, 4, 5]

// Extract a portion (doesn't modify original)
let slice = numbers.slice(1, 4);
console.log(slice);   // [2, 3, 4]
console.log(numbers); // [1, 2, 3, 4, 5] (unchanged)
```

## Iterating Over Arrays

### For Loop

```javascript
let fruits = ["apple", "banana", "orange"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

### For…of Loop

```javascript
for (let fruit of fruits) {
  console.log(fruit);
}
```

### forEach Method

```javascript
fruits.forEach(function(fruit, index) {
  console.log(`${index}: ${fruit}`);
});

// With arrow function
fruits.forEach((fruit, index) => {
  console.log(`${index}: ${fruit}`);
});
```

## Array Transformation Methods

### Map

Create a new array by transforming each element:

```javascript
let numbers = [1, 2, 3, 4, 5];
let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

### Filter

Create a new array with elements that pass a test:

```javascript
let numbers = [1, 2, 3, 4, 5, 6];
let evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4, 6]
```

### Reduce

Reduce array to a single value:

```javascript
let numbers = [1, 2, 3, 4, 5];
let sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // 15
```

## Combining Arrays

```javascript
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];

// Using concat
let combined = arr1.concat(arr2);
console.log(combined); // [1, 2, 3, 4, 5, 6]

// Using spread operator
let spread = [...arr1, ...arr2];
console.log(spread); // [1, 2, 3, 4, 5, 6]
```

## Practice Exercises

1. Create an array of 5 numbers and calculate their average
1. Write a function that takes an array and returns a new array with only unique values
1. Use `filter` to get all words longer than 5 characters from an array of strings
1. Use `map` to convert an array of Celsius temperatures to Fahrenheit

## Next Lesson

In Lesson 7, we’ll explore objects and how to structure complex data.
