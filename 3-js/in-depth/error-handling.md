[&larr; Back](./README.md)

# Error Handling

**Error Handling** is the process of programmatically anticipating and addressing errors.

## Table of Content

- [Runtime Errors](#runtime-errors)
- [Constructing an Error](#constructing-an-error)
- [The throw keyword](#the-throw-keyword)
- [The try...catch statement](#the-trycatch-statement)
- [Handling with try...catch](#handling-with-trycatch)

<br>

## Runtime Errors

Errors contain useful messages that thell us why our program isn't working or why the error was _thrown_. When an error is thrown, our program stops running and the console displays the error message in red text.

**Runtime Error:** an error thrown after the code execution.

In JavaScript, we have built-in error objects that have a `name` and `message` properties which tell us what went wrong. Examples of built-in runtime errors:

- `ReferenceError` : when a variable or function cannot be found.
- `TypeError` : when a value is not a valid type.

The code that is written after a thrown runtime error will not be evaluated.

<br>

## Constructing an Error

JavaScript errors are objects that have a `name` and `message` property.

What if we need an error message that isn't covered by built-in errors?

We can use the `Error` function to make our own error objects with a unique message.

```js
Error("Oh no, an error");
new Error("Oh no, another error");
```

The `Error` function takes an argument of a string which becomes the value of the error's `message` property.

We might see errors created with the `new` keyword, both methods will lead to the same functionality.

Creating an error is not the same as throwing an error. A thrown error will cause the program to stop running.

<br>

## The throw keyword

Creating an error doesn't cause the program to stop, an error must be thrown for it to halt the program.

To throw an error in JavaScript we use thr `throw` keyword.

```js
throw Error("Oh no, an error occurred, what I'm gonna do");
// Error: Oh no, an error occurred, what I'm gonna do

console.log("This will never run");
```

When we use the `throw` keyword, the error is thrown and code after the `throw` statement will not execute.

<br>

## The try...catch statement

Thrown errrs causes our program to stop running.

We can anticipate and handle errors by writing code to address the error and allow our program to continue running.

Using the `try...catch` statement, we can anticipate and handle errors by writing code to address the error and allow our program to continue running.

```js
try {
  throw Error("Oh no, you caught me");
} catch (error) {
  console.log(error);
}

console.log("Huh, thanks god you caught the error");
```

- Inside the `try` block we insert code that we anticipate might throw an error.
- The `catch` statement accepts the thrown error from the `try` block.
- The parameter `error` represents the thrown error.
- The _catch block_ of the `catch` statement, contains code that executes to handle the error.
- Since the error is caught, the program will keep running.

In a `try..catch` statement, we evaluate code in the `try` block and if the code throws an error, the code inside the `catch` block will handle the error for us. The `catch` block will have access to whatever error occurs in the `try` block.

<br>

## Handling with try...catch

With `try...catch` statement we can handle built-in errors thrown by JavaScript engine.

```js
const age = 24;

try {
  age = 25;
} catch (error) {
  console.log(error);
}

// TypeError: Assignment to constant variable.
```

- Reassignment of a `const` variable - a `TypeError` was thrown.
- Then, in the `catch` block we logged the error.
- `try...catch` for built-in JavaScript errors is useful when working with external data.

<br>
