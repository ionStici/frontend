[&larr; Back](./README.md)

# Global object

The **global object** is a special object that is accessible from any part of your code. It provides a set of core functionality and serves as the top-level scope for your JavaScript program when running in a browser environment.

The global object's properties and methods vary depending on whether your code is running in a browser, Node.js, or another JavaScript environment.

In a browser environment, the global object is referred to as `window`, for Node.js it is `global`. Recently, `globalThis` was added to the language as a standard name for the global object.

### Global Functions

Global functions like `setTimeout`, `setInterval`, `alert` are actually properties of the global object in a browser environment, but regardless of this, these functions can be accessed directly:

```js
alert("Hello"); // === window.alert("Hello");
```

### Declaring Global Properties

In a browser, global functions and variables declared with `var` become the property of the global object. Instead of declaring a variable with `var` to make it global, better write it directly as a property:

```js
window.currentUser = { name: "John" };
currentUser.name; // "John"
```

Using global variables is generally discouraged.

### Browser-Specific Properties

_The `window` object provides information about the browser and the environment through properties like:_

- `window.document` represents the DOM
- `window.location` represents the current URL
- `window.navigator` and `window.screen`

..and more!

<br>

## window.open

The `open()` method in JavaScript is used to open a new browser window or tab, depending on the browser's settings.

```js
window.open(url, windowName, windowFeatures);
```

- `url`: the url of the page to be opened in the new window. If not specified or set to an empty string, an empty window is opened.

<br>

## window.history.pushState

The `window.history.pushState(stateObject, title, url)` method is part of the HTML5 History API, it allows you to manipulate the browser's history by adding a new state you the history stack.

This method is commonly used in single-page applications (SPAs) to update the URL and manage navigation without causing a full page reload.

The below example is for removing the `#` symbol from URLs.

```js
history.pushState(
  "",
  document.title,
  window.location.pathname + window.location.search
);
```

Again, `pushState` method allows us to change the url without realing the page. It accepts 3 arguments, first one is called the state which doesn't really matter, second called title which is also not relevant, but the third one is the actual URL.

```js
window.history.pushState(null, "", `#${model.state.id}`);
```

We can do a lot more with the history api, such as going back and forth as if we were clicking the forward and backward buttons in the browser.

<br>

## window.location

The `window.location` object provides information about the current URL and enables you to navigate to different URLs. It is part of the `Location` interface and has several properties and methods that offer functionalities related to the browser's location.

- `widnow.location.href` - string containing the entire URL

- `window.location.pathname` - the URL path

- `window.location.search` - the query parameter of the URL

- `window.location.hash` - URL #id

- `window.location.reload()` - reload the page programmatically

..and more!

These properties and methods of `window.location` are commonly used for tasks like redirecting to a new page, reading and modifying parts of the URL, and controlling navigation within a web application.

<br>

## Namespace

**Namespaces** refers to the technique used for avoiding naming collisions in your code.

For example, an object can be used as a namespace, it helps avoid the risk of naming collisions.

```js
const myNamespace = {
  userName: "John",
  sayHello: () => console.log(`Hello, ${this.userName}`),
};
```

<br>
