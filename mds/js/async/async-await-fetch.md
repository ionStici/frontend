[&larr; Back](./README.md)

# Async / Await

## Table of Contents

- [Consuming Promises with Async / Await](#consuming-promises-with-async--await)
- [Recreating the Geolocation + Country API example](#recreating-the-geolocation--country-api-example)
- [Error Handling with try...catch](#error-handling-with-trycatch)
- [Returning values from async functions](#returning-values-from-async-functions)
- [async...await IIFE](#asyncawait-iife)

<br>

## Consuming Promises with Async / Await

```js
const getCountry = async function (country) {
  const response = await fetch(`https://restcountries.com/v2/name/${country}`);
  const data = await response.json();
  console.log(data[0]);
};
getCountry("italy");
```

1. Prepend the function with an `async` keyword to create an asynchronous function (running in the background while performing the code that's inside of it). When this function is done it automatically returns a promise.

2. Inside the `async` function we use `await` statements to "wait" for the result of the promise. `await` will stop the code execution at this point of the function until the promise is fulfilled and the data has been fetched.

3. We store the resolved value of the `await fetch()` promise in a variable. Then we call `json()` on the `response` which will again return a promise and again we use `await`.

Once a `async...await` function is called, it is loaded off to the background. Again, these functions are executed asynchronously in the background, it will not block the main thread of execution.

By using `async...await` functions, our asynchronous code looks and feels like synchronous code. The function simply wait until the value of the promise is returned and then assign that value to a variable.

<br>

## Recreating the Geolocation + Country API example

```js
const getPosition = function () {
  return new Promise((resolve, reject) => {
    navigator.geolocation.getCurrentPosition(resolve, reject);
  });
};

const asyncFunction = async function (country) {
  // Geolocation
  const position = await getPosition();
  const { latitude: lat, longitude: lng } = position.coords;

  // Country Data
  const response = await fetch(`https://restcountries.com/v2/name/${country}`);
  const data = await response.json();
};
```

<br>

## Error Handling with try...catch

```js
const asyncFunction = async function () {
  try {
    const response = await fetch(`https://restcountries.com/v2/name/italy`);
    const data = await response.json();
    if (!response.ok) throw new Error(`${response.status}`);
    return data[0];
  } catch (error) {
    throw error;
  }
};
```

<br>

## Returning values from async functions

If we try to return something from an `async` function and call it traditionally, we will get a promise in pending state. To get the fulfilled value by returning something from an `async` function, we can use the `then()` method on the function:

```js
asyncFunction()
  .then((data) => data)
  .catch((error) => error.message);
```

To catch errors with the `catch()` method we must _re-throw_ the error inside the `catch` block of the `async` function.

<br>

## async...await IIFE

```js
(async function () {
  try {
    const country = await asyncFunction();
    console.log(country);
  } catch (error) {
    error.message;
  }
  console.log("Instead of finally() method");
})();
```

<br>
