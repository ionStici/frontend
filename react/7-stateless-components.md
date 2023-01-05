# **Stateless Components from Stateful Components**

<br>

## **Stateless Components Inherit From Stateful Components**

```JSX
class Child extends React.Component {
    render() {
        return <h1>{this.props.h1}</h1>;
    }
}

class Parent extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            h1: "Main Heading"
        }
    }

    render() {
        return <Child h1={this.state.h1} />
    }
}

```

**Programming Pattern** - Two React components, one stateless (no state), inherits from another stateful (state defined) component.

<br>

## **Stateless Child Components Update Their Parents' state**
