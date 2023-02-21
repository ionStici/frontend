[&larr; Back](./README.md)

# Function Components

## Table of Content

- [Function Components](#function-components)
- [Function Components and Props](#function-components-and-props)
- [Array methods in React Components](#array-methods-in-react-components)

<br>

## Function Components

**Function Components:** React components as JavaScript functions.

To create a function component, we simply write a JS function that returns either JSX or `null`.

One important thing to note is that React requires your function name to begin with a capital letter.

```js
const Comp = () => {
  return <h1>Hello World</h1>;
};
```

## Function Components and Props

To access `props`, we give the function a `props` parameter.

Within the function body, we access props using this pattern: `props.propertyName`.

```jsx
const Comp = (props) => {
  return <h1>{props.name}</h1>;
};
```

<br>

## Array methods in React Components

```js
const Comp = (props) => <p>{props.arr.join(" ")}</p>;
```

Array methods such as `join()` can be used directly when accessing a prop array.
