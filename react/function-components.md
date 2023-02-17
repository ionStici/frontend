[&larr; Back](./README.md)

# Function Components and Hooks

## Table of Content

- [Function Components](#function-components)
  - [Function Components and Props](#function-components-and-props)

<div></div>

- [The State Hook](#the-state-hook)
  - [Update Function Component State](#update-function-component-state)
  - [Initialize State](#initialize-state)
  - [Set From Previous State](#set-from-previous-state)

<div></div>

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

### Function Components and Props

Function components also can receive information via `props`.

To access `props`, we give the function a `props` parameter.

Within the function body, we access props using this pattern: `props.propertyName` (no this keyword).

```jsx
const Comp = (props) => {
  return <h1>{props.name}</h1>;
};
```

<br>

## The State Hook

React Hooks are functions that let us manage the internal state of components and handle post-rendering side effects directly form our function components. Hooks don't work inside classes.

Built-in Hooks: `useState() useEffect() useContext() useReducer() useRef()`. [Full List](https://reactjs.org/docs/hooks-reference.html).

<br>

### Update Function Component State

The _State Hook_ is a named export from the React library, so we import it like this:

```js
import React, { useState } from "react";
```

`useState()` is a JavaScript function defined in the React library. When we call this function, it returns an array with two values:

- _current state_ - the current value of this state.
- _state setter_ - a function that we can use to update the value of this state.

Destructuring this array in to local variables:

```js
const Comp = () => {
  const [toggle, setToggle] = useState();
  setToggle(true);
  return toggle;
};
```

We update the value of `toggle` and re-render the component with this new value by calling the `setToggle` function with the next state value as an argument.

No need to worry about binding functions to call instances, working with constructors, dealing with the `this` keyword.

Calling the state setter signals to React that the component needs to re-render, so the whole function defining the component is called again. The magic of useState() is that it allows React to keep track of the current value of state from one render to the next!

<br>

### Initialize State

To initialize our state with any value we want, we simply pass the initial value as an argument to the `useState()` function call.

```js
const [isLoading, setIsLoading] = useState(true);
```

- During the first render, the initial state argument is used.
- When the state setter is called, React ignores the initial state argument and uses the new value.
- When the component re-renders for any other reason, React continues to use the same value from the previous render.

If we don’t pass an initial value when calling useState(), then the current value of the state during the first render will be undefined.

If we don’t have the value needed during the first render, we should explicitly pass `null` instead of just passively leaving the value as `undefined`.

<br>

### Set From Previous State

```js
const Comp = () => {
  const [count, setCount] = useState(0);
  const increment = () => setCount((prevCount) => prevCount + 1);
  return <button onClick={increment}>Increment</button>;
};
```

- The state setter callback function takes the previous state value as an argument.
- The value returned by this state setter callback function is used as the next state value.

It is best practice to update state with a callback function.

<br>

### Arrays in State

JavaScript arrays are the best data model for managing and rendering JSX lists.

```js
const arr = [1, 3, 5, 7];

function Comp() {
  const [num, setNum] = useState([9, 12]);
  const handleClick = () => useState((prev) => [...arr, ...prev]);
}
```

We define an `arr` _static data model_ outside of our function component since it doesn't need to be recreated each time our component re-render.

Then, the `num` array contains _dynamic data_, meaning that it changes.

When updating an array in state, we do not just add new data to the previous array. We replace the previous array with a brand new array. This means that any information that we want to save from the previous array needs to be explicitly copied over to our new array.

Array methods are very useful when working with data.

```js
// Destructuring the event object directly
const event = ({ target }) => target;
```

<br>

### Objects in State

```js
function Comp() {
  const [pair, setPair] = useState({});

  const handleEvent = (name, value) =>
    setPair((prev) => ({ ...prev, name: value }));
}
```

We define the initial state as an empty object.

The spread syntax is the same for objects as for arrays.

When updating the object with new data, we first copy the values from the previous object and then set the next value of state, the same technique as when working with arrays.

Inside of our state setter callback function, we wrap our curly brackets in parentheses like so: `setPair((prev) => ({ ...prev }))`. This tells JavaScript that our curly brackets refer to a new object to be returned. We use `...`, the spread operator, to fill in the corresponding fields from our previous state. Finally, we overwrite the appropriate key with its updated value.

<br>

### Separate Hooks for Separate States

We can make as many calls to `useState()` as we want.

It’s best to split state into multiple state variables based on which values tend to change together.

```js
function Comp() {
  const [num, setNum] = useState();
  const [name, setName] = useState();
  const [list, setList] = useState();
}
```

<br>
