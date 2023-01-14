[&larr; Back](./README.md)

# Variables

## Table of Content

- [Values and Variables](#values-and-variables)
- [let, const, var](#let-const-var)
- [Mathematical Assignment Operators](#mathematical-assignment-operators)
- [The Increment and Decrement Operator](#the-increment-and-decrement-operator)

<br>

## Values and Variables

In programming, a value is the fundamental unit of data, like `23`, `true`, or `Hello`.

Variables are used to label and store data (values) in the computer's memory.

After creating a variable, we can: store or update data, reference for data.

```js
let firstName = "John"; // declaring a variable
```

1. To create or declare a new variable, we use one of the keywords: `let` `const` `var`
2. `firstName` is the variable's name that we gave.
3. `=` is the _assignment operator_. In this case, it assign a value to a variable.
4. `"John"` is the value assigned to the variable `firstName`.

<details>
<summary>Rules for naming variables</summary>

- Cannot start with a number.
- Can only contain: letters, numbers, dollar sign, underscore.
- Variable names are case sensitive.
- Don't use reserved JS keywords.

</details>

<br>

**Naming Convention:** Use the _camelCase_ technique and descriptive names for naming variables.

_Other conventions:_ First letter in uppercase: OOP. All letters in uppercase: for constants.

**Note:** Variables are not the same as values. Variables contain values and represent them with a name.

<br>

## let, const, var

Use `const` by default, and `let` only when you need to update the variable.

### let

`let` keyword is used to declare variables that can be reassigned later.

```js
let myName = "John";

let age;
age = "25";
let x, y, z;
```

We can declare a empty variable, so without assigning a value. In this case, the variable will be automatically initialized with `undefined` as value. But later we can reassign a value to that empty variable. Besides this, we can declare multiple empty variables at once.

### const

`const` is used to declare immutable variables.

We cannot reassgin a const variable, it is a constant.

```js
const myName = "John";

const age; // SyntaxError
const myName = 'Superman';  // TypeError
```

- If we try to reassign a `const` variable, we will get a `TypeError`.
- And if we try to declare a empty `const` variable, we will get a `SyntaxError`.

### var

`var` is the old way of declaring variables, it works similar to `let` with some differences.

In modern JavaScript, `var` should be completely avoided.

<br>

## Mathematical Assignment Operators

The most straightforward assignment operator is just the equal sign `=`

Additionally, JavaScript has _built-in mathematical assignment operators_

```js
let x = 5;
x = x + 2; // 7

x += 1; // 8
x -= 2; // 6
x *= 2; // 12
2 /= 3; // 4
```

The mathematical assignment operator: performs the mathematical operation of the first operator using the number to the right, then reassigning `x` variable to the computed value.

<br>

## The Increment and Decrement Assignment Operators

- _The increment operator_ `++`
- _The decrement operator_ `--`

These operators, will increase or decrease the value of the variable by `1`.

```js
let x = 10;

x++; // 11 | x = x + 1;
x--; // 10 | x = x - 1;
```

Prefixed increment and decrement operators:

```js
let a = 10; // 10
++a; // 11
a++; // 11
a; // 12
```

The prefixed operator will assign the value to the variable immediatly on exactly that line of code.

<br>
