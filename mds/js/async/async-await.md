[&larr; Back](./README.md)

# Async / Await

## Table of Contents

- [Introduction](#introduction)
- [async...await](#async--await)
- [Handling Errors](#handling-errors)
- [Handling Independent Promises](#handling-independent-promises)
- [Await Promise.all()](#await-promiseall)

<br>

## Introduction

_Asynchronous JavaScript Over Time:_

1. _Originally_, JavaScript used callback functions to handle asynchronous actions (difficult to read, debug, scale).

2. _ES6:_ Native promises (more readable code).

3. _ES8:_ `async...await` new syntax for handling asynchronous actions (improves the readability and scalability of our code). This syntax allows us to write asynchronous code that reads similarly to traditional synchronous, imperative programs.

_Note:_ `async...await` syntax is syntactic sugar, it doesn't introduce new functionality into the language, it is just a new syntax for using the same ES6 promises.

<br>

## async...await

Prepend a function with the `async` keyword to handle asynchronous actions using the function.

We use `then` and `catch` when calling the `async` function to handle the asynchronous action.

Why? Because an `async` function _always_ return a `Promise`.

```js
// const sayHello = async function () {};
// const sayHello = async () => {};

async function sayHello() {
  let hello = await sayHello();
  let data = await myPromise();
  return data;
}

sayHello()
  .then((data) => data)
  .catch((error) => error);
```

The `await` keyword is an operator (used only inside an `async` function) which returns the resolved value of a `Promise`.

Since promises resolve in an indeterminate amount of time, `await` pauses (halts) the execution of the `async` function until a given promise is resolved, until the promise is no longer pending.

Without the `await` keyword, the function execution will not wait for any asynchronous actions.

With `await` we assign the resolved value of the awaited promises to variables. This syntax allows us to handle dependent promises (the second `await` will wait for the previous `await`) in a much more readable and code-less way than the traditional way of chaining `then()` methods.

<br>

## Handling Errors

Using `catch` in a long promise chain makes it challenging to debug and find where the error occurred.

With `async...await` syntax, we use `try...catch` statements to handle errors.

By using `try...catch` we handle both synchronous and asynchronous errors.

```js
async function hello() {
  try {
    const message = "Hello";
    message = await myPromise();
  } catch (error) {
    error; // TypeError
  }
}
```

Since `async` functions return promises we can still use `catch` in the global scope with `async` functions to catch final errors in complex code.

```js
let reject = hello();
reject.catch((error) => error);
```

<br>

## Handling Independent Promises

Each `await` will halt the execution of our `async` function (executing each `await` in sequence).

**Independent promises:** Both promises are constructed without using `await`, then awaited in an array for their resolved value. Both promises and their asynchronous operation run simultaneously.

```js
async function parallel() {
  const first = firstPromise();
  const second = secondPromise();
  [await first, await second];
}
```

<br>

## Await Promise.all()

Multiple promises executed simultaneously.

```js
async function sim() {
  const arrayOfPromises = await Promise.all([promiseOne(), PromiseTwo()]);
}
```

We pass an array of promises as the argument to `Promise.all()`, and it will return a single promise.

This promise will resolve when all of the promises in the argument array have resolved.

This promise’s resolve value will be an array containing the resolved values of each promise from the argument array.

Each provided asynchronous task executed concurrently to each other.

As soon as the first promise in the array rejects, the promise returned from `Promise.all()` will reject with that reason.

<br>
