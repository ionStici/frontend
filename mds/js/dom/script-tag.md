[&larr; Back](./README.md)

# Connecting HTML with JavaScript

## Table of Contents

- [The Script Element](#the-script-element)
- [Link a JavaScript file](#link-a-javascript-file)
- [How are scripts loaded?](#how-are-scripts-loaded)
- [`defer` attribute](#defer-attribute)
- [`async` attribute](#async-attribute)

<br>

##

## The Script Element

JavaScript makes HTML documents dynamic and interactive.

The `<script>` element allow us to add JavaScript code right inside an HTML file.

We can think of the `<script>` element as the door to JavaScript for HTML.

```js
<script>/* js code */</script>
```

<br>

## Link a JavaScript file

We can link an external js file to our HTML document using the `src` attribute and the js file path name.

```js
<script src="script.js"></script>
```

<br>

## How are scripts loaded?

_HTML parsers_ render the html elements accordingly. Elements are by default parsed in the order they appear in the HTML file. When the HTML parser reach the `script` element, it FIRST loads the script and executes its contents BEFORE parsing the rest of the HTML. If one script depends on another script, they should be placed in the correct order.

**Regular `<head>`**

```js
<head>
  <script src="script.js"></script>
</head>
```

In the html parsing phase, when the script tag is reached, the html parsing will stop and wait for the script to get fetched and executed, and only after that the rest of the html can be parsed. Note: that the script will be executed before the DOM is ready.

**Regular `<body>`**

```js
<body>
  /* all html code */
  <script src="script.js"></script>
</body>
```

We put the script at the end of the body tag, so that all the html is already parsed when it reaches the script tag. We need a technique like this - the script to be loaded the last - so that we don't get any errors in case that any elements or styles was not found by JS at any point.

<br>

## `defer` attribute

```js
<head>
  <script src="script.js" defer></script>
</head>
```

When the HTML parser reach the `script` element with the `defer` attribute, it loads the script (asynchronously), but defers the execution of the JavaScript until the rest of the elements in the HTML file are parsed, the HTML parsing is not interrupted.

- `DOMContentLoaded` event gets fired after the whole script has been downloaded and executed.
- `defer` guarantees that the scripts are executed in the order they appear in the code.

<div></div>

- When `defer` is useful? When the script contains functionality that requires interaction with the DOM.
- Why? So that JavaScript will not return any error in case it didn't find any elements or styles.

<br>

## `async` attribute

```js
<head>
  <script src="script.js" async></script>
</head>
```

With the `async` attribute, scripts are downloaded asynchronously, the HTML parsing is not interrupted while scripts are downloaded.

But then when the script has been downloaded, it will execute immediately in a synchronous way, so that HTML parsing will wait for the script to execute first.

- `DOMContentLoaded` event usually waits for all scripts to execute, but in case for scripts loaded with async, it will fire as soon as the HTML finishes parsing, without waiting for the scripts to be downloaded and executed.
- `async` scripts are not guaranteed to be executed in the exact order they appear in the code. The script that arrives first, gets executed first.
- When `async` is useful? For scripts that are independent and don't need to interact with your own code.
