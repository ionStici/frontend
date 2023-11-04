# React

[**React**](https://react.dev/) is a declarative JavaScript library for building UIs.

Why React? Fast, modular, scalable, flexible, popular.

<br>

## New React App

```
npm create vite@latest my-app
```

### Predefined Scripts

- `npm run dev` starts the development server.

- `npm run build` bundles the app into static files for production.

- `npm run preview` preview the production version of the app.

### Directory Structure

- `public/` for static assets.

- `src/` contains the actual application code.

- `package.json` contains descriptive and functional metadata about a project.

- `package-lock.json` contains the dependency tree installed in node_modules/.

- `node_modules/` contains dependencies and sub-dependencies used by React.

<br>

## JSX

**JSX** is a syntax extension for JavaScript, it allows developers to declaratively create HTML elements in JavaScript by writing HTML markup code directly inside of JavaScript files.

```jsx
<h1>Hello</h1> // a JSX element
```

JSX elements are treated as JS expressions, which means that we can store them in variables.

```jsx
const h1 = <h1 id="h1">Hello</h1>;
```

JSX elements accept html attributes just like HTML elements do.

_p.s. We can think of JSX elements as built-in react components._

<br>

## Babel Transformation

Before reaching the browser, JSX code is compiled into regular JavaScript objects that create HTML elements on the page.

This piece of JSX code:

```jsx
// JSX
const element = <h1>Hello, World!</h1>;
```

Is transformed by Babel into this:

```js
// JS
const element = React.createElement("h1", null, "Hello, World!");
```

<br>

## Nested JSX and Outer Elements

```JSX
const list = (
    <ul>
        <li>JSX</li>
        <li>React</li>
    </ul>
);
```

JSX rules:

1. If a JSX expression takes up more than one line, then you must wrap it in parentheses.
2. Any JSX expression must have exactly one outer (parent) element.

<br>

## className

To set a `class` attribute in JSX, we use the `className` keyword instead.

```jsx
<h1 className="heading-1">Hello</h1>
```

<br>

## Self-Closing Tags

In JSX, for self-closing tags, it is mandatory to include a forward-slash before the final angle-bracket.

```JSX
<img src="/img.jpg" />
```

<br>

## Curly Braces in JSX

Code within curly braces inside a JSX expression will be treated as JS code.

They mark the beginning and the end of a JS injection into JSX.

```jsx
const myName = "John";
const hello = <p>Hello, {myName}</p>;
```

<br>

## React Components

React apps are built by creating and combining multiple components.

React components are simply functions that fulfill 2 rules:

1. Must start with an uppercase character
2. Must return JSX or `null`

```jsx
function App() {
  return <h1>Hello, World!</h1>;
}
```

Besides returning, we can have any JavaScript logic inside function components.

Separation of concerns: One component per file, which, by using JSX, combines HTML, CSS and JS in one single block of code.

<br>

## Rendering a Component

```jsx
// index.jsx
import React from "react";
import ReactDOM from "react-dom/client";

function App() {
  const text = "Hello, React!";
  return <h1>{text}</h1>;
}

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

- The `React` and `ReactDOM` libraries are imported.

- A functional component named `App` is defined.

- `ReactDOM.createRoot()` creates the root DOM node.

- The `render()` method is called on the `root` obhect, which mounts the `App` component to the DOM.

- `<React.StrictMode>` is an optional utility component that helps detect potential problems.

_Virtual DOM note:_ `render` only updates DOM elements that have been changed.

<br>
