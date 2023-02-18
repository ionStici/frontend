[&larr; Back](./README.md)

# propTypes

## Introduction

`propTypes` are useful for two reasons

1. _Validation_ can ensure that your `props` are doing what they're supposed to be doing. If `props` are missing, or if they’re present but they aren’t what you’re expecting, then a warning will print in the console.
2. _Documenting_ `props` makes it easier to glance at a file and quickly understand the component class inside. When you have a lot of files this can be a huge benefit.

<br>

## Apply PropTypes

If a component class expects a `prop`, then you can use `propTypes`.

Import the `prop-types` library:

```js
import PropTypes from "prop-types";
```

Then, we declare `propTypes` as a static property for our component (after the component has been defined).

```jsx
Comp.propTypes = {
  name: PropTypes.string,
};
```

For each `prop` that the component expects to receive, there can be one property on the `propTypes` object.

<br>

## Add Properties to PropTypes

- The _name_ of each property in `propTypes` should be the name of an expected `prop`
- The _value_ of each property in `propTypes` should fit this pattern: `PropTypes.expected_data_type`

Each property on the `propTypes` object is called a `propType`.

```jsx
Comp.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number.isRequired,
  status: PropTypes.bool.isRequired,
  data: PropTypes.object.isRequired,
  setJob: PropTypes.func.isRequired,
  friends: PropTypes.array.isRequired,
};
```

`bool` and `func` are abbreviated, but all other data types are spelled normally.

If you add `isRequired` to a `propType`, then you will get a console warning _if that prop isn’t sent._

<br>

## PropTypes in Function Components

```js
function Comp() {
  // ...
}

Comp.propTypes = {
  name: PropTypes.string.isRequired,
};
```

To write `propTypes` for a function component, the process is similar.

<br>
