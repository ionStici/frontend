[&larr; Back](./README.md)

# React Forms

In a React form, the server should know about every new character or deletion, as soon as it happens. That way, your screen will always be in sync with the rest of your application. We want to update the server any time a user enters or deletes any character.

Unlike in the traditional form paradigm, in React we re-send the form on every single character change. This removes the need to ever “submit” anything.

<br>

## Input onChange

```jsx
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = { userInput: "", submit: "" };

    this.handleUserInput = this.handleUserInput.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleUserInput({ target }) {
    this.setState({ userInput: target.value });
  }

  handleSubmit(event) {
    event.preventDefault();
    this.setState({ submit: this.state.userInput });
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <input
          type="text"
          value={this.state.userInput}
          onChange={this.handleUserInput}
        />

        <h2>{this.state.userInput}</h2>
        <h2>{this.state.submit}</h2>
      </form>
    );
  }
}
```

Input fields maintain their own state in the DOM as the user types. With React, you can move this mutable state into a React component's `state`. The user's input becomes part of the application `state`, so React controls the value of that input field. Typically, if you have React components with input fields the user can type into, it will be a controlled input form.

<br>

## Controlled vs Uncontrolled

- An **uncontrolled component** is a component that maintains its own internal state.
- A **controlled component** is a component that does not maintain any internal state.

The fact that `<input />` keeps track of its own information makes it an uncontrolled component. It maintains its own internal state, by remembering data about itself.

A controlled component, on the other hand, has no memory. If you ask it for information about itself, then it will have to get that information through props. Most React components are controlled.

In React, when you give an `<input />` a value attribute, then something strange happens: the `<input />` BECOMES controlled. It stops using its internal storage. This is a more ‘React’ way of doing things.

More information about controlled and uncontrolled components in the [React Forms Documentation](https://reactjs.org/docs/forms.html)

<br>
