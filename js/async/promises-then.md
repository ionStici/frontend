[&larr; Back](./README.md)

# Consuming Promises

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

```js
fetch("https://restcountries.com/v2/name/italy")
  .then((response) => response.json())
  .then((data) => data[0]);
```

The `fetch()` function will build and return a `Promise`.

At first the `Promise` will be in `pending` state, then at a certain point it will be settled in a fulfilled or rejected state.

To handle the fulfilled state we call `then()` on the `Promise`. Into `then()` we pass a callback which will be executed as soon as the promise is fulfilled. This callback will receive 1 argument which is the value of the fulfilled promise (we name it **response**).

`response` will be an object with data about the response itself, like status, headers, etc. The data itself that we requested is in the body property `response.body`. But, `body` is represented as `ReadableStream` and in order to be able to read the data from the `body` we need to call the `json()` method on `response` which in fact _will return a new Promise._

To further handle the promise, we return `response.json()` from the callback function, and chain another `then()` method to handle the previous returned `response.json()`. The parameter of our second `then()` will be the data itself returned from `response.json()`.

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
prom
  .then((res) => {
    return data;
  })
  .then((secondRes) => data)
  .then((thirdRes) => data);
```

To chain a second `then()`, we have to `return` the promise from the previous `then()`.

### Chaining Promises Mistakes

1. Nesting promises instead of chaining them.

   Be sure to chain the next `then()` method and NOT just nest it.

   This way we are back to callback hell.

2. Be sure to `return` the promise for the next `then()` method.

   If we do not, the next `then()` will handle the same settled value as the original promise.

<br>
