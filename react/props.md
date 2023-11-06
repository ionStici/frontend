# Props

A component can pass data "props" to another inner component.

`props` is the name of the object that stores the passed data.

To pass `props`, we simply define key / value pairs

inside the component's angle brackets.

```jsx
function App() {
  return <User name="John" logIn={true} nums={[7, 3]} />;
}

function User(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

To access `props` inside a component's body, first we specify the `props` parameter, then we access the data using the pattern: `props.propertyName`.

`props` are read-only, they are **immutable**. If you need to mutate props, then you should use **state**.

React uses a one-way data flow approach, which means that data can only be passed from parent components to child components, and not the other way around.

<br>

## Event Handler as Props

<br>

## Destructuring Props

```jsx
function Header({ userData }) {}
```

<br>
