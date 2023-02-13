[&larr; Back](./README.md)

# Promises

## Table of Content

- [Promises Introduction](#promises-introduction)
- [Constructing a Promise](#constructing-a-promise)
- [resolve and reject methods](#resolve-and-reject-methods)
- [Promisifying](#promisifying)

<br>

## Promises Introduction

A `Promise` is an object that represent the eventual outcome of an asynchronous operation.

</details>

Since promises work with asynchronous operations, they are time-sensitive, meaning that promises change over time. A `Promise` object can be in one of 3 states:

1. **Pending** is the initial state of the promise, the asynchronous operation has not completed yet, the promise still awaits a response.

   When the asynchronous operation has finished, the `Promise` is **Settled**. Two different types of settled promises: _Fulfilled_ and _Rejected_ promises.

2. **Fulfilled:** The asynchronous operation has completed successfully and the promise now has a _resolved value_.

3. **Rejected:** The asynchronous operation has failed and the promise received a reason for the failure (error).

After the `Promise` is constructed and then settled, we **consume the Promise**.

<br>

## Constructing a Promise

We create new promises using the `Promise` constructor.

```js
const condition = Math.random() > 0.5;

const executorFunction = (resolve, reject) =>
  setTimeout(() => (condition ? resolve("YES") : reject("NO")), 1500);

const prom = new Promise(executorFunction);
```

The `Promise` constructor takes a function as argument (_executor function_). The executor function starts an asynchronous operation and dictates how the promise should be settled.

The executor function receives 2 function parameters: `resolve()` and `reject()`. Depending on which of these 2 functions is called, the promise will resolve or reject.

- If `resolve` is invoked, the state of the promise will change from pending to fulfilled. The resolved value will be set to the argument passed into `resolve()`.

- If `reject` is invoked, the state of the promise will change fro pending to rejected. The rejection reason will be set to the argument passed into `reject()`.

_p.s._ By using the `setTimeout` function we simulate an asynchronous behavior.

<br>

## resolve and reject methods

`Promise.resolve()` and `Promise.reject()` are static methods on the `Promise` constructor. These two will create a promise that is immediately resolved or rejected.

The argument we pass in will be the fulfilled or rejected value which we then handle with `then()` or `catch()`.

```js
Promise.resolve("Resolved").then((x) => x); // handle with then()
Promise.reject("Rejected").catch((x) => x); // handle with catch()
```

<br>

## Promisifying

**Promisifying** means to convert a callback based asynchronous behavior to promise based.

1. Promisifying: Creating a function -> Returning a Promise.
2. Inside `then()` we run the code supposed for promisifying.

```js
const getPosition = () =>
  new Promise((resolve, reject) => {
    navigator.geolocation.getCurrentPosition(resolve, reject);
  });

getPosition()
  .then((position) => [position.coords.latitude, position.coords.longitude])
  .catch((error) => error.message);
```

<br>
