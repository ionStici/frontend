[&larr; Back](./README.md)

# State

## Table of Content

- [this.state](#thisstate)
- [Setting initial state](#setting-initial-state)
- [Update state with `this.setState`](#update-state-with-thissetstate)

<br>

## **this.state**

React components will often need dynamic information (information that can change) in order to render.

There are two ways for a React Component to access dynamic information: `props` and `state`.

Besides `props` and `state`, every value in a component should always stay exactly the same.

<br>

## Setting initial state

```JSX
class Example extends React.Component {

    contructor(props) {
        super(props);
        this.state = { age: 25 }
    }

    render() {
        return <p>{this.state.age}</p>;
    }
}
```

To make a component have `state`, we define the `state` property inside the `constructor` method, like above example. `this.state` should be equal to an object.

React components always have to call super in their constructors to be set up properly.

Then we can access state from our class as usual: `this.state.name-of-property`.

<br>

## Update state with `this.setState`

A component changes its state by calling the function:

```JSX
this.setState({age: 26});
```

This `setState` function takes 2 arguments: an object that will update the component's state and a callback (which you basically never need).

By calling this function like above with an object, it merges that object with the component's current state. If there are properties in the current state that aren’t part of that object, then those properties remain how they were.

You can’t call this.setState() from inside of the render function.

Note: Any time that you call this.setState(), this function will automatically call .render() as soon as the state has changed. This is also why we can not place setState inside the render function, it will create an infinite loop.

A React app is basically just a lot of components, setting state and passing props to one another.

- A React component should use `props` to store information that can be changed only by another component.
- On the other hand, `state` is used to store information that the component itself can change.

<br>
