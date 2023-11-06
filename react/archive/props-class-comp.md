[&larr; Back](./README.md)

# Props

## Table of Content

- [this.props](#thisprops)
- [Event Handler as a prop](#event-handler-as-a-prop)
- [this.props.children](#thispropschildren)
- [defaultProps](#defaultprops)
- [propTypes](#proptypes)

<br>

## this.props

A component can pass information "props" to another component.

`props` is the name of the object that stores that passed-in information.

Every component has the `props` object that holds information.

We pass `props` to a React component by giving it attributes like real data.

```js
<Comp message="Love You" logIn={false} arr={[1, 2]} />
```

Then, to access `props` inside a component's body, we use the `this.props` object and the name of the attribute that we defined within the component's name.

```js
render() { return <h1>{this.props.message}</h1>; }
```

<br>

## Event Handler as a prop

```js
export class Button extends React.Component {
  render() {
    return <button onClick={this.props.onClick}>Click</button>;
  }
}
```

```js
import { Button } from "./btn.js";

class App extends React.Component {
  handleClick() {
    console.log("Click");
  }

  render() {
    return <Button onClick={this.handleClick} />;
  }
}
```

We provide an event function to a child component as a prop.

Through the `props` object, the child component will use the provided prop as an event handler.

- **Naming Convention**

  _Event Functions:_ keyword `handle` + the type of the event `Click`

  _Props:_ keyword `on` + the type of the event `Click`

<br>

## this.props.children

Optional: components can have a closing tag.

```js
console.log(this.props.children); // Hello
<Comp>Hello</Comp>;
```

The `props` object has a `children` property which will return everything in we pass in between a component's opening and closing JSX tags.

If the component is an self-closing tag, then `children` will be `undefined`.

<br>

## defaultProps

In case a prop is not defined, we can set default props.

```js
Comp.defaultProps = {
  property: "value",
};
```

We append the `defaultProps` property on the component name and set equal to an object.

Inside this object, we write properties for any default prop.

`defaultProps` must be defined before the component is rendered so that it will not override existing props.

If we pass `null` as the value for a prop, it will remain `null` and not use the default property.

<br>

# propTypes

`propTypes` is a type-checking feature. Import the `prop-types` library

```js
import PropTypes from "prop-types";
```

We declare `propTypes` as a static property for our component (after the component has been defined).

```js
Comp.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number.isRequired,
  status: PropTypes.bool.isRequired,
  data: PropTypes.object.isRequired,
  setJob: PropTypes.func.isRequired,
  friends: PropTypes.array.isRequired,
};
```

For each `prop` that the component expects to receive, there can be one property on the `propTypes` object.

- The _name_ of each property in `propTypes` should be the name of an expected `prop`
- The _value_ of each property in `propTypes` should fit this pattern: `PropTypes.expected_data_type`

Each property on the `propTypes` object is called a `propType`.

- `bool` and `func` are abbreviated, but all other data types are spelled normally.
- If we add `isRequired` to a `propType`, we will get a console warning _if that prop isn’t sent._
- In case for function components, propTypes works the same way.

<br>
