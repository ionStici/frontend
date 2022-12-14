# **React**

<br>

**React.js** is a JavaScript library. It was developed by engineers at Facebook.

- React is fast. Apps made in React can handle complex updates and still feel quick and responsive.
- React is modular. Instead of writing large, dense files of code, you can write many smaller, reusable files. React’s modularity can be a beautiful solution to JavaScript’s maintainability problems.
- React is scalable. Large programs that display a lot of changing data are where React performs best.
- React is flexible. You can use React for interesting projects that have nothing to do with making a web app. People are still figuring out React’s potential. There’s room to explore.
- React is popular. While this reason has admittedly little to do with React’s quality, the truth is that understanding React will make you more employable.

<br>

## **Intro to JSX**

**JSX** is a syntax extension for JavaScript written to be used with React (looks like HTML).

_Syntax extension_ in this case means that JSX is not valid JS, web browsers will not understand it.

JS files that contains JSX code, before reaching a web browser, must first be compiled.

A JSX compiler translates JSX code into regular JavaScript.

<hr>

### **JSX Elements**

A JSX element:

```JSX
<h1>Hello</h1>
```

A basic unit of JSX is called a JSX element. The difference between HTML and JSX here, is that this code is found in a JS file, instead of an HTML file.

JSX elements are treated as JavaScript expressions.

That means taht a JSX element can be saved in a variable, passed to a function, stored in an object or array.

```JSX
const h1 = <h1>Hello</h1>

const obj = {
    myName: <p>Ion</p>,
}
```

<br>

### **Attributes in JSX**

```JSX
const h1 = <h1 className="heading-1" id="h1">Hello</h1>;
```

<br>

### **Nested JSX and Outer Elements**

If a JSX expression takes up more than one line, then you must wrap it in parentheses.

But, consider that any JSX expression must have exactly one outer (parent) element.

```JSX
const btn = (
    <ul>
        <li>Hello</li>
        <li>Hey</li>
    </ul>
);
```

<br>

### **Rendering JSX**

To render a JSX expression means to make it appear on screen.

```JSX
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
    <h1>Hello World</h1>,
    document.querySelector('div')
);
```

`ReactDOM` is the name of a JS library which contains several React-specific methods which deals with the DOM, first we import these methods.

`ReactDOM.render()` is a method for rendering JSX. It takes a JSX expression, creates a corresponding tree of DOM nodes, and adds that tree to the DOM.

- The **first argument** of `render()` method, is a JSX expression which will be rendered on the screen.
- The **second argument** is the element to which the first argument is appended.

_p.s. The first argument could also be a variable, so long as that variable evaluates to a JSX expression._

<br>

### **Virtual DOM**

`ReactDOM.render()` only updates DOM elements that have changed.

If you render the exact same thing twice in a row, the second render will do nothing.

<br>

### **class vs className**

To set a `class` attribute in JSX, we use `className` keyword instead:

```JSX
<h1 className="heading-1">Hello</h1>
```
