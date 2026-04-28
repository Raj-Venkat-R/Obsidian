---
title: "JavaScript Notes - Arrays, Loops, Objects, Array Methods"
tags: [javascript, arrays, loops, objects, map, filter]
created: 2026-04-28
---

# Arrays, Loops, Objects, and Array Methods

## Overview
This section covers:
- Arrays and their behavior
- Looping techniques
- Objects and key–value structure
- Array methods: forEach, map, filter
- Arrow functions

---

# 1. Arrays

## Definition
An array is an **ordered collection of values** stored in a single variable.

```js
let arr = [10, 20, 30];
```

---

## Key Characteristics

### 1. Indexed (0-based)

```js
arr[0] // 10
arr[1] // 20
```

---

### 2. Dynamic Size

```js
let arr = [];
arr.push(10);
```

Array size grows automatically.

---

### 3. Mixed Data Types

```js
let arr = [1, "hello", true, null];
```

---

### 4. Length

```js
arr.length
```

---

## Modifying Arrays

### Update

```js
arr[1] = 50;
```

---

### Add Elements

```js
arr.push(40);     // end
arr.unshift(5);   // beginning
```

---

### Remove Elements

```js
arr.pop();     // remove last
arr.shift();   // remove first
```

---

## Important Concept: Reference Behavior

```js
let arr = [1, 2];
let copy = arr;

copy[0] = 100;

console.log(arr); // [100, 2]
```

Arrays share memory when assigned.

---

## Checking Array Type

```js
Array.isArray(arr); // true
```

---

# 2. Loops

## Definition
Loops are used to **repeat a block of code**.

---

## for Loop (Most Important)

```js
for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

Use when:
- Iteration count is known
- Working with arrays

---

## while Loop

```js
let i = 0;

while (i < 5) {
    console.log(i);
    i++;
}
```

Use when:
- Iteration count is unknown

---

## do...while Loop

```js
let i = 0;

do {
    console.log(i);
    i++;
} while (i < 5);
```

Runs at least once.

---

## for...of Loop (Preferred for Arrays)

```js
for (let value of arr) {
    console.log(value);
}
```

- Directly gives values
- Cleaner than index-based loop

---

## for...in Loop

```js
for (let key in obj) {
    console.log(key);
}
```

- Used for objects
- Returns keys (not values)

Not recommended for arrays.

---

## Control Statements

### break

```js
if (i === 5) break;
```

Stops loop.

---

### continue

```js
if (i === 2) continue;
```

Skips current iteration.

---

# 3. Objects

## Definition
An object is a **collection of key–value pairs**.

```js
let user = {
    name: "Raj",
    age: 20
};
```

---

## Accessing Values

### Dot notation

```js
user.name
```

---

### Bracket notation

```js
user["name"]
```

Used when key is dynamic:

```js
let key = "name";
user[key];
```

---

## Modifying Object

```js
user.age = 21;
```

---

## Adding Property

```js
user.city = "Chennai";
```

---

## Deleting Property

```js
delete user.age;
```

---

## Looping Object

```js
for (let key in user) {
    console.log(key, user[key]);
}
```

---

## Object vs Array

| Feature | Array            | Object           |
|--------|-----------------|------------------|
| Access | Index           | Key              |
| Order  | Ordered         | Not strict       |
| Use    | List data       | Structured data  |

---

# 4. Array Methods

## forEach()

### Definition
Loops through array elements.

```js
arr.forEach(function(value) {
    console.log(value);
});
```

### Key Points
- Does not return anything
- Used for side effects (logging, DOM updates)

---

## map()

### Definition
Transforms array and returns a new array.

```js
let result = arr.map(function(value) {
    return value * 2;
});
```

### Key Points
- Returns new array
- Does not modify original array

---

## filter()

### Definition
Selects elements based on condition.

```js
let result = arr.filter(function(value) {
    return value > 10;
});
```

### Key Points
- Returns new array
- Includes only matching elements

---

## Comparison

| Method     | Purpose              | Returns       |
|------------|---------------------|---------------|
| forEach    | Execute code        | undefined     |
| map        | Transform values    | New array     |
| filter     | Select values       | New array     |

---

# 5. Arrow Functions

## Definition
Shorter syntax for writing functions.

---

## Normal Function

```js
function add(a, b) {
    return a + b;
}
```

---

## Arrow Function

```js
let add = (a, b) => {
    return a + b;
};
```

---

## Short Form

```js
let add = (a, b) => a + b;
```

---

## Usage with Array Methods

```js
arr.map(val => val * 2);
arr.filter(val => val > 10);
arr.forEach(val => console.log(val));
```

---

## Common Mistake

```js
arr.filter(val => {
    val > 10; // missing return
});
```

Correct:

```js
arr.filter(val => val > 10);
```

---

# Key Takeaways

- Arrays store ordered data and are dynamic
- Loops help iterate through data
- Objects store structured data using key–value pairs
- `forEach`, `map`, `filter` are core array methods
- Arrow functions simplify function syntax
- Use the right method based on purpose (loop vs transform vs filter)

---

# Next Step

- Combine arrays + objects
- Practice problems:
  - filter + map chaining
  - array of objects
  - real data manipulation