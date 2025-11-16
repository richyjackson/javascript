# Lesson 7: Objects

## What are Objects?

Objects are collections of key-value pairs that represent entities with properties and behaviors.

## Creating Objects

```javascript
// Object literal
let person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  isEmployed: true
};

// Empty object
let emptyObj = {};
```

## Accessing Object Properties

### Dot Notation

```javascript
let person = {
  name: "Alice",
  age: 25
};

console.log(person.name); // "Alice"
console.log(person.age);  // 25
```

### Bracket Notation

```javascript
console.log(person["name"]); // "Alice"

// Useful when property name is in a variable
let prop = "age";
console.log(person[prop]); // 25

// Required for properties with spaces or special characters
let obj = {
  "first name": "John"
};
console.log(obj["first name"]);
```

## Modifying Objects

```javascript
let person = {
  name: "Alice",
  age: 25
};

// Update property
person.age = 26;

// Add new property
person.email = "alice@example.com";

// Delete property
delete person.age;

console.log(person); // { name: "Alice", email: "alice@example.com" }
```

## Object Methods

Objects can contain functions called methods:

```javascript
let calculator = {
  add: function(a, b) {
    return a + b;
  },
  subtract: function(a, b) {
    return a - b;
  }
};

console.log(calculator.add(5, 3));      // 8
console.log(calculator.subtract(10, 4)); // 6
```

### Shorthand Method Syntax

```javascript
let calculator = {
  add(a, b) {
    return a + b;
  },
  subtract(a, b) {
    return a - b;
  }
};
```

## The `this` Keyword

Inside an object method, `this` refers to the object:

```javascript
let person = {
  firstName: "John",
  lastName: "Doe",
  fullName: function() {
    return `${this.firstName} ${this.lastName}`;
  }
};

console.log(person.fullName()); // "John Doe"
```

**Note:** Arrow functions don’t have their own `this`, so avoid using them as object methods when you need `this`.

## Nested Objects

Objects can contain other objects:

```javascript
let user = {
  name: "Alice",
  address: {
    street: "123 Main St",
    city: "New York",
    zipCode: "10001"
  }
};

console.log(user.address.city); // "New York"
```

## Object Destructuring

Extract properties into variables:

```javascript
let person = {
  name: "Alice",
  age: 25,
  city: "Boston"
};

// Traditional way
let name = person.name;
let age = person.age;

// Destructuring
let { name, age, city } = person;
console.log(name); // "Alice"
console.log(age);  // 25
```

## Useful Object Methods

### Object.keys()

Get all property names:

```javascript
let person = { name: "Alice", age: 25, city: "Boston" };
let keys = Object.keys(person);
console.log(keys); // ["name", "age", "city"]
```

### Object.values()

Get all property values:

```javascript
let values = Object.values(person);
console.log(values); // ["Alice", 25, "Boston"]
```

### Object.entries()

Get key-value pairs:

```javascript
let entries = Object.entries(person);
console.log(entries); 
// [["name", "Alice"], ["age", 25], ["city", "Boston"]]
```

## Iterating Over Objects

```javascript
let person = {
  name: "Alice",
  age: 25,
  city: "Boston"
};

// Using for...in
for (let key in person) {
  console.log(`${key}: ${person[key]}`);
}

// Using Object.entries()
for (let [key, value] of Object.entries(person)) {
  console.log(`${key}: ${value}`);
}
```

## Object Spread Operator

Copy and merge objects:

```javascript
let person = { name: "Alice", age: 25 };

// Copy object
let personCopy = { ...person };

// Merge objects
let contact = { email: "alice@example.com", phone: "555-1234" };
let fullProfile = { ...person, ...contact };

console.log(fullProfile);
// { name: "Alice", age: 25, email: "alice@example.com", phone: "555-1234" }
```

## Practice Exercises

1. Create an object representing a book with properties: title, author, pages, and isRead
1. Add a method to the book object that returns a summary string
1. Create an array of 3 book objects and write a function that returns only the books that have been read
1. Write a function that takes two objects and merges them into one

## Next Lesson

In Lesson 8, we’ll learn about the Document Object Model (DOM) and how JavaScript interacts with web pages.
