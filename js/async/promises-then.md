[&larr; Back](./README.md)

# then()

## Table of Content

- [Consuming Promises](#consuming-promises)
- [Success and Failure Callback Functions](#success-and-failure-callback-functions)
- [Consuming a Promise returned by the fetch function](#consuming-a-promise-returned-by-the-fetch-function)
- [Using catch() with Promises](#using-catch-with-promises)
- [Chaining Multiple Promises](#chaining-multiple-promises)

<br>

## Consuming Promises

The initial state of an asynchronous promise is `pending`, but we have a guarantee that it will settle.

How we handle the future fulfilled or rejected value of a promise? Using `then()`

`then()` is a higher-order function, it takes 2 callback functions as arguments (handlers). When the promise settles, the corresponding handler will be invoked with that settled value. Two handlers:

1. **Success handler** contains the logic for the promise resolving.
2. **Failure handler** contains the logic for the promise rejecting.

We can invoke `then()` with one, both, or neither handler.

<br>

## Success and Failure Callback Functions

To consume a promise we invoke `then()` on the promise

```js
const prom = new Promise((response, reject) => resolve("Success"));

const handleSuccess = (resolveValue) => console.log(resolveValue);
const handleFailure = (rejectionReason) => console.log(rejectionReason);

prom.then(handleSuccess, handleFailure); // Success
```

- Argument **1**: the success handler callback.
- Argument **2**: the failure handler callback.

_Terminology:_ the success callback is sometimes called the "success handler function" or the `onFulfilled` function. The failure callback is sometimes called the "failure handler function" or the `onRejected" function.

<br>

## Consuming a Promise returned by the fetch function

**Fetch API** - the modern way of doing Ajax calls.

<br>

## Using catch() with Promises

Instead of passing a second handler into `then()` for failure handling, we can chain a `catch()` function.

```js
prom.then((res) => console.log(res)).catch((rej) => console.log(rej));
// prom.then((res) => console.log(res)).then(null, (rej) => console.log(rej));
```

The `catch()` function takes one argument, which is the **failure handler**, and it will be invoked with the reason for rejection.

<br>

## Chaining Multiple Promises

Chaining Promises _(composition)_

```js
prom.then((res) => data).then((secondRes) => data);
```

<br>
