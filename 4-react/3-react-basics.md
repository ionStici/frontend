# **React**

**React.js** is a JavaScript library (developed by engineers at Facebook).

Why React: fast, modular, scalable, flexible, popular.

<br>

## **Table of Content**

- [Intro to JSX](#intro-to-jsx)
- [JSX Elements](#jsx-elements)
- [Nested JSX and Outer Elements](#nested-jsx-and-outer-elements)
- [Rendering JSX](#rendering-jsx)
- [Virtual DOM](#virtual-dom)
- [class vs className](#class-vs-classname)
- [Self-Closing Tags](#self-closing-tags)
- [Curly Braces in JSX](#curly-braces-in-jsx)
- [Variables in JSX](#variables-in-jsx)
- [Event Listeners in JSX](#event-listeners-in-jsx)
- [JSX Conditionals: `if` statement](#jsx-conditionals-if-statement)
- [JSX Conditionals: The Ternary Operator](#jsx-conditionals-the-ternary-operator)
- [JSX Conditionals: `&&`](#jsx-conditionals)
- [`.map` in JSX](#map-in-jsx)
- [Key](#key)
- [React.createElement](#reactcreateelement)

<br>

## **Intro to JSX**

**JSX** is a syntax extension for JavaScript written to be used with React (looks like HTML).

_Syntax extension_ in this case means that JSX is not valid JS, web browsers will not understand it.

JS files that contains JSX code, before reaching a web browser, must first be compiled.

A JSX compiler translates JSX code into regular JavaScript.

<br>

## **JSX Elements**

```JSX
<h1>Hello</h1>  // a JSX element
```

A basic unit of JSX is called a JSX element. The difference between HTML and JSX here, is that this code is found in a JS file, instead of an HTML file.

JSX elements are treated as JavaScript expressions. That means that a JSX element can be saved in a variable, passed to a function, stored in an object or array.

```JSX
const h1 = <h1 className="heading-1" id="h1">Hello</h1>

const obj = {
    myName: <p>Ion</p>,
}
```

We specify the html attributes as usual.

<br>

## **Nested JSX and Outer Elements**

If a JSX expression takes up more than one line, then you must wrap it in parentheses.

But, consider that any JSX expression must have exactly one outer (parent) element.

```JSX
const list = (
    <ul>
        <li>Hello</li>
        <li>Hey</li>
    </ul>
);
```

<br>

## **Rendering JSX**

Render a JSX expression on screen.

```JSX
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
    <h1>Hello World</h1>,
    document.querySelector('div')
);
```

`ReactDOM` is a JS library that contains React-specific methods which deals with the DOM.

`ReactDOM.render()` is a method for rendering JSX. It takes a JSX expression, creates a corresponding tree of DOM nodes, and adds that tree to the DOM.

- The **first argument** of `render()` method, is the JSX expression which we want to render.
- The **second argument** is the element to which the JSX expression is appended.

_p.s. The first argument could also be a variable, so long as that variable evaluates to a JSX expression._

<br>

## **Virtual DOM**

`ReactDOM.render()` only updates DOM elements that have been changed.

If you render the exact same thing twice in a row, the second render will do nothing.

<br>

## **class vs className**

To set a `class` attribute in JSX, we use `className` keyword instead:

```JSX
<h1 className="heading-1">Hello</h1>
```

<br>

## **Self-Closing Tags**

In JSX, for self-closing tags it is mandatory to include a forward-slash immediately before the final angle-bracket:

```JSX
<img src="./img.jpg" />
```

<br>

## **Curly Braces in JSX**

By wrapping code in curly braces inside a JSX expression, we can convert text to JS code:

```JSX
<p>{10 + 5}</p>  // 15
```

The curly braces themselves won't be treated as JSX nor as JS. They are markers that signal the beginning and end of a JS injection into JSX.

<br>

## **Variables in JSX**

We can access JS variables while inside of a JSX expression:

```JSX
const yourName = 'Joe';
const hello = <p>Hello, {yourName}</p>;

const imgData = {
    source: './img.jpg',
    description: 'Someone',
    imgClass: 'img',
    length: '250px',
}

const me = (
    <img
        src={imgData.source}
        alt={imgData.description}
        className={imgData.imgClass}
        width={imgData.length}
    />
);
```

When writing JSX, it's a common practice to use variables to set attributes.

<br>

## **Event Listeners in JSX**

Add event listeners by giving JSX elements special attributes:

```JSX
const myFunc = function() {...};
<button onClick={myFunc}>Click</button>
```

The event listener attribute's name should contain the word `on` plus the type of the event. [Supported Events](https://reactjs.org/docs/events.html#supported-events).

Then the event listener attribute's value would be a predefined function.

In JSX, event listener names are written in camelCase.

<br>

## **JSX Conditionals: `if` statement**

You can not inject an `if` statement into a JSX expression.

But we can create an `if` statement and then based on conditions, define a JSX expression.

```JSX
let myName;

if (true) {
    myName = <p>Mike</p>;
}
```

<br>

## **JSX Conditionals: The Ternary Operator**

```JSX
const p = (
    <p> { true ? 'First' : 'Second' } </p>
);
```

<br>

## **JSX Conditionals: `&&`**

```JSX
const p = {true && <p>Hello</p>};
```

<br>

## **`.map` in JSX**

Creating a list in JSX with `.map` array method:

```JSX
const arr = ['Dog', 'Note', 'Cactus'];

const list = arr.map(i => <li>{i}</li>);
<ul>{list}</ul>
```

After `map` is executed, `list` will be an array.

In JSX, it is acceptable to insert an array of tags into another tag.

<br>

## **Key**

A `key` is a JSX attribute. The attribute's value should be something unique, similar to an `id` attribute.

React uses them internally to keep track of lists.

You should always use `key` if: **1.** The list-items have memory from one render to the next. **2.** A list’s order might be shuffled.

Each `key` must be q unique string that Reac can use to correctly pair each rendered element with its corresponding item in the array.

```JSX
<li key="item_1">Example 1</li>
<li key="item_2">Example 2</li>
```

<br>

## **React.createElement**

We can write React code without using JSX at all.

The following JSX expression:

```JSX
const h1 = <h1>Hello world</h1>;
```

can be rewritten without JSX:

```JSX
const h1 = React.createElement(
    'h1',
    null,
    'Hello world'
);
```

When a JSX element is compiled, the compiler transforms the JSX element into `React.createElement()` method by calling it.
