# Lesson 4: Loops

## For Loop

Repeat code a specific number of times:

```javascript
// Print numbers 1 to 5
for (let i = 1; i <= 5; i++) {
  console.log(i);
}

// Anatomy of a for loop:
// for (initialization; condition; increment) {
//   code to execute
// }
```

### Counting Backwards

```javascript
for (let i = 10; i >= 1; i--) {
  console.log(i);
}
console.log("Blast off!");
```

## While Loop

Repeat while a condition is true:

```javascript
let count = 0;

while (count < 5) {
  console.log(`Count is: ${count}`);
  count++;
}
```

**Warning:** Make sure the condition eventually becomes false, or you’ll create an infinite loop!

## Do-While Loop

Execute code at least once, then repeat while condition is true:

```javascript
let password;

do {
  password = prompt("Enter password:");
} while (password !== "secret");

console.log("Access granted!");
```

## Loop Control Statements

### Break

Exit a loop early:

```javascript
for (let i = 1; i <= 10; i++) {
  if (i === 5) {
    break; // Stop the loop when i is 5
  }
  console.log(i); // Prints: 1, 2, 3, 4
}
```

### Continue

Skip the current iteration:

```javascript
for (let i = 1; i <= 5; i++) {
  if (i === 3) {
    continue; // Skip when i is 3
  }
  console.log(i); // Prints: 1, 2, 4, 5
}
```

## Nested Loops

Loops inside loops:

```javascript
// Multiplication table
for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 3; j++) {
    console.log(`${i} × ${j} = ${i * j}`);
  }
}
```

## Common Loop Patterns

### Sum of numbers

```javascript
let sum = 0;
for (let i = 1; i <= 100; i++) {
  sum += i;
}
console.log(`Sum: ${sum}`);
```

### Finding a value

```javascript
let numbers = [10, 20, 30, 40, 50];
let target = 30;
let found = false;

for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] === target) {
    found = true;
    break;
  }
}

console.log(found ? "Found!" : "Not found");
```

## Practice Exercises

1. Write a for loop that prints even numbers from 2 to 20
1. Use a while loop to calculate the factorial of a number (e.g., 5! = 5×4×3×2×1)
1. Create a nested loop that prints a 5×5 grid of asterisks (*)
1. Write a loop that finds and prints all numbers from 1 to 50 that are divisible by both 3 and 5

## Next Lesson

In Lesson 5, we’ll learn about functions and how to organize code into reusable blocks.
