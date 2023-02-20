[&larr; Back](./README.md)

# Props

## Table of Content

- [this.props](#thisprops)
- [Pass and Receive an Event Handler as a prop](#pass-and-receive-an-event-handler-as-a-prop)
- [this.props.children](#thispropschildren)
- [defaultProps](#defaultprops)

<br>

## this.props

A component can pass information "props" to another component.

`props` is the name of the object that stores that passed-in information.

Every component has the `props` object that holds information.

We pass `props` to a React component by giving it attributes like real data.

```js
<Comp message="Live You" logIn={false} arr={[1, 2]} />
```

Then, to access `props` inside a component's body, we use the `this.props` object and the name of the attribute that we defined within the component's name.

```js
render() { return <h1>{this.props.message}</h1>; }
```

<br>

## Pass and Receive an Event Handler as a prop

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
