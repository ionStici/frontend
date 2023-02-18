[&larr; Back](./README.md)

# React Forms

In a React form, you want the server to know about every new character or deletion, as soon as it happens. That way, your screen will always be in sync with the rest of your application.

In a React form, the server should know about every new character or deletion as soon as it happens.

We want to update the server any time a user enters or deletes any character.

Unlike in the traditional form paradigm, in React we re-send the form on every single character change. This removes the need to ever “submit” anything.

<br>

## Input onChange

```jsx
class Comp extends React.Component {
  constructor(props) {
    super(props);
    this.state = { userInput: "" };
    this.handleUserInput = this.handleUserInput.bind(this);
  }

  handleUserInput({ target }) {
    this.setState({
      userInput: target.value,
    });
  }

  render() {
    return (
      <div>
        <input
          value={this.state.userInput}
          type="text"
          onChange={this.handleUserInput}
        />
        <h1>{this.state.userInput}</h1>
      </div>
    );
  }
}
```

<br>

## Controlled vs Uncontrolled

- An **uncontrolled component** is a component that maintains its own internal state.
- A **controlled component** is a component that does not maintain any internal state.

Since a controlled component has no state, it must be controlled by someone else.

`<input />` keeps track of its own text. We can ask it what its text is at any time using `value` property, and it will be able to tell us.

The fact that `<input />` keeps track of information makes it an uncontrolled component. It maintains its own internal state, by remembering data about itself.

A controlled component, on the other hand, has no memory. If you ask it for information about itself, then it will have to get that information through props. Most React components are controlled.

In React, when you give an `<input />` a value attribute, then something strange happens: the `<input />` BECOMES controlled. It stops using its internal storage. This is a more ‘React’ way of doing things.

More information about controlled and uncontrolled components in the [React Forms Documentation](https://reactjs.org/docs/forms.html)

<br>
