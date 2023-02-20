[&larr; Back](./README.md)

# React Components

React applications are made out of components.

A component is a reusable chunk of code that is responsible for one specific job.

<br>

## Import React

```JSX
import React from 'react';
import ReactDOM from 'react-dom/client';
```

This imports two objects named `React` and `ReactDOM`, which contains React-related methods.

- `React` contains methods only for pure React purposes.
- `ReactDOM` contains methods meant for interacting with the DOM.

<br>

## Create a Component Class

- We create a React component using JavaScript classes or functions.
- We use React class components to render as many instances of that component as we want.
- We declare a new React class component by extending the `Component` subclass from the `React` library.
- This will give the class component access to many useful React features.
- The body of the component class will act as a set of instructions on how to build the component.

```JS
class ComponentClass extends React.Component {
    constructor(props) {
        super(props);
    }

    render() {
        return (<div><h1>Hello</h1></div>);
    }
}

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<ComponentClass />);
```

To make sure that the component is initialized properly, inside the `constructor` method we must call the `super(props)` method which will in turn call the `constructor` of the parent class `React.Component`.

The `render` method inside the component class should return a JSX expression.

Component classes act as regular JS classes, we ca use everything generally.

Event handlers should be defined as methods of the component class

Using the class name inside angle brackets will **create a component instance**: `<ComponentClass />`

To **render** the component instance, we call `render` on the root element and pass in the class component. This outer `render` function will call the component's `render` method, which in turn will return the JSX element.

<br>

## A Component Render another Component (Composition)

Within the `render` method we can return other component instances as well.

```JSX
import { NavBar, CtaComp } from './Comps.js';

class Header extends React.Component {
    render() {
        return (
            <header>
                <NavBar />
                <CtaComp />
            </header>
        );
    };
};
```

Nesting components within other components is the fundamental relationship of React.

<br>
