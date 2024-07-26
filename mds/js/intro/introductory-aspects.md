[&larr; Back](./README.md)

# Introductory Aspects

## Table of Contents

- [Console](#console)
- [Comments in JavaScript](#comments-in-javascript)
- [Data Types](#data-types)
- [typeof operator](#typeof-operator)
- [Arithmetic Operators](#arithmetic-operators)
- [String Concatenation](#string-concatenation)
- [Properties](#properties)
- [Methods](#methods)
- [Built-in Objects](#built-in-objects)

## Console

The **console** is a panel that can be used to display messages from the source code.

When we have an error in our code, usually we get a notification in the browser's console, along with the line where the error is.

We can log certain things to the console to see the results of the code execution.

In JS, the `console` keyword is an object that contains a collection of data and actions that we can use in our code.

Keywords are words that are built into the JS language, so the computer recognizes them and treats them correspondingly.

One action that is built into the `console` object is the `.log()` method, which will print to the console what we type inside the parentheses.

```js
console.log("hello"); // hello
console.log(console); // to see what methods the console object contains
console.error("An Error"); // Will display the result in red as an error
```

The semicolon denotes the end of the statement.

## Comments in JavaScript

```
Single-line: // code
Multi-line:  /* code */
```

## Data Types

Data types are the classifications JavaScript gives to the different kinds of data that we use in programming.

In JS, there are eight fundamental data types:

1. **Number:** Any number, integers or decimals.
2. **String:** A sequence of characters surrounded by single or double quotes (used for text).
3. **Boolean:** Logical type that can be only `true` or `false`. Used for taking decisions.
4. **undefined** represents the absence of a value.

   This data type is denoted by the keyword `undefined`.

   This value is taken by a variable that is not yet defined (empty value).

   For an empty value, `undefined` is also the value and the data type.

5. **Null** is represented by the keyword `null`.

   Represents the intentional absence of a value (empty value).

   Compared to `undefined`, `null` is used in different circumstances.

6. **Symbol:** introduced in ES2015. Symbols are unique identifiers, useful in more complex coding.

7. **BigInt:** (ES2020) is for integers that are too large to be represented by the `number` type.

8. **Object:** Collections of related data.

The first 7 data types can be referred as **primitive data types** or just **primitives**.

**Objects** or **Reference types** are more complex.

## typeof operator

We can check the type of a value using the `typeof` operator:

```js
typeof true; // boolean
typeof null; // object
```

JS says that the type of `null` is an object, which is not correct, `typeof null` should return `null`. This is regarded as an error in js, but it is never corrected for legacy reasons.

## Arithmetic Operators

JavaScript built-in arithmetic operators.

An operator is a character that performs a task and transforms values or combine multiple values.

```js
3 + 5; // 8 | add +
2 - 2; // 0 | substract -
3 * 2; // 6 | multiply *
4 / 1; // 4 | divide /
3 ** 3; // 27 | exponentiation **
7 % 3; // 1 | remainder (modulo) %
```

The remainder operator `%` returns the number that _remains_ after the right-hand number divides into the left-hand number as many times as it **evenly** can.

## String Concatenation

We can use the plus operator to join (**concatenate**) strings:

```js
"hello" + " " + "world"; // hello world
greeting + " " + myName; // Hello John | String Concatenation with Variables
```

This appends the right string to the left string.

## Properties

A **property** is a piece of information about and stored in a particular data type.

For example, each string instance has a `.length` property that holds the number of characters the string has, example:

```js
"hello".length; // 5
```

Here, we append the `length` property to a string using the dot `.` operator.

The `.length` property will return 5 in this case, which is the number of characters the string has.

_Note:_ Depending on the data type, we have access to specific properties.

## Methods

Methods are like actions we can perform.

Data types have access to specific methods that allow us to handle instances of that data type.

We **call** a method by appending an instance with: the dot `.` operator -> the method name -> opening and closing parentheses.

Example: `'string'.methodName()`

```js
"hello".toUpperCase(); // HELLO | returns the string in all capital letters
```

[List of built-in string methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

## Built-in Objects

Built-in objects - e.g. `Math` - contain a collection of methods and properties that JS provides.

For complex mathematical operations, JS has the built-in `Math` object.

```js
Math.random(); // returns a random number between 0 and 1
```

Here, we called `.random()` method on the `Math` built-in object.
