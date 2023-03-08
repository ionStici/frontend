# React Redux Library

```
npm install react-redux
```

## The Provider Component

```js
import { App } from "./app/App.js";
import { store } from "./app/store.js";
import { Provider } from "react-redux";

root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```

The `<Provider>` component gives the components of an app access to the Redux store without the need to pass the store directly to the React components through props.

Wrap the `<Provider>` component around the top-level component and pass store through the `store` prop of the Provider.

Note that we no longer use the `render` function that we usually subscribe.

<br>

## Selectors

The Redux store is provided to the React components of the application using the `<Provider>` component. Now, for each React component, you need to define which data from the store that component needs access to. This can be done by creating selector functions. These are not provided by the `react-redux` library but instead are user-defined.

A selector function, or selector, is a pure function that selects data from the Redux store’s state. Each component in an application that needs access to the state will have one or more selectors that extract only the necessary data for that component.

As pure functions, selectors should output the same data given the same input. This means that no randomness or side effects can occur inside the function.

A selector:

- Takes `state` as an argument.
- Returns what is needed by the component from `state`.

```js
export const selectFilter = (state) => state.filter;

export const selectTodoText = (state) => state.todos.map((todo) => todo.text);

export const selectIsCompleteIDs = (state) =>
  state.todos.filter((todo) => todo.isComplete).map((todo) => todo.id);
```

It is a convention to give selectors a name that starts with `select` and that represents the specific piece of data they retrieve.

<br>

## The useSelector() Hook

- `useSelector` returns data from the Redux store using selectors
- It subscribes a child component of `<Provider />` to changes in the store. React, not Redux, will re-render the component if the data from the selector changes.

```js
// Todos.js
import { useSelector } from "react-redux";
import { selectTodos } from "todosSlice.js";

export const Todos = () => {
  const todos = useSelector(selectTodos);

  return <p>{todos}</p>;
};
```

After passing the selector function, `useSelector` will return the selected data from the Redux store.

Calling `useSelector()` inside the component also subscribes the respective component to re-render if any changes occur in the `todos` portion of the Redux store. This optimizes the performance of the application by only re-rendering components that have had their data change and not the entire application.

`useSelector` can also use an inline selector as an argument:

```js
const todos = useSelector((state) => state.todos);
```

Inline selectors can be useful if you need to use props for data retrieval.

```js
export const Todo = (props) => {
  const todo = useSelector((state) => state.todos[props.id]);
};
```

`useSelector()` completes the 3 step process for accessing data from the Redux store using `react-redux`.

1. The `<Provider>` component is used to provide the Redux store to the nested application.
2. Selectors are created to give instructions on retrieving data from the store.
3. `useSelector()` is called within a child component of `<Provider>` for executing selector instructions to retrieve data and subscribe to re-rendering.

<br>

## The useDispatch() Hook

```js
import { useSelector, useDispatch } from "react-redux";
import { selectTodo } from "./todoSlice.js";
import { removeTodo } from "./todoSlice.js";

const Todo = () => {
  const todo = useSelector(selectTodo);
  const dispatch = useDispatch();

  return <button onClick={() => dispatch(removeTodo(todo))}>{todo}</button>;
};
```

The `useDispatch` hook allows you to dispatch actions from any component that is a descendent of the `<Provider>` component, therefore avoiding passing a reference to `store.dispatch` through props. Both approaches accomplish the same thing but `useDispatch()` avoids props drilling.

<br>
