[&larr; Back](./README.md)

# State

## Table of Content

- [this.state](#thisstate)
- [Update state with `this.setState`](#update-state-with-thissetstate)
- [Access state in the render method](#access-state-in-the-render-method)
- [Access the previous state](#access-the-previous-state)

<br>

## **this.state**

Two ways for a React Component to access dynamic information: `props` and `state`

Besides `props` and `state`, every value in a component should always stay exactly the same.

```js
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = { keyWord: "Click" };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState({ keyWord: "Clicked!" });
  }

  render() {
    return <button onClick={this.handleClick}>{this.state.keyWord}</button>;
  }
}
```

For a component to have `state`, we define the property `this.state` inside the `constructor` and set equal to an object.

We access properties from the state object as usual: `this.state.property-name`

<br>

## Update state with `this.setState`

We can change the state of a component by calling the `setState()` function.

This `setState` function takes 2 arguments: an object that will update the component's state and a callback (which you basically never need).

_First argument:_ an object with key-value pairs. The keys are your state properties and the values are the updated state data.

By calling this function with an object, it merges that object with the component's current state. If there are properties in the current state that aren’t part of that object, then those properties remain how they were.

You can’t call `this.setState()` from inside of the render function.

React expects you to never modify state directly, instead always use `this.setState()` when state changes occur.

Note: Any time that you call `this.setState()`, this function will automatically call `render()` as soon as the state has changed. This is also why we can not place `setState` inside the render function, it will create an infinite loop.

- A React component should use `props` to store information that can be changed only by another component.
- On the other hand, `state` is used to store information that the component itself can change.

A React app is basically just a lot of components, setting state and passing props to one another.

When `state` data updates, it triggers a re-render of the components using that data - including child components that received the data as a prop.

React updates the actual DOM only where necessary. This means you don't have to worry about changing the DOM. You simply declare what the UI should look like.

Note: `state` is completely encapsulated to its component (unless you pass `state` data to a child component as `props`).

<br>

## Access state in the render method

In the `render()` method, before the `return` statement, we can write JavaScript directly. For example: we can declare functions, access data from `state` and `props`, performs computations of this data, etc.

```js
class Comp extends React.Component {
  // ...

  render() {
    const name = this.state.name;
    return <h1>{name}</h1>;
  }
}
```

<br>

## Access the previous state

We should not rely on the previous value of `this.state` or `this.props` when calculating the next value.

Instead, we should pass to `setState` a function which can access `state` and `props`.

Using a function with `setState` guarantees we are working with the most current values of state and props.

```js
this.setState((state, props) => ({ counter: state.counter + 1 }));
```

Note: we wrap the object literal in parentheses.

<br>
