[&larr; Back](./README.md)

# Strategies for Complex State

## Table of Content

- [Slices](#slices)
- [Actions and Payloads](#actions-and-payloads)
- [Reducer: Immutable Updates](#reducer-immutable-updates)

<br>

## Slices

In a Redux application, the top-level `state` properties are known as **slices**.

**Slices** - top-level `state`.

Each _slice_ represents a different feature of the entire app.

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

<br>

## Immutable Updates & Complex State

The `store`‘s reducer function is called each time an action is dispatched. It is passed the `action` and the current `state` as arguments and returns the `store`‘s next state.

Rule: when the reducer is updating the `state`, it must make a copy and return the copy rather than directly mutating the incoming `state`.

```js
const initialState = {
  filter: "SHOW_INCOMPLETE",
  todos: [
    { id: 0, text: "learn redux", completed: false },
    { id: 1, text: "build a redux app", completed: true },
    { id: 2, text: "do a dance", completed: false },
  ],
};

const todosReducer = (state = initialState, action) => {
  switch (action.type) {
    case "filter/setFilter":
      return {
        ...state,
        filter: action.payload,
      };

    case "todos/addTodo":
      return {
        ...state,
        todos: [...state.todos, action.payload],
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

- When a 'filter/setFilter' action is received, it spreads the old state‘s contents (...state) into a new object before updating the filter property with the new filter from action.payload.

- When a 'todos/addTodo' action is received, it does the same except this time, since state.todos is a mutable array, its contents are also spread into a new array, with the new todo from action.payload added to the end.

- When a 'todos/toggleTodo action is received, it uses the .map() method to create a copy of the state.todos array. Additionally, the todo being toggled is found using action.payload.id and it is spread into a new object and updated.

<br>

## Reducer Composition

**Reducer Composition Pattern** - individual slice reducers are responsible for updating only one slice of the app's state, and their results are recombined by a rootReducer to form a single state object.

```js
const initialTodos = [];
const todosReducer = (todos = initialTodos, action) => {};

const initialFilter = "";
const filterReducer = (filter = initialFilter, action) => {};

const rootReducer = (state = {}, action) => {
  const nextState = {
    todos: todosReducer(state.todos, action),
    filter: filterReducer(state.filter, action),
  };
  return nextState;
};

const store = createStore(rootReducer);
```

In the reducer composition pattern, when an `action` is dispatched to the `store`:

- The `rootReducer` calls each slice reducer, regardless of the `action.type`, with the incoming `action` and the appropriate slice of the state as arguments.
- The slice reducers each determine if they need to update their slice of state, or simply return their slice of state unchanged.
- The `rootReducer` reassembles the updated slice values in a new state object.

The initialState object has been replaced by individual initialSliceName variables which are used as default values for each slice reducer’s slice of state. This is another common feature of the reducer composition pattern.

All slice reducers are called within the rootReducer to update their respective slices of state.

<br>

## combineReducers

Redux utility function: `combineReducers()`.

```js
import { createStore, combineReducers } from "redux";

const reducers = {
  todos: todosReducer,
  filter: filterReducer,
};

const rootReducer = combineReducers(reducers);
const store = createStore(rootReducer);
```

- `combineReducers()` function accepts an object of reducers and returns a `rootReducer` function.
- The returned `rootReducer` is passed to `createStore()` to create a `store` object with it.

When an action is dispatched to the `store`, the `rootReducer` is executed which then calls each slice reducer, passing along the action and the appropriate slice of state.

```js
const store = createStore(
  combineReducers({
    todos: todosReducer,
    filter: filterReducer,
  })
);
```

<br>

## A File Structure for Redux

Break up the Redux app using the [Redux Ducks Pattern](https://github.com/erikras/ducks-modular-redux).

```
src/
|-- index.js
|-- app/
    |-- store.js
|-- features/
    |-- featureA/
        |-- featureASlice.js
    |-- featureB/
        |-- featureBSlice.js
```

`index.js` is the entry point to the entire app.

`app/store.js` purpose is to create the `rootReducer` and the Redux `store`.

The `features/` directory and its sub-directories, contain the code relating to each individual slice of the `store`'s state.

<br>

## Passing Store Data Through the Top-Level React Component

```
src/
|-- index.js
|-- app/
    |-- App.js (+)
    |-- store.js
|-- components/
    |-- FavoriteButton.js (+)
    |-- Recipe.js (+)
|-- features/
    |-- allRecipes/
        |-- AllRecipes.js (+)
        |-- allRecipesSlice.js
    |-- favoriteRecipes/
        |-- FavoriteRecipes.js (+)
        |-- favoriteRecipesSlice.js
    |-- searchTerm/
        |-- SearchTerm.js (+)
        |-- searchTermSlice.js
```

p.s. The `<App />` top-level react component, will render each feature-component and pass any data needed by those components as prop values.

In Redux applications, we pass to component data like: state slices and dispatch methods for triggering state changes through user interactions within the component.

The distribution of `store.dispatch` methods and the slices of state to all of the feature-components, via the `<App />` component, begins in the `index.js` file.

```js
// index.js
import { App } from "./app/App.js";
import { store } from "./app/store.js";

const root = createRoot(document.getElementById("root"));
const render = () => {
  root.render(<App state={store.getState()} dispatch={store.dispatch} />);
};
render();

store.subscribe(render);
```

```js
// app.js
```

<br>

## Using Store Data Within Feature Components

Plugging in a feature-component to a Redux application involves the following steps:

- Import the React feature-components into the top-level App.js file.
- Render each feature-component and pass along the slice of state and the dispatch method as props.
- Within each feature-component:
  - Extract the slice of state and dispatch from props.
  - Render the component using data from the slice of state.
  - Import any action creators from the associated slice file.
  - Dispatch actions in response to user inputs within the component.
