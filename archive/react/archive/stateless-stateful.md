# State and Props interacting between Components

## Table of Content

- [Stateless Components Inherit from Stateful Components](#stateless-components-inherit-from-stateful-components)
- [Bind `this` to a Class method](#bind-this-to-a-class-method)
- [Child Components Update Their Parents' state](#child-components-update-their-parents-state)
- [Child Components Update Sibling Components](#child-components-update-sibling-components)

<br>

## Stateless Components Inherit from Stateful Components

- “Stateful” describes any component that has a state property;
- “Stateless” describes any component that does not.

A child component can access the state of its parent component through props.

```js
const Child = (props) => <h1>{this.props.name}</h1>;

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

- `props` for storing information that can be changed only by a different component.
- `state` for storing information that the component itself can change.

<br>

## Bind `this` to a Class method

A class method typically needs to use the `this` keyword so it can access properties on the class (such as `state` and `props`) inside the scope of the method.

To do this, we have to explicitly bind `this` in the constructor so `this` becomes bound to the class methods when the component is initialized.

Otherwise, inside the class method `this` will be `undefined`.

```js
class Comp extends React.Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    // ...
  }
}
```

<br>

## Child Components Update Their Parents' state

```js
const Child = (props) => {
  return <button onClick={props.onClick}>{props.name}</button>;
};

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
```

1. We define a method on the Parent component that will update the state using `setState`

2. We bind this method to the current instance of the component in its constructor.

   This ensures that when we pass the method to the child component, it will still update the parent component.

3. Then the method is passed to the Child component, which will use it as an event handler.

<br>

## Child Components Update Sibling Components

A child component updates its parent’s state, and the parent passes that state to a sibling component.

_Concept:_ one stateless component display information, and a different stateless component offer the ability to change that information.

```jsx
const ChildOne = (props) => <button onClick={props.onClick}>Click</button>;
const ChildTwo = (props) => <p>{props.text}</p>;

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
```

The `ChildOne` component will call the `changeState` method which in turn will call the `setState` method. The `ChildTwo` component will update itself when the `setState` method is invoked because `setState` at the same time will call `render`.

<br>
