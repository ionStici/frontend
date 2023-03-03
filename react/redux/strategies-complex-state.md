# Strategies for Complex State

## Table of Content

- [Slices](#slices)
- [Actions and Payloads](#actions-and-payloads)
- [Reducer: Immutable Updates](#reducer-immutable-updates)

<br>

## Slices

In a Redux application, the top-level `state` properties are known as **slices**.

Each _slice_ represents a different feature of the entire application.

Most Redux apps, begin with an `initialState` that allows the programmer to do two key things:

1. Plan out the general structure of the state.
2. Provide an initial state value to the reducer function.

```js
const initialState = {
  todos: [
    { id: 0, text: "do this", isComplete: false },
    { id: 1, text: "do that", isComplete: true },
  ],
  visibilityFilter: "SHOW_INCOMPLETE",
  searchTerm: "",
};
```

The `initialState` example above has 3 slices.

<br>

## Actions and Payloads

When an application state has multiple slices, individual actions typically only change one slice at a time. Therefore, each action’s `type` follows the pattern `'sliceName/actionDescriptor'`, to clarify which slice of state should be updated.

In a todo app, the action `type` for adding a new todo might be: `'todos.addTodo'`.

Important to consider which actions will have a `payload` (additional data passed to the reducer in order to carry out the desired change-of-state).

Example of the `searchTerm` slice:

```js
store.dispatch({ type: "searchTerm/setSearchTerm", payload: "homework" });
store.dispatch({ type: "searchTerm/clearSearchTerm" });
```

After we have a clear idea of the app's actions, the next step is to make the action creators.

Action creators enable Redux programmers to re-use action object structures without typing them out by hand and they improve the readability of their code, particularly when dealing with bulky payloads.

```js
const setSearchTerm = (term) => ({
  type: "searchTerm/setSearchTerm",
  payload: "term",
});

const clearSearchTerm = () => ({ type: "searchTerm/clearSearchTerm" });
```

<br>

## Reducer: Immutable Updates

The `store`‘s reducer function is called each time an action is dispatched. It is passed the `action` and the current `state` as arguments and returns the `store`‘s next state.

_Rule of reducers_: when the reducer is updating the `state`, it must make a copy and return the copy rather than directly mutating the incoming `state`. When the state is a mutable data type, like an array or object, this is typically done using the spread operator `...` Example:

```js
const todoReducer = function (state = initialState, action) {
  switch (action.type) {
    case "todos/addTodo":
      return {
        ...state,
        todos: [...state.todos, action.payload],
      };

    case "filter/setFilter":
      return {
        ...state,
        filter: action.payload,
      };

    case "todos/toggleTodo":
      return {
        ...state,
        todos: state.todos.map((todo) => {
          return todo.id === action.payload.id
            ? { ...todo, completed: !todo.completed }
            : todo;
        }),
      };

    default:
      return state;
  }
};
```
