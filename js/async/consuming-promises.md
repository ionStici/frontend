[&larr; Back](./README.md)

# Consuming Promises

## Table of Content

- [Consuming Promises](#consuming-promises)
- [Success and Failure Callback Functions](#success-and-failure-callback-functions)
- [Consuming a Promise returned by the fetch function](#consuming-a-promise-returned-by-the-fetch-function)
- [Using catch() with Promises](#using-catch-with-promises)
- [Handling Rejected Promises](#handling-rejected-promises)
- [Chaining Multiple Promises](#chaining-multiple-promises)
- [finally() method](#finally-method)
- [Throwing Errors Manually](#throwing-errors-manually)

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

_Explication:_ The data that we receive as a parameter to the first callback of the `then()` function is the fulfilled value of the `Promise` we're handling.

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

## Handling Rejected Promises

```js
fetch("https://restcountries.com/v2/name/italy")
  .then(
    (response) => response.json(),
    (error) => console.log(err.message)
  )
  .then((data) => data[0])
  .catch((error) => console.log(err.message));
```

A Promise in which an error happens is a rejected promise. The only way in which `fetch` rejects in when the user loses his internet connection. To simulate no internet connection we can use chrome devTools (Network -> offline).

Using `fetch` while offline error: `Uncaught (in promise) Type Error: Failed to fetch.`

**2 ways of handling promise rejection:**

1. _Using a second callback into the `then() method._

   This callback will be called with an error argument when the promise will reject.

   By handling errors like this we actually catch the default error (similar to `try...catch`).

2. **Using the `catch()` method**, technically works like the second callback of `then()`

   The `catch()` method will catch all the errors no matter where they appeared in the promise chain.

   Errors basically propagate down the chain until they are caught, and only if they're not caught anywhere then we get that `Uncaught` error.

   `catch` also receives the error object. We place `catch` at the end of the chain.

The error object that we receive as a parameter in `catch`, contains a `message` property that we can use.

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

// Fetch example
fetch("https://restcountries.com/v2/name/italy")
  .then((response) => response.json())
  .then((data) => {
    data[0];

    return fetch("https://restcountries.com/v2/name/germany");
  })
  .then((response) => response.json())
  .then((data) => data[0]);
```

- The chained Promise depends on the first Promise, being done in sequence.
- To chain a second `then()`, we have to `return` the promise from the previous `then()`.
- The chained `then()` method will handle whatever promise was returned from the previous `then()`.
- The `then()` method always returns a `Promise`, no matter if we return explicitly anything or not.

<div></div>

**Example:** We return a simple value inside the `then()` method. That value will become the fulfilled value of the promise that the current `then()` returns. The next chained `then()` will receive that value as a parameter to the fulfilled handler function.

<div></div>

- **Fetch Example**

  The second Ajax call occurs in the `then()` method of the first Ajax call. As soon as the first Ajax call is made, only then the second Ajax call occur.

  By returning a promise with the `fetch()` function inside the `then()` method, the next `then()` method will receive the fulfilled value of the promise created by `fetch()` in the previous `then()`.

<br>

### Chaining Promises Mistakes

1. Nesting promises instead of chaining them.

   Be sure to chain the next `then()` method and NOT just nest it.

   This way we are back to callback hell.

2. Be sure to `return` the promise for the next `then()` method.

   If we do not, the next `then()` will handle the same settled value as the original promise.

<br>

## finally() method

```js
prom.then((res) => res).finally(() => console.log("Finally"));
```

The `finally()` method and its callback will always be called whatever the promise is fulfilled or rejected.

_Note:_ `finally` and `catch` also return the promise, we can chain methods on them.

<br>

## Throwing Errors Manually

In case we search for a country that doesn't exist, we get the following error:

`Cannot read property “flag” of undefined.`

This error doesn't reflect the true meaning that the API can't find a country with the wrong name.

Besides this, the promise will still be fulfilled. The `fetch` function only rejects when there is no internet connection.

In our situation we have a 404 error comming from the server which is not a real error. So there is no rejection and our `catch()` method cannot pick up this error.

We have to manually fix the `404` request error that happens when APIs doesn't find what we requested and tell the user that no result was found with this name. The `fetch` function doesn't reject in a case like this and we have to do it manually.

```js
fetch(`https://restcountries.com/v2/name/italy`)
  .then((response) => {
    if (!response.ok) throw new Error(`Error: ${res.status}`);
    return res.json();
  })
  .then((data) => data[0])
  .catch((error) => error.message);
```

We find information about the request in the `response` object. In case the API does not find any result, the property `ok` from the `response` object is set to `false`, and the `status` property is set to `404`.

If `status` were `200`, then `ok` would be `true`, this happens when the request was succesfully.

We can use the fact the `ok` is false and reject the promise manually by creating a real error.

- **_if ( response.ok is false ) then throw error_**

We create a new error using the `Error` constructor and pass in the error message.

Then, the `throw` keyword will immediately terminate the current function, just like `return` does.

The effect of creating and throwing an error like in our code example, is that the promise from the current `then()` method will reject, and this rejected promise will propagate down to the `catch` method.

The error message that we created using the `Error` constructor will be used for the rejection error object. We can find the message in the `error.message` property.

If we get a rejection in the second `fetch` then we get a `400` error.

_Advice:_ Create error messages that make sense and inform the user by displaying UI messages.

<br>

### Helper function

```js
const getJSON = function (url, errorMessage) {
  return fetch(url).then((res) => {
    if (!res.ok) throw new Error(`${errorMessage}: ${res.status}`);
    return res.json();
  });
};

getJSON(`https://restcountries.com/v2/name/italy`, "Error")
  .then((data) => data[0])
  .cathc((error) => error.message);
```

<br>
