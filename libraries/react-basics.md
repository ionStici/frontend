[&larr; Back](./README.md)

# **React**

**React.js** is a JavaScript library (developed by engineers at Facebook).

Why React: fast, modular, scalable, flexible, popular.

<br>

## **Table of Content**

- [Intro to JSX](#intro-to-jsx)
- [JSX Elements](#jsx-elements)
- [Nested JSX and Outer Elements](#nested-jsx-and-outer-elements)
- [Rendering JSX](#rendering-jsx)
- [class vs className](#class-vs-classname)
- [Self-Closing Tags](#self-closing-tags)
- [Curly Braces in JSX](#curly-braces-in-jsx)
- [Variables in JSX](#variables-in-jsx)
- [Event Listeners in JSX](#event-listeners-in-jsx)
- [JSX and Conditionals](#jsx-and-conditionals)
- [`map` in JSX](#map-in-jsx)
- [Key attribute](#key-attribute)
- [React.createElement](#reactcreateelement)

<br>

## Intro to JSX

**JSX** is a React syntax extension for JavaScript.

Before reaching a browser, the JSX compiler translates JSX code into regular JavaScript.

<br>

## JSX Elements

```JSX
<h1>Hello</h1> // a JSX element
```

**JSX Elements** - a basic unit of JSX.

JSX elements are treated as JS expressions: we can store them in variables or in data structures.

```JSX
const h1 = <h1 id="h1">Hello</h1>
```

We define html attributes as usual.

<br>

## Nested JSX and Outer Elements

```JSX
const list = (
    <ul>
        <li>Hello</li>
        <li>Hey</li>
    </ul>
);
```

1. If a JSX expression takes up more than one line, then you must wrap it in parentheses.
2. Any JSX expression must have exactly one outer (parent) element.

<br>

## Rendering JSX

```JSX
import React from 'react';
import ReactDOM from 'react-dom/client';

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<h1>Hello World</h1>);
```

`ReactDOM` is a JS library that contains React-specific methods which deals with the DOM.

`render()` is a method for rendering JSX, it creates and adds the corresponding tree of nodes to the DOM.

- `render` is appended to the `root` element (created by `createRoot`).
- The argument of `render()` is the JSX expression that will be rendered.

_Virtual DOM:_ `render` only updates DOM elements that have been changed.

_p.s. The argument of `render` can also be a variable, as long as that variable evaluates to a JSX expression._

<br>

## class vs className

To set a `class` attribute in JSX, we use the `className` keyword instead

```JSX
<h1 className="heading-1">Hello</h1>
```

<br>

## Self-Closing Tags

In JSX, for self-closing tags it is mandatory to include a forward-slash immediately before the final angle-bracket

```JSX
<img src="./img.jpg" />
```

<br>

## Curly Braces in JSX

```JSX
<p>{10 + 5}</p>  // 15
```

Code within curly braces inside a JSX expression will be treated as JS code.

They mark the beginning and the end of a JS injection into JSX.

<br>

## Variables in JSX

We can access JS variables while inside of a JSX expression.

```JSX
const myName = 'Joe';
const hello = <p>Hello, {myName}</p>;
```

<br>

## Event Listeners in JSX

```JSX
const myFunc = function() { ... };
<button onClick={myFunc}>Click</button>
```

- Event listeners are defined on JSX elements by special attributes: [Supported Events](https://reactjs.org/docs/events.html#supported-events).
- The name of the event listener attribute: The keyword `on` + the event type (in camelCase).
- The value of the event listener attribute would be a predefined function.

<br>

## JSX and Conditionals

- We can define JSX inside **`if` statements** (_note:_ we can't inject `if` into JSX)

  ```JSX
  let myName;
  if (true) { myName = <p>Mike</p>; }
  ```

- **Ternary Operator** (inside JSX)

  ```JSX
  const p = (<p> { true ? 'First' : 'Second' } </p>);
  ```

- **`&&`**

  ```JSX
  const p = {true && <p>Hello</p>};
  ```

<br>

## `map` in JSX

```JSX
const arr = ['Dog', 'Note', 'Cactus'];

const list = arr.map(i => <li>{i}</li>);
<ul>{list}</ul>
```

After `map` is executed, `list` will be an array.

In JSX it is acceptable to insert an array of tags into another tag.

<br>

## Key attribute

A `key` is a JSX attribute. The attribute's value should be something unique, similar to an `id` attribute.

React uses them internally to keep track of lists.

You should always use `key` if:

1. The list-items have memory from one render to the next.
2. The order of the list might be shuffled.

Each `key` must be a unique string that React can use to correctly pair each rendered element with its corresponding item in the array.

```JSX
<li key="item_1">Example 1</li>
<li key="item_2">Example 2</li>
```

<br>

## React.createElement

We can write React code without using JSX. The following JSX expression:

```JSX
const h1 = <h1>Hello world</h1>;
```

Can be rewritten without JSX:

```JSX
const h1 = React.createElement(
    'h1',
    null,
    'Hello world'
);
```

The JSX compiler transforms JSX elements into `React.createElement()`.

<br>
