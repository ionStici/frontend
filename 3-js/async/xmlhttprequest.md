[&larr; Back](./README.md)

# XMLHttpRequest

_Note:_ The JavaScript Fetch API is an better alternative to the XMLHttpRequest.

The old way of doing Ajax calls: `XMLHttpRequest` function.

```js
let request = new XMLHttpRequest();
request.open("GET", "https://restcountries.com/v2/name/italy");
request.send();

request.addEventListener("load", function () {
  const [data] = JSON.parse(this.responseText);
  console.log(data);
});
```

- We store in a variable and call the `XMLHttpRequest` function.
- In `request.open()`, the first argument is the type of the request. The type of HTTP request to get data is called `GET`. The second argument must be a string containing the URL to which the Ajax call will be made.
- With `request.send()` we send the request to the URL indicated in the `open` method.
- This Ajax call is asynchronous, non-blocking JavaScript.
- To catch the result from the Ajax call, we use a `load` event on the `request` object.
- Once the request finish to fetch the data in the background, step made at `request.send()`, it will emit a `load` event. As soon as the data arrives, the load event is fired and the callback function is called.
- The `this` keyword inside this callback is the request itself.
- The response of the Ajax call is in the property `.responseText`
- The response is in JSON format, so we need to convert this to an actual JavaScript object. JSON is just a big string of text. We use the `JSON.parse()` method to convert JSON strings to objects.

<div></div>

- By calling this `request` twice, we basically have 2 Ajax calls happening at the same time. And this data can arrive in different order at slightly different time - because of the non-blocking behavior. The request is send, and the JavaScipt moves on in the code right away. Either request arrives first, then it will fire the `load` event first.
- If we want these requests to be made in a specific oder then we would have to chain the requests, like: the second request runs only after the first request has finished.

<br>

## Callback Hell

To control which Ajax call finish first and which second, we can create a sequence of Ajax calls so that the second one runs only after the first one has finished.

```js
request.addEventListener("load", function () {
  const [data] = JSON.parse(this.responseText);

  const requestSecond = XMLHttpRequest();
  requestSecond.open("GET", "https://restcountries.com/v2/name/germany");
  requestSecond.send();

  requestSecond.addEventListener("load", function () {
    const [data] = JSON.parse(this.responseText);
  });
});
```

The second Ajax call depends on the first one, because it is placed inside the callback of the first Ajax call. So the second one can't run until the callback of the first one is called.

With this we get nested callbacks, and if we want to do more requests in sequence, we would end with callbacks inside of callbacks inside of callbacks. This kind of structure is called: _callback hell_.

**Callback Hell** is when we have a lot of nested callbacks in order to execute asynchronous tasks in sequence. It makes the code harder to maintain, difficult to understand, looks messy and can produce errors.

Since ES6, we can use **Promises** to do Ajax calls and escape the callback hell.

<br>
