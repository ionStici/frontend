[&larr; Back](./README.md)

# State and Props interacting between Components

## Table of Content

- [Stateless Components Inherit from Stateful Components](#stateless-components-inherit-from-stateful-components)
- [Child Components Update Their Parents' state](#child-components-update-their-parents-state)
- [Child Components Update Sibling Components](#child-components-update-sibling-components)

<br>

## Stateless Components Inherit from Stateful Components

Two React Components: a stateful component which passes its state down to a stateless component.

“Stateful” describes any component that has a state property; “stateless” describes any component that does not.

We do this by passing the parent's state as props to the child component.

```jsx
import React from "react";
import ReactDOM from "react-dom";

export class Child extends React.Component {
  render() {
    return <h1>{this.props.name}</h1>;
  }
}

class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { name: "John" };
  }

  render() {
    return <Child name={this.state.name} />;
  }
}
```

- A React component should use props to store information that can be changed, but can only be changed by a different component.
- A React component should use state to store information that the component itself can change.

<br>

## Child Components Update Their Parents' state

```jsx
class Child extends React.Component {
  render() {
    return (
      <button onClick={this.props.onClick}>Click: {this.props.name}</button>
    );
  }
}

class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { keyWord: "Error" };
    this.changeState = this.changeState.bind(this);
  }

  changeState() {
    this.setState({ keyWord: "Hello" });
  }

  render() {
    return <Child name={this.state.keyWord} onClick={this.changeState} />;
  }
}

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<Parent />);
```

1. We define a method on the Parent component that will update the state using `setState`
2. We bind this method to the current instance of the component in its constructor.

   This ensures that when we pass the method to the child component, it will still update the parent component.

3. Then the method is passed to the Child component, which will use it as an event handler.

<br>

## Child Components Update Sibling Components

A child component updates its parent’s state, and the parent passes that state to a sibling component.

Concept: one stateless component display information, and a different stateless component offer the ability to change that information.

```jsx
export class ChildOne extends React.Component {
  render() {
    return <button onClick={this.props.onClick}>Click</button>;
  }
}

export class ChildTwo extends React.Component {
  render() {
    return <p>{this.props.text}</p>;
  }
}

class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { sayHello: "Hello" };
    this.changeState = this.changeState.bind(this);
  }

  changeState() {
    this.setState({ sayHello: "Hello World" });
  }

  render() {
    return (
      <div>
        <ChildOne onClick={this.changeState} />
        <ChildTwo text={this.state.sayHello} />
      </div>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<Parent />);
```

The `ChildOne` component will call the `changeState` method which in turn will call the `setState` method. The `ChildTwo` component will update itself when the `setState` method is invoked because `setState` at the same time will call `render`.

<br>
