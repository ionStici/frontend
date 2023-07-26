[&larr; Back](./README.md)

# Component Lifecycle Methods

## Table of Content

- [Introduction](#introduction)
- [componentDidMount](#componentdidmount)
- [componentWillUnmount](#componentwillunmount)
  - [Cleaning up side effects of event listeners](#cleaning-up-side-effects-of-event-listeners)
- [componentDidUpdate](#componentdidupdate)
- [shouldComponentUpdate](#shouldcomponentupdate)

<br>

## Introduction

React components have several special methods that provide opportunities to perform actions at specific points in the lifecycle of a component.

The component lifecycle has three high-level parts:

1. _Mounting:_ when the component is being initialized and put into the DOM for the first time.
2. _Updating:_ when the component updates as a result of changed state or changed props.
3. _Unmounting:_ when the component is being removed from the DOM.

Two common lifecycle methods:

- `constructor()` the first method called during the mounting phase.
- `render()` called later during mounting phase to render the component and during the updating phase to re-render the component.

_A component updates (`render` is invoked):_ if the state changes + if different props are passed to a component.

Another method (not very used): `getDerivedStateFromProps()` is called between the `constructor` and `render`.

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

- Best practice in React for server calls: inside the lifecycle method `componentDidMount`.
- Because this method is called after the component is mounted to the DOM.
- Any calls to `setState` within this method will trigger a re-rendering of your component.
- Call an API in this method -> set the state with the data returned by the API -> automatically triggers an update once we receive the data.

<br>

## componentWillUnmount

**In general, when a component produces a side-effect, you should remember to clean it up.**

`componentWillUnmount()` is called in the unmounting phase, right before the component is completely destroyed. It's a useful time to clean up any of your component's mess.

```js
class Clock extends React.Component {
  // code ...

  componentDidMount() {
    const tick = setInterval(() => this.setState({ date: new Date() }), 1000);
  }

  componentWillUnmount() {
    clearInterval(tick);
  }
}
```

Code example: When the component is unmounted, the timer define in `componentDidMount` will keep ticking. This can lead to subtle bugs. We should clean ap side-effects of components.

From our example, within the `componentWillUnmount` lifecycle method, is the perfect place to clean any side-effects.

<br>

### Cleaning up side effects of event listeners

```js
class Comp extends React.Component {
  // ...

  componentDidMount() {
    document.addEventListener("keydown", handleKeyPress);
  }

  componentWillUnmount() {
    document.removeEventListener("keydown", handleKeyPress);
  }
}
```

- `componentDidMount` is also the best place to attach event listeners for specific functionalities.
- `componentWillUnmount` will clean up the `keydown` event side effect.

It's good practice to use this lifecycle method to do any clean up on React components before they are unmounted and destroyed. Removing event listeners is an example of one such clean up action.

React provides a synthetic event system, which is great for most interactions with DOM elements.

However, if you want to attach an event handler to the document or window objects, you have to do this directly.

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

## shouldComponentUpdate

If any component receives new `state` or `props`, it re-renders itself and all its children. This is usually okay.

Using `shouldComponentUpdate` method on child components, we can explicitly indicate if the components should update or not (in case they receives new `state` or `props`). This method is a useful way to optimize performance.

`shouldComponentUpdate` takes `nextProps` and `nextState` as parameters.

```js
class Child extends React.Component {
  // ...

  shouldComponentUpdate(nextProps, nextState) {
    if (nextProps.value !== this.state.value) return true;
  }
}
```

`shouldComponentUpdate` method must return a boolean value that tells React whether or not to update the component.

You can compare the current props `this.props` to the nest props `nextProps` to determine if you need to update or not, and return `true` or `false` accordingly.

<br>
