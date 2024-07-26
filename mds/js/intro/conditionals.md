[&larr; Back](./README.md)

# Conditionals

A conditional statement checks a specific condition(s) and performs a task based on the result.

## Table of Contents

- [if statement](#if-statement)
- [Comparison Operators](#comparison-operators)
- [Logical Operators](#logical-operators)
- [Truthy and Falsy](#truthy-and-falsy)
- [Truthy and Falsy Assignment](#truthy-and-falsy-assignment)
- [Ternary Operator](#ternary-operator)
- [The switch statement](#the-switch-statement)

<br>

## if statement

If ( something is true ) { then do this }

```js
if (true) {
  console.log("It's true!");
}

if (true) console.log("one line statement");
```

- `if` keyword
- Inside `()` parentheses, a condition is provided that evaluates to `true` or `false`
- A code block (block statement) indicated by a set of curly braces `{}`
- If the condition evaluates to `true`, the code inside curly braces `{}` will be executed
- If the condition evaluates to `false`, the block won't execute
- If the statement have only one line, we can skip the curly braces

_Note:_ variables declared inside any code block `{}` will not be accessible outside of the block. To get a value out of a `if` statement, declare the variable outside of the code block, and reassign it inside the if statement.

### if...else statements

```js
if (false) {
  console.log("");
} else {
  console.log("");
}
```

`else` statement will execute if all previous conditions were false.

### else if statements

```js
if (false) {
  console.log("false");
} else if (true) {
  console.log("true");
  console.log("multiple expressions");
} else if (true) {
  console.log("I will not be executed");
}
```

- With `else if`, we can add multiple conditions (as many as we want)
- Each condition is checked, from top to bottom, until it finds the first true one and will execute it
- The rest of the code after the first true condition, will not be executed

<br>

## Comparison Operators

We use **comparison operators** to produce **boolean values**.

- Less than `<`
- Greater than `>`
- Less than or equal to `<=`
- Greater than or equal to `>=`
- Is equal to `===`
- Is not equal to `!==`

Comparison operators compare the value on the left with the value on the right.

We can think of comparison statements as questions. When the answer is "Yes", the statement evaluates to `true`, and when the answer is "no", the statement evaluates to `false`.

```js
5 > 12 - 10; // false
"iphone" === "macbook"; // false
```

_p.s._ JS first do the math operations and then the comparison operations.

We can also use comparison operators on different data types like strings.

All comparison statements evaluate to either `true` or `false` and are made up of: two values that will be compared, and an operator that separates the values and compares them.

<br>

## Logical Operators

- The **and** operator `&&`
- The **or** operator `||`
- The **not** operator `!`

<br>

```js
true && true; // true |
```

- **AND** will return true, only if both conditions are true.
- In all other situations, if either one side is false, then AND returns false.

<br>

```js
false || true; // true
```

- **OR** will return true, if just one of the values evaluates to true.
- Only if all values are false then OR will return false.

<br>

```js
!true; // false
```

- **NOT** will reverse boolean values.
- If the value is true, NOT returns false, and vice versa.

<br>

## Truthy and Falsy

How non-boolean data types are evaluated when checked inside a condition.

### Falsy Values

All of this five falsy values will be evaluated to `false` when we attempt to convert them to a boolean.

- `0`
- Empty string `""`
- `undefined`
- `null`
- `NaN`

### Truthy Values

Everything else are **truthy values**. They evaluate to `true` when we attempt to convert them to a boolean.

Any number that is not zero or any string that is no an empty string will be converted to `true` in logical operations.

### When values are converted to boolean

When does JS convert values to boolean? In two scenarios:

- When using logical operators.
- Inside a logical context, like in the condition of an if statement.

<br>

## Truthy and Falsy Assignment

Short-circuit Evaluation

```js
let age = "";
age = age || "The age is not specified";
```

The OR operator checks the left-hand condition first, and if it is false, it will asign the second value to the variable. But if it is true (truthy), then the first value will be used.

<br>

## Ternary Operator

```js
true ? console.log("true") : console.log("false");
```

1. A condition is provided before the `?` question mark
2. Two expressions follow the `?` and are separated by a colon `:`
3. If the condition evaluates to true, the first expression executes
4. If the condition evaluates to false, the second expression executes

The ternary operator is an expression (it produces a value). This means that we can use it in places where js expects an expression, like when assigning a variable, or in a template literal.

```js
let someVar = true ? "true" : "false";
let greet = `Hello ${true ? "world" : "friend"}`;
```

<br>

## The switch statement

```js
let day = "monday";

switch (day) {
  case "monday": // if day === 'monday'
    console.log("It is monday!");
    console.log("Yupi");
    break;

  case "tuesday":
  case "wednesday":
  case "thursday":
  case "friday":
    console.log("FOUR CASES");
    break;

  case "saturday":
  case "sunday":
    // if day === "saturday" || "sunday"
    cosnole.log("It is saturaday or sunday");
    break;

  default:
    console.log("Not a valid day!");
    break;
}
```

- The `switch` keyword initiates the statement.
- Then inside parentheses we insert the value that will be compared in each case.
- Inside curly braces block `{}`, we define multiple cases with options.
- The `case` keyword will compare the case option with the initial value.
- If the case returns true, then the code after the colon will run until the first `break` keyword.
- The `break` keyword will exit the current block and not execute any more code.
- The values are compared in a strict equality way.
- The `default` statement will run if none of the cases are true.

<br>
