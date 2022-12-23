# **Components interacting**

<br>

## **A Component in a Render Function**

Render methods can return component instances.

A component can render another component.

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
