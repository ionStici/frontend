[&larr; Back](./README.md)

# JavaScript Basics

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
