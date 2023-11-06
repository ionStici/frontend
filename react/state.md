# The useState Hooks

React Hooks are functions that let us manage the internal state of components and handle post-rendering side effects directly form our functional components.

<br>

## Update Function Component State

The _State Hook_ is a named export from the React library.

```jsx
import React, { useState } from "react";

function App() {
  const [count, setCount] = useState(1);

  const handleClick = () => {
    setCount(count + 1);
  };

  return <button onClick={handleClick}>Number: {count}</button>;
}
```

`useState()` is a function that returns an array with 2 values that we destructure.

1. _current state_ - the current value of this state.
2. _state setter_ - a function that we can use to update the value of this state.

As argument to `useState()`, we can pass the _initial value_ of this piece of state, that will be used during the first render.

If we don't pass an initial value to `useState()` then it will result in `undefined` during the first render, instead we should explicitly pass `null`.

By updating the value of state using the state setter, we trigger a component re-render.

`useState()` allows react to keep track of the current state from one render to the next.

We can make as many calls to `useState()` as we want. It's recommended to split the state into multiple state variables, each responsible for its part of the application.

Follow this pattern for naming the state and setter: `[toggle, setToggle]`

<br>

## Previous State

```jsx
function App() {
  const [count, setCount] = useState(1);
  const increment = () => setCount((prev) => prev + 1);

  return <button onClick={increment}>Increment: {count}</button>;
}
```

- The state setter callback function receives the previous state value as an argument.
- The value returned by this state setter callback will be used as the next state value.

<br>

## Arrays in State

JavaScript arrays are the best data model for managing and rendering JSX lists.

```jsx
const arr = [1, 3, 5, 7];

function App() {
  const [nums, setNums] = useState([9, 12]);

  const handleClick = () => useState((prev) => [...arr, ...prev]);

  return <button onClick={handleClick}>{nums.join(" ")}</button>;
}
```

We define an `arr` _static data model_ outside of our function component since it doesn't need to be recreated each time our component re-renders.

Then, the `nums` array contains _dynamic data_, meaning that it changes.

When updating an array in state, we do not just add new data to the previous array, instead we replace the previous array with a brand new array. This means that any information that we want to save from the previous array needs to be explicitly copied over to our new array.

<br>

## Objects in State

```jsx
function App() {
  const [pair, setPair] = useState({});

  const handleClick = (name, value) => {
    setPair((prev) => ({ ...prev, name: value }));
  };
}
```

When updating the object with new data, first we copy the values from the previous object and only then we set more values, the same technique as when working with arrays.

<br>
