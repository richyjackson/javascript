# Lesson 10: Modern JavaScript (ES6+)

## Template Literals

Enhanced string syntax with embedded expressions:

```javascript
let name = "Alice";
let age = 25;

// Old way
let greeting = "Hello, " + name + "! You are " + age + " years old.";

// Template literals
let betterGreeting = `Hello, ${name}! You are ${age} years old.`;

// Multi-line strings
let html = `
  <div>
    <h1>${name}</h1>
    <p>Age: ${age}</p>
  </div>
`;

// Expressions
let calculation = `The sum of 5 + 3 is ${5 + 3}`;
```

## Destructuring

Extract values from arrays and objects:

```javascript
// Array destructuring
let colors = ["red", "green", "blue"];
let [first, second, third] = colors;
console.log(first); // "red"

// Skip values
let [primary, , tertiary] = colors;

// Rest operator
let [head, ...rest] = colors;
console.log(rest); // ["green", "blue"]

// Object destructuring
let person = {
  name: "Alice",
  age: 25,
  city: "Boston"
};

let { name, age } = person;
console.log(name); // "Alice"

// Rename variables
let { name: fullName, age: years } = person;

// Default values
let { name, country = "USA" } = person;
```

## Spread Operator

Expand arrays and objects:

```javascript
// Arrays
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let combined = [...arr1, ...arr2];
console.log(combined); // [1, 2, 3, 4, 5, 6]

// Copy array
let original = [1, 2, 3];
let copy = [...original];

// Objects
let person = { name: "Alice", age: 25 };
let details = { city: "Boston", country: "USA" };
let fullProfile = { ...person, ...details };

// Override properties
let updated = { ...person, age: 26 };
```

## Rest Parameters

Collect function arguments into an array:

```javascript
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3));       // 6
console.log(sum(1, 2, 3, 4, 5)); // 15

function introduce(greeting, ...names) {
  return `${greeting} ${names.join(", ")}!`;
}

console.log(introduce("Hello", "Alice", "Bob", "Charlie"));
// "Hello Alice, Bob, Charlie!"
```

## Default Parameters

```javascript
function greet(name = "Guest", greeting = "Hello") {
  return `${greeting}, ${name}!`;
}

console.log(greet());              // "Hello, Guest!"
console.log(greet("Alice"));       // "Hello, Alice!"
console.log(greet("Bob", "Hi"));   // "Hi, Bob!"
```

## Enhanced Object Literals

```javascript
let name = "Alice";
let age = 25;

// Property shorthand
let person = { name, age }; // Same as { name: name, age: age }

// Method shorthand
let obj = {
  // Old way
  sayHello: function() {
    return "Hello";
  },
  // New way
  sayGoodbye() {
    return "Goodbye";
  }
};

// Computed property names
let prop = "favoriteColor";
let user = {
  [prop]: "blue",
  [`${prop}Code`]: "#0000FF"
};
console.log(user.favoriteColor); // "blue"
```

## Arrow Functions Advanced

```javascript
// No parameters
let greet = () => "Hello!";

// Single parameter (parentheses optional)
let double = num => num * 2;

// Multiple parameters
let add = (a, b) => a + b;

// Multi-line function
let calculate = (a, b) => {
  let sum = a + b;
  let product = a * b;
  return { sum, product };
};

// Returning objects (wrap in parentheses)
let makePerson = (name, age) => ({ name, age });
```

## Array Methods (Recap with Advanced Usage)

```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Map
let doubled = numbers.map(n => n * 2);

// Filter
let evens = numbers.filter(n => n % 2 === 0);

// Reduce
let sum = numbers.reduce((acc, n) => acc + n, 0);

// Find - returns first matching element
let firstEven = numbers.find(n => n % 2 === 0); // 2

// Some - checks if any element passes test
let hasEven = numbers.some(n => n % 2 === 0); // true

// Every - checks if all elements pass test
let allPositive = numbers.every(n => n > 0); // true

// Method chaining
let result = numbers
  .filter(n => n % 2 === 0)
  .map(n => n * 2)
  .reduce((acc, n) => acc + n, 0);
```

## Modules

Split code into reusable files:

```javascript
// math.js
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}

export const PI = 3.14159;

// Default export
export default function multiply(a, b) {
  return a * b;
}

// main.js
import multiply, { add, subtract, PI } from './math.js';

console.log(add(5, 3));      // 8
console.log(multiply(4, 7)); // 28
console.log(PI);             // 3.14159
```

## Optional Chaining

Safely access nested properties:

```javascript
let user = {
  name: "Alice",
  address: {
    city: "Boston"
  }
};

// Without optional chaining
let zipCode = user.address && user.address.zipCode;

// With optional chaining
let zipCode2 = user.address?.zipCode;

// Method calls
let result = obj.method?.();

// Array access
let firstItem = arr?.[0];
```

## Nullish Coalescing

Provide default values for null or undefined:

```javascript
// Old way
let value = userInput || "default"; // Problem: treats 0, "", false as falsy

// Nullish coalescing
let value = userInput ?? "default"; // Only replaces null or undefined

let count = 0;
console.log(count || 10);  // 10 (not what we want!)
console.log(count ?? 10);  // 0 (correct!)
```

## Classes

Syntactic sugar for constructor functions:

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  greet() {
    return `Hello, I'm ${this.name}`;
  }
  
  static species() {
    return "Homo sapiens";
  }
}

let alice = new Person("Alice", 25);
console.log(alice.greet());
console.log(Person.species());

// Inheritance
class Student extends Person {
  constructor(name, age, grade) {
    super(name, age);
    this.grade = grade;
  }
  
  study() {
    return `${this.name} is studying`;
  }
}

let student = new Student("Bob", 20, "A");
console.log(student.greet());
console.log(student.study());
```

## Best Practices

1. **Use `const` by default, `let` when needed, avoid `var`**
1. **Prefer arrow functions for callbacks**
1. **Use template literals instead of string concatenation**
1. **Destructure objects and arrays when appropriate**
1. **Use async/await instead of raw promises**
1. **Keep functions small and focused**
1. **Use meaningful variable names**
1. **Comment complex logic, not obvious code**

## Practice Exercises

1. Refactor a callback-based function to use async/await
1. Create a class hierarchy for different types of vehicles
1. Use array methods to process a list of products (filter by price, map to names, etc.)
1. Build a module system with separate files for utilities and main application logic

## Congratulations!

You’ve completed the JavaScript course! Continue practicing by building real projects, reading documentation, and exploring advanced topics like TypeScript, frameworks (React, Vue, Angular), and Node.js.

### Next Steps

- Build projects: Todo app, weather app, calculator
- Learn Git and GitHub for version control
- Explore a frontend framework
- Learn about testing (Jest, Mocha)
- Study Node.js for backend development
- Practice algorithms and data structures
