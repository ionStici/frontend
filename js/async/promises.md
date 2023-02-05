[&larr; Back](./README.md)

# Promises

## Table of Content

- [Promises Introduction](#promises-introduction)

<br>

## Promises Introduction

**Promises** are objects that represent the eventual outcome of an asynchronous operation.

<details>
<summary>Other Definitions</summary>

<div></div>

- Promise: an object that is used as a placeholder for the future result of an asynchronous operation.

<div></div>

- Promise: a container for an asynchronous delivered value.

<div></div>

- Promise: a container for a future value. Example of future value: the response from an Ajax call.

<div></div>

_Advantages of using promises:_

<div></div>

- We no longer rely on events and callbacks to handle asynchronous results.

<div></div>

- We chain promises as a sequence and escape callback hell.

<div></div>

</details>

<br>

Since promises work with asynchronous operations, they are time-sensitive, meaning that promises change over time. We call this the _life cycle of a promise_. A `Promise` object can be in one of 3 states:

1. **Pending:** The initial state - the operation has not completed yet. This is before any value resulting from the asynchronous task is available. During this time, the asynchronous task is still doing its work in the background.

   Then, when the task finishes, the Promise is **Settled**. There are 2 different types of settled promises: _Fulfilled_ and _Rejected_ promises.

2. **Fulfilled:** The operation has completed successfully and the promise now has a _resolved value_

   A fulfilled promise successfully resulted in a value, for example a request's promise might resolve a JSON object as its value after fetching data from an API. The promise received the data and is now available for use.

3. **Rejected:** The operation has failed and the promise has a reason for the failure. The reason is usually an `Error` of some kind during the asynchronous task, for example in case the user is offline.

All promises eventually settle, enabling us to write logic for what to do if the promise fulfills or if it rejects.

_Note:_ A promise is only settled once, and from there the state will remain unchanged. The promise will be either fulfilled or rejected. It's impossible to change the settled state.

These different states are relevant once we use the promise to get a result: **to consume a Promise**. For example we consume a promise that was returned from the fetch function.

Generally, a `Promise` first must be build. In the case of the Fecth API, it's the fetch function that builds the promise and returns it for us to consume. So in this case we don't have to build it ourselves. Most of the times we just consume returned promises from the Fetch function, but sometimes we also need to build a `Promise`.

<br>
