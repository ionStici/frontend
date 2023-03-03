[&larr; Back](./../README.md)

# Core Redux API

## Table of Content

- [State Management Introduction](#state-management-introduction)
- [Overview](#overview)
- [createStore](#createstore)
- [Dispatch Actions to the Store](#dispatch-actions-to-the-store)
- [getState](#getstate)
- [Action Creators](#action-creators)
- [Respond to State Changes](#respond-to-state-changes)
- [Connect the Redux Store to a UI (Steps)](#connect-the-redux-store-to-a-ui-steps)
- [React and Redux](#react-and-redux)
- [Redux without React](#redux-without-react)

<br>

## State Management Introduction

**The State of an Application** - the data about the app.

**State Management** - the process of sharing and updating the state.

**[Redux](https://redux.js.org/)** is a library for managing and updating application state based on the Flux architecture.

- **State** is the set of data values that describes the application. It is used to render the UI.

- **View** is the user interface displayed to users. Users interact with the UI which dispatch actions to the store.

- **Actions** are objects describing an event that a user can take to change the state in the application.

- In a Redux application, _data flows in one direction_: from **state** to **view** to **action**, back to state and so on.

- A **Reducer** is a function that determines how the current state and an action are used in combination to create the application’s next state. [**Rules of Reducer Functions**](https://redux.js.org/tutorials/fundamentals/part-3-state-actions-reducers#rules-of-reducers).

- **Store** is a special object in Redux, it is like a container for state. It provides a way to dispatch actions. It calls the reducer when actions are dispatched. Only one _store_ per app.

- **Data flow**

  1. The store initializes the state with a default value.

  2. The view displays that state.

  3. When a user interacts with the view, like clicking a button, an action is dispatched to the store.

  4. The dispatched action and the current state are combined in the store’s reducer to determine the next state.

  5. The view is updated to display the new state.

<br>

## Overview

- Redux applications are built upon a one-way flow of data model that are managed by the **store**.

- The Redux `store` is an object that holds and manages the entire state of an application.

- The **state** is the set of data values that are used to render the user interface.

- Users interact with the UI which dispatch actions to the store. An **action** is an object that expresses a desired change to the state.

- The store generates its next state using a **reducer** function which receives the most recent action and the current state as inputs.

- Finally, the UI is re-rendered based on the new state of the store and the entire process can begin again.

<br>

## createStore

```js
// npm install redux
import { createStore } from "redux";

const initialState = true;
const reducer = (state = initialState) => state;

const store = createStore(reducer);
```

The **`store`** object holds the current state, receives action dispatches, executes the reducer to get the next state, provides access to the current state for the UI to re-render.

We create the `store` object using the `createStore` helper function which receives the reducer function as its only argument.

After creating the `store` object, it provides useful methods for interacting with its state.

<br>

## Dispatch Actions to the Store

State updates are triggered by dispatching actions. An action is a JS object that contains information about an action event that has occurred. The Redux store receives these action objects, then updates its state accordingly. Actions must carry the `type` property that specifies the type of action that occurred, and also optionally some data.

- `store.dispatch()` method is used to dispatch an action to the store, to update the state.
- As argument we pass in an action object which must have a `type` property describing the desired state change.

```js
const action = { type: "actionDescriptor" };
store.dispatch(action);
```

Each time `store.dispatch()` is called with an `action` object, the store's reducer function will be executed with the same `action` object. Assuming that the `action.type` is recognized by the reducer, the state will be updated and returned.

<br>

## getState

- `store.getState()` returns the current value of the store's state.
- Internally, when the store executes its reducer, it uses `store.getState()` as the state argument.

The store calls the reducer like this:

```js
toggleReducer(store.getState(), { type: "toggle" });
```

<br>

## Action Creators

- **Action Creators** are functions that create and return action objects (`type` property).
- They are responsible for sending action objects to the Redux store (to update the state).
- Action Creators are called and passed directly to the `store.dispatch()` method.

```js
const toggle = () => ({ type: "toggle" });

store.dispatch(toggle());
store.dispatch({ type: "toggle" });
```

Before the reducer of an application is even written, we should write action creators as a way of planning out which actions will be available to dispatch to the store.

<br>

## Respond to State Changes

Actions dispatched to the `store` can be listened for and responded to using the `store.subscribe()` method. This method accepts a function as argument, called a _listener_, that is executed in response to changes to the `store`‘s state.

```js
const reactToChange = () => console.log(store.getState());
store.subscribe(reactToChange);
```

Each time an action is dispatched to the `store`, and a change to the state occurs, the subscribed listener `reactToChange()` will be executed.

### unsubscribe

Sometimes it is useful to stop the listener from responding to changes to the `store`, so `store.subscribe()` returns an `unsubscribe` function.

```js
const unsubscribe = store.subscribe(reactToChange);
unsubscribe();
```

After `unsubscribe()` is called, it causes `reactToChange()` to no longer be executed in response to further dispatches made to store.

<br>

## Connect the Redux Store to a UI (Steps)

- Create a Redux store
- Render the initial state of the application.
- Subscribe to updates. Inside the subscription callback:
  - Get the current store state
  - Select the data needed by this piece of UI
  - Update the UI with the data
- Respond to UI events by dispatching Redux actions

<br>

## React and Redux

Common steps involved in connecting Redux to a React UI:

- A `render()` function will be subscribed to the `store` to re-render the top-level React Component.
- The top-level React component will receive the current value of `store.getState()` as a `prop` and use that data to render the UI.
- Event listeners attached to React components will dispatch actions to the `store`.

```js
import React from "react";
import ReactDOM from "react-dom";
import { createStore } from "redux";

const increment = () => ({ type: "increment" });
const decrement = () => ({ type: "decrement" });

const initialState = 0;

const counterReducer = (state = initialState, action) => {
  switch (action.type) {
    case "increment":
      return state + 1;

    case "decrement":
      return state - 1;

    default:
      return state;
  }
};

const store = createStore(counterReducer);

// // // // //
const App = function (props) {
  const state = props.state;

  const handleIncrement = () => store.dispatch(increment());
  const handleDecrement = () => store.dispatch(decrement());

  store.subscribe(renderListener);

  return (
    <div>
      <p>{state}</p>
      <button onClick={handleIncrement}>+</button>
      <button onClick={handleDecrement}>-</button>
    </div>
  );
};

// // // // //
const root = ReactDOM.createRoot(document.getElementById("root"));

const renderListener = () => {
  root.render(<App state={store.getState()} />);
};

renderListener();
```

<br>

## Redux without React

```js
import { createStore } from "redux";

// Action Creators
const increment = () => ({ type: "increment" });
const decrement = () => ({ type: "decrement" });

// Initial State / Reducer / Store
const initialState = 0;
const counterReducer = function (state = initialState, action) {
  switch (action.type) {
    case "increment":
      return state + 1;
    case "decrement":
      return state - 1;
    default:
      return state;
  }
};

const store = createStore(counterReducer);

// HTML elements
const counterElement = document.getElementById("counter");
const incrementer = document.getElementById("incrementer");
const decrementer = document.getElementById("decrementer");

// Subscribe Listener
const render = () => {
  counterElement.innerHTML = store.getState();
};
render();
store.subscribe(render);

// DOM Event Handlers
const incrementerClicked = () => store.dispatch(increment());
incrementer.addEventListener("click", incrementerClicked);

const decrementerClicked = () => store.dispatch(decrement());
decrementer.addEventListener("click", decrementerClicked);
```

<br>
