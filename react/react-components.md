[&larr; Back](./README.md)

# **React Components**

React applications are made out of components.

A component is a small, reusable chunk of code that is responsible for one specific job (usually rendering some HTML).

<br>

## **Import React**

```JSX
import React from 'react';
import ReactDOM from 'react-dom';
```

This imports two objects named `React` and `ReactDOM`, which contains React-related methods:

- `React` contains methods only for pure React purposes.
- `ReactDOM` contains methods meant for interacting with the DOM.

<br>

## **Create a Component Class**

We can create React components with JavaScript classes and functions.

A component class is like a factory that builds components. We use React class components to render as many instances of that component as we want.

With JS classes, to declare a new component class, first we extend the `Component` subclass from the `React` library.

The body of the component class will act as a set of instructions, explaining to the component class how it should build a React component.

```JSX
class ComponentClass extends React.Component {

    get h1HtmlClass() {
        return 'heading-1';
    }

    myFunc() {
        alert("Don't hover me!");
    }

    render() {
        const nothing = 'A random variable';

        return (
            <h1 className={this.h1HtmlClass}>
                <span onHover={this.myFunc}>Hello</span>
                <span>world</span>
            </h1>
        );
    }
}

ReactDOM.render(
    <ComponentClass />,
    document.querySelector('.box')
);
```

In the body of the component class we have a `render` method which usually returns a JSX expression. Use parentheses for multiline JSX expressions.

The component class acts as regular JS classes, so you can use the `this` keyword, conditionals, event listeners, everything generally.

In React, event handlers are defined as methods of the component class.

JSX elements can be either HTML-like or component instances.

To create a Component Instance, we write a JSX element with the name of the component class: `<ComponentClass />`

### **Render a Component**

Now, to render the component instance, we call the component's `render` method by passing the component instance to `ReactDOM.render()` as first argument.

So, `ReactDOM.render()` will call the component instance's `render` method, which in turn will return the JSX element.

Then, the result will be added to the virtual DOM.
