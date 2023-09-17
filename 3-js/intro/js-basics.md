[&larr; Back](./README.md)

# JavaScript Basics

## Table of Content

- [Strict Mode](#strict-mode)
- [String Interpolation](#string-interpolation)

<br>

## Strict Mode

To active strict mode, include the following string at the beginning of the script:

```js
"strict mode";
```

Strict mode helps developers avoid accidental errors, identify bugs, write secure code.

- Strict mode forbids us to do certain things
- It will create visible errors for us in certain situations
- Introduces a short list of variable names that are reserved for features that might be added to the language latter

<br>

## String Interpolation

We can insert (interpolate) variables into strings using **template literals** (ES6 Feature).

```js
const myName = "John";
let me = `I'm ${myName}`;
console.log(me); // I'm John
```

- A template literal is wrapped by backticks **``**
- Variables are inserted inside curly parentheses `${}` syntax
- We can insert any js expression in the template literal placeholder

Another great use of template literals is to create multi-line strings. Very useful when we build HTML from JS. Before ES6, multi-line strings was more harder to write using `/n/`.

<br>
