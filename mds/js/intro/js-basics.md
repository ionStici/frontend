[&larr; Back](./README.md)

# JavaScript Basics

## Table of Contents

- [Strict Mode](#strict-mode)
- [Equality Operators](#equality-operators)
- [Operator Precedence](#operator-precedence)
- [Statements and Expressions](#statements-and-expressions)
- [String Interpolation](#string-interpolation)
- [The DRY Principle](#the-dry-principle)

<br>

## Strict Mode

To active strict mode, include the following string at the beginning of the script:

```js
"strict mode";
```

Strict mode helps developers avoid accidental errors, identify bugs, write secure code.

- Strict mode forbids us to do certain things
- It will create visible errors for us in certain situations
- Introduces a short list of variable names that are reserved for features that might be added to the language latter

<br>

## Equality Operators

Two equality operators: `==` and `===`

Differential operators: `!==` and `!=`

- _The strict equality operator_ **`===`** does not perform type coercion. It only returns true when both values are exactly the same.
- _The loose equality operator_ **`==`** does type coercion, `"18" == 18; // true`

General rule: always use the strict equality operator `===`

<br>

## Operator Precedence

JavaScript has a well defined order of operator precedence (order in which operators are executed).

[**Table of Precedence**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#table)

The grouping `()` parenthesis has the highest priority in precedence, always are executed first.

In JS, assignment operators work from right-to-left - `let x = 10 + 2;` - first is calculated the value from the right, and then the value is assigned to the variable.

<br>

## Statements and Expressions

The difference between expressions and statements is important to know, because JavaScript expects statemenets and expressions in different places. For example, in a template literal, we can only insert expressions, but not statemenets.

- **Expressions** are small units of code that produce a value. They can be thought of as combinations of values, variables, operators, and function calls that result in a single value.

  Expressions can be used within statements to calculate values, assign values to variables, or perform various operations.

  Examples of expressions include mathematical calculations, function calls, and variable references.

  ```js
  let y = 10; // Assignment expression
  let sum = 5 + 3; // Arithmetic expression
  let greeting = "Hello, " + "world!"; // Concatenation expression
  let result = Math.max(5, 8); // Function call expression
  ```

- **Statements** are complete instructions that perform actions. They don't necessarily produce a value but instead perform an operation. Statements often end with a semicolon `;`

  Examples of statements include variable declarations, control structures like `if` and `for` loops, function declarations, and assignments.

  ```js
  let x; // Variable declaration statement
  if (x > 5) {
    // Conditional statement
    console.log("x is greater than 5"); // Function call statement
  }
  ```

<br>

## String Interpolation

We can insert (interpolate) variables into strings using **template literals** (ES6 Feature).

```js
const myName = "John";
let me = `I'm ${myName}`;
console.log(me); // I'm John
```

- A template literal is wrapped by backticks **``**
- Variables are inserted inside curly parentheses `${}` syntax
- We can insert any js expression in the template literal placeholder

Another great use of template literals is to create multi-line strings. Very useful when we build HTML from JS. Before ES6, multi-line strings was more harder to write using `/n/`.

<br>

## The DRY Principle

**DRY** - _don't repeat yourself_.

**Refactoring** - restructuring and improving our code without changing how it works (e.g. eliminating duplicate code).

For example, when we have the same pieces of code in multiple places, we can refactor the same code into a function, and then call that function in all the places where we have the duplicate code. We refactor functionality that we use over and over again into their own function in order to make the code more DRY.

<br>
