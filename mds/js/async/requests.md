[&larr; Back](./README.md)

# Requests with Fetch API

How is the information accessed on the web? Through HTTP requests. The four most commonly used types of HTTP requests: GET, POST, PUT, DELETE. With a GET request, we're retrieving information from some source. For a POST request, we're posting information to a soruce that will process the information and send it back

<br>

## Table of Contents

- [Intro to GET Requests using Fetch](#intro-to-get-requests-using-fetch)
- [Intro to POST Requests using Fetch](#intro-to-post-requests-using-fetch)
- [Intro to async GET Requests](#intro-to-async-get-requests)
- [Intro to async POST Requests](#intro-to-async-post-requests)

<br>

## Intro to GET Requests using Fetch

The `fetch()` function creates a request object that contains relevant information that an API needs. Sends that request object to the API endpoint provided. Returns a promise that ultimately resolves to a response object, which contains the status of the promise with information the API sent back.

```js
// FETCH POST
fetch("https://api-to-call.com/endpoint") // 1. Sends Request
  .then(
    (response) => {
      if (response.ok) return response.json(); // 2. Convert response object to JSON
      throw new Error("Request failed!"); // 3
    },
    (error) => error.message // 3. Handle Errors
  )
  .then((data) => data); // 4. Handle Success
```

1. Call the `fetch()` function and pass in a URL as a string for the first argument, determining the endpoint of the request.

   The first argument of the chained `then()` method is the response of the `GET` request. The `then()` method wil fire only after the promises status of `fetch()` has bee resolved.

2. The `ok` property of the `response` object returns a boolean value. If there are no errors, `response.ok` will be `true` and the statement `response.json()` will return.

3. If `response.ok` is a falsy value, our code will `throw ` an error which will be handled by the second callback of the `then()` method.

4. The second `then()` method will run after the previous `then()` method has finished running without errors. Its argument contains the returned `response.json()` object and now can be handled.

<br>

## Intro to POST Requests using Fetch

```js
// FETCH POST
fetch("https://api-to-call.com/endpoint", {
  method: "POST",
  body: JSON.stringify({ id: "200" }),
}) // 1. Send Request
  .then(
    (response) => {
      if (response.ok) return response.json(); // 2. Convert response object to JSON
      throw new Error("Request failed!"); // 3
    },
    (error) => error.message // Handle Errors
  )
  .then((data) => data); // 4. Handle Success
```

1. Constructing POST requests - the `fetch()` function takes two arguments: (1) an endpoint, (2) an object that contains information needed for the POST request.

   This object contains 2 properties: `method` and `body` determining that this is a POST request and what information will be sent to the API.

2. A successful POST request will return a response body.

The rest of the request is identical to the GET request.

<br>

## Intro to async GET Requests

```js
// async await GET
const getData = async () => {
  try {
    const response = await fetch("https://api-to-call.com/endpoint"); // 1. Send Request
    if (response.ok) {
      const data = await response.json();
      // 2. Handle response if successful
    }
    throw new Error("Request failed!"); // 3 +
  } catch (error) {
    // 3 +
    error; // 3. Handle response if unsuccessful
  }
};
```

- Declare an `async` functions which returns a promise.
- The `await` keyword will halt the function while waiting for a promise to resolve.
- `try...catch` statement: the code in the `catch` block will run if in the `try` block execution occured any errors.

<br>

## Intro to async POST Requests

```js
// async await POST
const getData = async () => {
  try {
    const response = await fetch("https://api-to-call.com/endpoint", {
      method: "POST",
      body: JSON.stringify({ id: 200 }),
    }); // 1. Send Request

    if (response.ok) {
      const data = await response.json();
      // 2. Handle response if successful
    }

    throw new Error("Request failed!"); // 3 +
  } catch (error) {
    console.log(error); // 3. Handle response if unsuccessful
  }
};
```

In the `fetch()` call we include additional argument for the POST request that contains information like `method` and `body`. For `method` property we specify the type of the request to `POST`, and in the `body` property we include the value of `JSON.stringify({id: 200})`.

<br>
