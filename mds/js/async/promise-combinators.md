[&larr; Back](./README.md)

# Promise Combinators

Multiple `await` statements in an `async` function will run one after another in sequence. We can check how data is loaded in devTools at Network tab. How to load multiple promises in parallel?

## Table of Contents

- [Promise.all()](#promiseall)
- [Promise.race()](#promiserace)
- [Promise.allSettled()](#promiseallsettled)
- [Promise.any()](#promiseany)

<br>

## Promise.all()

To maximize efficiency we should use _concurrency_, multiple asynchronous operations happening together (in parallel). With promises, we can do this with the function `Promise.all()`.

`Promise.all()` accepts an array of promises as its argument and returns a single promise. It will run all the promises in the array at the same time. That single promise will settle in one of two ways:

- If every promise in the argument array resolves, then `Promise.all()` resolves with an array containing the resolve value from each promise in the argument array.
- If one of the promise rejects, then the whole `Promise.all()` rejects as well (short circuits).

```js
let myPromises = Promise.all([promOne(), promTwo(), promThree()]);
myPromises.then((arrayOfValues) => arrayOfValues).catch((error) => error);
```

```js
// Helper function
const getJSON = function (url, errorMessage = "Error") {
  return fetch(url).then((response) => {
    if (!response.ok) throw new Error(`${errorMessage} (${response.status})`);
    return response.json();
  });
};
```

```js
const getThreeCountries = async function (c1, c2, c3) {
  try {
    const data = await Promise.all([
      getJSON(`https://restcountries.com/v2/name/${c1}`, "Error:"),
      getJSON(`https://restcountries.com/v2/name/${c2}`, "Error:"),
      getJSON(`https://restcountries.com/v2/name/${c3}`, "Error:"),
    ]);

    data.map((c) => c[0].capital);
  } catch (error) {
    error.message;
  }
};
getThreeCountries("italy", "germany", "spain");
```

Now, if we check in devTools how the data is loaded, we will see that it was loaded in parallel.

For multiple asynchronous operations at the same time that don't depend on one another, we should run them in parallel with `Promise.all()`.

`Promise.all()` is a static method on the `Promise` constructor. It is called a combinator because it allows us to combine multiple promises.

In case we don't use `async...await`, we can handle `Promise.all()` with the `then()` method, it will work exactly the same.

<br>

## Promise.race()

Receives an array of promises and returns the first settled promise (rejected or fulfilled).

Use case: to prevent a very long running promise, for example in case of a very bad internet connection.

```js
const timeout = (sec) =>
  new Promise((resolve, reject) =>
    setTimeout(() => reject(new Error("Request tool too long!"), sec * 1000))
  );

Promise.race([
  getJSON(`https://restcountries.com/v2/name/tanzania`),
  timeout(0.1),
])
  .then((data) => data)
  .catch((error) => error.message);
// Request tool too long!
```

If the `timeout` happens first, the other promises in `Promise.race()` will be canceled.

<br>

## Promise.allSettled()

`Promise.allSettled()` (ES2020) takes an array of promises and return an array of all the settled promises, no matter if a promise got rejected or not.

`Promise.all` will short circuit as one promise rejects, but `Promise.allSettled` never short circuits, it simply returns all the results of all the promises.

```js
Promise.allSettled([
  Promise.resolve("Yupi"),
  Promise.reject("Nope"),
  Promise.resolve("Yay"),
]);
```

From our code example, we will get three results, event though one of them rejected. With `Promise.all` in this case we would get an error.

<br>

## Promise.any()

`Promise.any` (ES2021) takes an array of promises and return the first fulfilled promise.

Similar to `Promise.race`, but `Promise.any` ignores rejected promises, unless of course all of them reject.

```js
Promise.any([
  Promise.resolve("Yupi"),
  Promise.reject("Nope"),
  Promise.resolve("Yay"),
])
  .then((res) => res)
  .catch((error) => error);
```

<br>
