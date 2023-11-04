## Event Listeners in JSX

```JSX
const myFunc = function() { ... };
<button onClick={myFunc}>Click</button>
```

- Event listeners are defined on JSX elements by special attributes: [Supported Events](https://reactjs.org/docs/events.html#supported-events).
- The name of the event listener attribute: The keyword `on` + the event type (in camelCase).
- The value of the event listener attribute would be a predefined function.

<br>

## JSX and Conditionals

- We can define JSX inside **`if` statements** (_note:_ we can't inject `if` into JSX)

  ```JSX
  let myName;
  if (true) { myName = <p>Mike</p>; }
  ```

- **Ternary Operator** (inside JSX)

  ```JSX
  const p = (<p> { true ? 'First' : 'Second' } </p>);
  ```

- **`&&`**

  ```JSX
  const p = {true && <p>Hello</p>};
  ```

<br>

## `map` in JSX

```JSX
const arr = ['Dog', 'Note', 'Cactus'];

const list = arr.map(i => <li>{i}</li>);
<ul>{list}</ul>
```

After `map` is executed, `list` will be an array.

In JSX it is acceptable to insert an array of tags into another tag.

<br>

## Key attribute

A `key` is a JSX attribute. The attribute's value should be something unique, similar to an `id` attribute.

React uses them internally to keep track of lists.

You should always use `key` if:

1. The list-items have memory from one render to the next.
2. The order of the list might be shuffled.

Each `key` must be a unique string that React can use to correctly pair each rendered element with its corresponding item in the array.

```JSX
<li key="item_1">Example 1</li>
<li key="item_2">Example 2</li>
```

<br>
