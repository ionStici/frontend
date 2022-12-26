# **Components interacting**

## **Table of Content**

- []()

<br>

## **A Component Render another Component**

Render methods can return component instances as well.

```JSX
import { NavBar } from './NavBar.js';
import { CtaComp } from './CtaComp.js';

class Header extends React.Component {
    render() {
        return (
            <header>
                <NavBar />
                <h1>Hello World</h1>
                <CtaComp />
            </header>
        );
    };
};
```

Nesting components inside of other components - complex architectures - the fundamental relationship of React.js.

<br>

## **this.props**

A component can pass information to another component.

Information that gets passed from one component to another is known as “props".

Terminology:

- `props` is the name of the object that stores passed-in information.
- `this.props` refers to that storage object.
- At the same time, each piece of passed-in information is called `a prop`.

### **Access a Component's props**

Every component has something called `props`. A component's `props` is an object. It holds information about that component.

```JSX
render() {
    console.log(this.props);
    return '';
}
```

### **Pass `props` to a Component**

We can pass information to a React component by giving it attributes like real data:

```JSX
<MyComponent message="Love you" num={10} user={false} arr={[1, 2, 3]} />
```

We pass information to a component by defining an attribute name and then the data.

The values that aren't strings must be wrapper in curly braces.

### **Render a Component's props**

To access props, inside the component's body, use `this.props` + the name of the attribute:

```JSX
render() {
    return this.props.message;
}
```

Common practice to render a component instance from another component, and also defining the props from that parent component.

### **Make decision with props**

```JSX
if (this.props.age >= 25) return 'Sir';
```

### **Event Handler in a Component Class**

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

First, we define our event handler function, then we asign it as value in the `onClick` attribute.

### **Pass and Receive an Event Handler as a prop**

```JSX
export class Button extends React.Component {
    render() {
        return <button onClick={this.props.click}>Click</button>;
    }
}
```

```JSX
import { Button } from 'btn.js';

class Example extends React.Component {
    click() {
        console.log('Click');
    }

    render() {
        return <Button click={this.click} />;
    }
}

ReactDOM.render(
    <Example />,
    document.querySelector('main')
);
```

First we define the event function in our importing component class.

Then we attach the event handler in the Button component, like: `onClick={this.props.click}`.

Finally, we render our Button component and also provide the event function so that Button could access it.
