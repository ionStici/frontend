[&larr; Back](./README.md)

# Function Components and Hooks

## Table of Content

- [Function Components](#function-components)
- [Function Components and Props](#function-components-and-props)

<br>

## Function Components

**Function Components:** We can define components as JavaScript functions.

In practice: We remove the `render` method and return the same JSX as a class component.

```js
// CLASS COMPONENT
class Comp extends React.Component {
  render() {
    return <h1>Hello World</h1>;
  }
}

// FUNCTION COMPONENT
const Comp = () => {
  return <h1>Hello World</h1>;
};
```

## Function Components and Props

Function components also can receive information via `props`.

To access `props`, we give the function a `props` parameter.

Within the function body, we access props using this pattern: `props.propertyName` (no this keyword).

```jsx
const Comp = (props) => {
  return <h1>{props.name}</h1>;
};
```

<br>
