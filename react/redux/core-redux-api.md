[&larr; Back](./README.md)

# Core Redux API

## Table of Content

- [Introduction / Terminology](./intro.md)

<div></div>

- [createStore](#createstore)
- [Action Objects and Action Creators](#action-objects-and-action-creators)

<div></div>

<br>

## createStore

```js
// npm install redux
import { createStore } from "redux";

const initialState = true;
const reducer = (state = initialState, action) => state;

const store = createStore(reducer);
```

Create the `store` object using the `createStore` helper function. It receives the reducer function as its only argument.

- The **`store`** object holds the entire state of an application.
- It provides useful methods for interacting with its state.

<br>

## Action Objects and Action Creators

- State updates are triggered by _dispatching actions_.
- **Actions** are object that contain information about a desired action event.

<div></div>

1. Action Objects must contain the `type` property equal to a string that reflects the type of a planned event.
2. And then optionally a `payload` property with some data which is sent to the `store`.

```js
const action = { type: "addTodo", payload: "do that" };
```

### Action Creators

**Action Creators** are functions that create and return action objects.

Action Creators are called and passed directly to the `store.dispatch()` method.

```js
const toggle = () => ({ type: "toggle" });
store.dispatch(toggle());
```

Before the reducer of an application is even written, we should write action creators as a way of planning out which actions will be available to dispatch to the store.

### Common Practice

Assign action types as read-only constants, then reference these constants wherever they are used.

```js
const TOGGLE_LIST = "toggle";
const toggle = () => ({ type: TOGGLE_LIST });
```

_Convention:_ write these constants in uppercase and underscores.

<br>
