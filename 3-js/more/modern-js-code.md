[&larr; Back](./README.md)

# Modern and Clean JavaScript Code

### 1. Readable Code

- Write code so that **others** can understand it
- Write code so that **you** can understand it in 1 year
- Avoid too "clever" and overcomplicated solutions
- Use descriptive variable names: **what they contain**
- Use descriptive function names: **what they do**

### 2. General Rules

- Use **DRY** principle (refactor your code)
- Dont pollute global namespace, encapsulate instead
- Don't use `var`
- Use strong type checks `===` and `!==`

### 3. Functions

- Generally, functions should do **only one thing**
- Don't use more than 3 function parameters
- Use default parameters whenever possible
- Generally, return same data type as received
- Use arrow functions when they make code more readable

### 4. OOP

- Use ES6 classes
- Encapsulate data and **don't mutate** it from outside the class
- Implement method chaining
- Do **not** use arrow functions as methods (in regular objects)

### 5. Avoid Nested Code

- Use early `return` **"guard clauses"**
- Use ternary (conditional) or logical operators instead of `if`
- Use multiple `if` instead of `if/else-if`
- Avoid `for` loops, use array methods instead
- Avoid callback-based asynchronous APIs

### 6. Asynchronous Code

- Consume promises with `async/await` for best readability
- Whenever possible, run promises in **parallel** `Promise.all`
- Handle errors and promise rejections

<br>
