# Practical aspects in React

## JavaScript within the Render Method (Conditionals)

We can write JS directly in the `render` method, before `return` statement.

_Practical use cases:_

- When we need a **local variable** later in the JSX code.
- Use an **`if` statement** to conditionally render the markup.
- Render Conditionally from Props.
- Use the **`&&` operator** we check if a condition is true and then return a markup.
- Use the ternary operator for conditions directly inside JSX code.
- Render Inline CSS conditionally based on component state.

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

_Example:_ in a "To Do List" app we render dynamically the current number of items using the `map` function.

```js
class Comp extends React.Component {
  constructor(props) {
    super(props);
    this.state = { arr: ["dog", "cat", "fox"] };
  }

  render() {
    const string = this.state.arr.map((item) => item).join(", ");
    return <p>{string}</p>;
  }
}
```

Using the `join()` method we merge the returned array in one single string.

<br>

## Give Sibling Elements a Unique Key Attribute

When we create an array of elements, each one needs a `key` attribute set to a unique value. React uses these keys to keep track of which items are added, changed, or removed. This helps make the re-rendering process more efficient when the list is modified in any way.

_Note:_ Keys only need to be unique between sibling elements, they don't need to be globally unique in your application.

```js
const data = [];
class Comp extends React.Component {
  render() {
    const list = data.map((item, i) => <li key={i}>{item}</li>);
    return <ul>{list}</ul>;
  }
}
```

<br>

## Use Array.filter() to Dynamically Filter an Array

Besides `map`, another useful array method in React: using `filter` we can filter the content of an array based on a condition and return a new array.

_Example:_ an array of users, filder only those users that are online.

```js
const users = [];

class Comp extends React.Component {
  render() {
    const onlineUsers = users.filter((user) => user.online === true);
    const markup = onlineUsers.map((item, i) => <li key={i}>{item.name}</li>);

    return <ul>{markup}</ul>;
  }
}
```

<br>

## Render React on the Server with renderToString

Since React is a JavaScript view library and you can run JavaScript on the server with Node, we can render a React component on the server using the `renderToString()` method.

The `renderToString()` method is provided on `ReactDOMServer`, which is available as a global object. The method takes one argument which is the React component.

```js
class App extends React.Component {
  render() {
    return null;
  }
}

ReactDOMServer.renderToString(<App />);
```

_Why rendering on the server with React?_

1. Without doing this, your React apps would consist of a relatively empty HTML file and a large bundle of JavaScript when it's initially loaded to the browser. This may not be ideal for search engines that are trying to index the content of your pages so people can find you. If you render the initial HTML markup on the server and send this to the client, the initial page load contains all of the page's markup which can be crawled by search engines.

2. Faster initial page load experience because the rendered HTML is smaller than the JavaScript code of the entire app. React will still be able to recognize your app and manage it after the initial load.

<br>
