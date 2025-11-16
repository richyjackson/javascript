# Lesson 2: Operators and Expressions

## Arithmetic Operators

Use these operators to perform mathematical calculations:

```javascript
let a = 10;
let b = 3;

console.log(a + b);  // Addition: 13
console.log(a - b);  // Subtraction: 7
console.log(a * b);  // Multiplication: 30
console.log(a / b);  // Division: 3.333...
console.log(a % b);  // Modulus (remainder): 1
console.log(a ** b); // Exponentiation: 1000
```

## Assignment Operators

```javascript
let x = 5;

x += 3;  // Same as: x = x + 3  (result: 8)
x -= 2;  // Same as: x = x - 2  (result: 6)
x *= 4;  // Same as: x = x * 4  (result: 24)
x /= 3;  // Same as: x = x / 3  (result: 8)
```

## Comparison Operators

These return `true` or `false`:

```javascript
let age = 18;

console.log(age == 18);   // Equal to: true
console.log(age === "18"); // Strict equal (type + value): false
console.log(age != 20);   // Not equal: true
console.log(age !== "18"); // Strict not equal: true
console.log(age > 16);    // Greater than: true
console.log(age < 21);    // Less than: true
console.log(age >= 18);   // Greater than or equal: true
console.log(age <= 18);   // Less than or equal: true
```

**Always use `===` and `!==` instead of `==` and `!=` to avoid unexpected type conversions.**

## Logical Operators

Combine multiple conditions:

```javascript
let hasTicket = true;
let isAdult = true;

console.log(hasTicket && isAdult); // AND: both must be true
console.log(hasTicket || isAdult); // OR: at least one must be true
console.log(!hasTicket);           // NOT: inverts the value
```

## String Concatenation

```javascript
let firstName = "John";
let lastName = "Doe";

// Using + operator
let fullName = firstName + " " + lastName;

// Using template literals (modern way)
let greeting = `Hello, ${firstName} ${lastName}!`;
console.log(greeting); // "Hello, John Doe!"
```

## Practice Exercises

1. Calculate the area of a rectangle (length × width)
1. Check if a number is even using the modulus operator
1. Create a greeting message using template literals with your name and age
1. Compare two numbers and log whether the first is greater than the second

## Next Lesson

In Lesson 3, we’ll learn about control flow with if statements and switch cases.
