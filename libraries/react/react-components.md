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

To **create a component instance**, we write the component class name as a custom HTML tag:

`<ComponentClass />`

To **render** the component instance, we call `render` on the root element and pass in the class component. This outer `render` function will call the component's `render` method, which in turn will return the JSX element.

<br>

## Component Composition

**Component Composition:** a component render other components.

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

A parent component which renders other child component instances. When React encounters a custom HTML tag that references another component, it renders the markup for that component in the location of the tag.

<br>

## Event Handlers in a Component Class

```JSX
class Example extends React.Component {
    clickEvent() {
        console.log('Ow, you clicked me 👋');
    }

    render() {
        return <button onClick={this.clickEvent}>Click</button>;
    }
}
```

We define the event handler function within the component body, then we asign it as value for the `onClick` attribute.

<br>
