[&larr; Back](./README.md)

# Component Lifecycle Methods

<br>

## Table of Content

- [Introduction](#introduction)
- [componentDidMount](#componentdidmount)
- [componentWillUnmount](#componentwillunmount)

<br>

## Introduction

The component lifecycle has three high-level parts:

1. _Mounting:_ when the component is being initialized and put into the DOM for the first time;
2. _Updating:_ when the component updates as a result of changed state or changed props.
3. _Unmounting:_ when the component is being removed from the DOM.

Two common lifecycle methods:

- `constructor()` the first method called during the mounting phase.
- `render()` called later during mounting phase to render the component and during the updating phase to re-render the component.

_A component updates (`render` is invoked):_ if the state changes + if different props are passed to a component.

<br>

## componentDidMount

`componentDidMount()` is the final method called during the mounting phase, it is called after the component is rendered.

_The order is:_ (1) `constructor()` -> (2) `render()` -> (3) `componentDidMount()`.

```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date() };
  }

  render() {
    return <div>{this.state.date.toLocaleTimeString()}</div>;
  }

  componentDidMount() {
    const tick = setInterval(() => this.setState({ date: new Date() }), 1000);
  }
}
```

Another method (not very used): `getDerivedStateFromProps()` is called between the `constructor` and `render`.

<br>

## componentWillUnmount

From the previous code example: when the component is unmounted, the timer will keep on ticking, trying to update the state of a component that's gone. This means that some JavaScript code will run unnecessarily, which will hurt the performance of the app. Generally, this can lead to subtle, annoying bugs. All this bad stuff can happen if we fail to clean up a side-effect of a component. In out code example, what we want is to clear the interval when the component is unmounted.

**In general, when a component produces a side-effect, you should remember to clean it up.**

`componentWillUnmount()` is called in the unmounting phase, right before the component is completely destroyed. It's a useful time to clean up any of your component's mess.

```js
class Clock extends React.Component {
  // code ...

  componentWillUnmount() {
    clearInterval(tick);
  }
}
```

<br>

## componentDidUpdate

An update is caused by changes to props or state.

When a component updates, it calls [several methods](https://reactjs.org/docs/react-component.html#updating), but only two are commonly used.

`componentDidUpdate()` is a good place for update-phase work.

```js
class Clock extends React.Component {
  // code ...

  componentDidUpdate() {
    // ...
  }
}
```

<br>
