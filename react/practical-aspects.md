[&larr; Back](./README.md)

# Practical aspects in React

## JS in Render Method

We can write JS directly in the `render` method, before `return` statement. Use cases:

- When we need a **local variable** later in the JSX code.
- Use an **`if` statement** to conditionally render the markup.
- Use the **`&&` operator** we check if a condition is true and then return a markup.
- Use the ternary operator for conditions directly inside JSX code.
- Render Conditionally from Props.
- Render Inline CSS conditionally based on component state.

_Note:_ `if` statements can't be inserted directly into JSX code, but ternary operators can.

```js
class Comp extends React.Component {
  // ..

  render() {
    let check;
    if (this.props.isTrue) check = true;
    return (
      <div style={{ color: `${this.state.status ? "red" : "green"}` }}>
        {check && <p>Hello {true ? "World" : ""}</p>}
      </div>
    );
  }
}
```

<br>

## Use Array.map() to Dynamically Render Elements

Using `Array.map()` in React to render an unknown number of elements based on user's interaction with the program.

Example: in a "To Do List" app we render dynamically the current number of items using the `map` function.

```js
class Comp extends React.Component {
  constructor(props) {
    super(props);
    this.state = { arr: ["dog", "cat", "fox"] };
  }

  render() {
    return <p>{this.state.arr.map((item) => item).join(", ")}</p>;
  }
}
```

Using the `join()` method we merge the returned array in one single string.

<br>

## Give Sibling Elements a Unique Key Attribute

<br>
