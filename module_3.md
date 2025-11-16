# Lesson 3: Control Flow

## If Statements

Execute code based on conditions:

```javascript
let temperature = 25;

if (temperature > 30) {
  console.log("It's hot!");
} else if (temperature > 20) {
  console.log("It's warm!");
} else if (temperature > 10) {
  console.log("It's cool!");
} else {
  console.log("It's cold!");
}
```

## Ternary Operator

A shorthand for simple if-else statements:

```javascript
let age = 18;
let canVote = age >= 18 ? "Yes" : "No";
console.log(canVote); // "Yes"

// Equivalent to:
// if (age >= 18) {
//   canVote = "Yes";
// } else {
//   canVote = "No";
// }
```

## Switch Statements

Handle multiple conditions more elegantly:

```javascript
let day = "Monday";

switch (day) {
  case "Monday":
    console.log("Start of the work week");
    break;
  case "Friday":
    console.log("Almost weekend!");
    break;
  case "Saturday":
  case "Sunday":
    console.log("It's the weekend!");
    break;
  default:
    console.log("It's a regular day");
}
```

**Important:** Don’t forget the `break` statement, or execution will “fall through” to the next case!

## Truthy and Falsy Values

JavaScript converts values to booleans in conditional statements:

```javascript
// Falsy values (evaluate to false):
// false, 0, "" (empty string), null, undefined, NaN

// Truthy values (evaluate to true):
// Everything else!

let name = "";

if (name) {
  console.log("Name is provided");
} else {
  console.log("Name is missing"); // This runs
}
```

## Logical Operators in Conditions

```javascript
let age = 25;
let hasLicense = true;

if (age >= 18 && hasLicense) {
  console.log("Can drive");
}

let isWeekend = true;
let isHoliday = false;

if (isWeekend || isHoliday) {
  console.log("No work today!");
}
```

## Practice Exercises

1. Write an if statement that checks if a number is positive, negative, or zero
1. Use a switch statement to convert a number (1-7) to a day of the week
1. Create a program that checks if someone can watch an R-rated movie (age >= 17)
1. Use the ternary operator to determine if a number is even or odd

## Next Lesson

In Lesson 4, we’ll explore loops and how to repeat code efficiently.
