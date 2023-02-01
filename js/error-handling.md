[&larr; Back](./README.md)

# Error Handling

**Error Handling** is the process of programmatically anticipating and addressing errors.

<br>

## Table of Content

- [Runtime Errors](#runtime-errors)
- [Constructing an Error](#constructing-an-error)
- [The throw keyword](#the-throw-keyword)
- [The try...catch statement](#the-trycatch-statement)

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

```js
try {
  throw Error("Oh no, you caught me");
} catch (error) {
  console.log(error);
}

console.log("Huh, thanks god you caught the error");
```

<br>
