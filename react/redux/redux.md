[&larr; Back](./../README.md)

# Redux

<br>

## Introduction to Redux

**The State of an Application** - all data that exists in memory when the app is running.

**State Management** - the process of sharing and updating this state.

**[Redux](https://redux.js.org/)** is a library for managing and updating application state based on the Flux architecture.

- In a Redux application, _data flows in one direction_: from **state** to **view** to **action**, back to state and so on.

- **State** is the set of data values that describes the application. It is used to render the UI.

- **View** - the user interface displayed to users. Users interact with the UI which dispatch actions to the store.

- **Actions** are objects describing an event that a user can take to change the state in the application. They help components communicate and share data with each other.

- A **Reducer** is a function that determines how the current state and an action are used in combination to create the application’s next state. A reducer function must be a pure function and it must update the state immutably: [**Rules of Reducer Functions**](https://redux.js.org/tutorials/fundamentals/part-3-state-actions-reducers#rules-of-reducers).

- **Store** - Redux uses a special object called the _store_. The _store_ is a container for state, it provides a way to dispatch actions, and it calls the reducer when actions are dispatched (only one _store_ object per app).

- **Data flow**

  1. The store initializes the state with a default value.

  2. The view displays that state.

  3. When a user interacts with the view, like clicking a button, an action is dispatched to the store.

  4. The dispatched action and the current state are combined in the store’s reducer to determine the next state.

  5. The view is updated to display the new state.

<br>

## freeCodeCamp

The Redux `store` is an object that holds and manages the entire state of an application.

We create the Redux `store` object using the `createStore()` method. This method takes a `reducer` function as a required argument.

```js
const reducer = (state = 5) => {
  return state;
};
const store = Redux.createStore(reducer);
```

<br>

Retrieve the current `state` held in the redux `store` object using the `getState()` method:

```js
const currentState = store.getState();
```

<br>

### Redux Action

State updates are triggered by dispatching actions.

An action is a JS object that contains information about an action event that has occurred.

The Redux store receives these action objects, then updates its state accordingly.

Actions must carry a `type` property that specifies the type of action that occurred, and also optionally some data.

Redux actions - messengers that deliver information about events to the Redux store. The store then conducts the business of updating state based on the action that occurred.

```js
const action = { type: "LOGIN" };
```

### Action Creator

An Action Creator is a JS function responsible for sending the action to the Redux store so it can update its state. Action creators create and return objects that represent action events.

```js
const actionCreator = function () {
  return action;
};
```

### Dispatch an Action Event

`store.dispatch()` is a method used to dispatch actions to the redux store.

We call the `dispatch` method on the `store` object and pass in the value returned from an action creator - then it will send an action back to the store.

Recall that action creators return an object with a type property that specifies the action that has occurred. Then the method dispatches an action object to the Redux store.

```js
store.dispatch(actionCreator());
store.dispatch({ type: "LOGIN" });
```

The code example disptach the action of type `LOGIN`

### Handle an Action in the Store

After an action is created and dispatched, the `reducer` function will instruct the Redux store know how to respond to that action.

Reducers in Redux are responsible for the state modifications that take place in response to actions.

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

## Introduction

Redix applications are built upon a one-way flow of data model and are managed by the **store**:

- The **state** is the set of data value that describes the application. It is used to render the user interface.
- Users interact with the UI which dispatch actions to the store. An **action** is an object that expresses a desired change to the state.
- The store generates its next state using a **reducer** function which receives the most recent action and the current state as inputs.
- Finally, the UI is re-rendered based on the new state of the store and the entire process can begin again.

```js
npm install redux
import { createStore } from "redux";
```

<br>

## Create a Redux Store

The `store` is an object that enforces the one-way data flow model that Redux is built upon. In holds the current state inside, receives action dispatches, executes the reducer to get the enxt state, and provides accesst to the current state for the UI to re-render.

`createStore` helper function for creating the `store` object, has a single argument: a reducer function.

```js
const store = createStore(reducer);
```

<br>

## Dispatch Actions to the Store

The `store` object returned by `createStore()` provides a number of useful methods for interacting with its state as well as the reducer function it was create with.

`store.dispatch()` method is used to dispatch an action to the store, indicating that you wish to update the state. Its only argument is an action object, which must have a type property describing the desired state change.

```js
const action = { type: "actionDescriptor" };
store.dispatch(action);
```

Each time `store.dispatch()` is called with an `action` object, the store’s reducer function will be executed with the same `action` object. Assuming that the action.type is recognized by the reducer, the state will be updated and returned.

The `store.getState()` method, returns the current value of the store's state. Internally, when the store executes its reducer, it uses `store.getState()` as the state argument. The store calls the reducer like this:

```js
toggleReducer(store.getState(), { type: "toggle" });
```

<br>

## Action Creators

**Action Creators** are used to reduce the repetition and to provide consistency.

An action creator is simply a function that returns an action object with a `type` property.

They are typically called and passed directly to the `store.dispatch()` method resulting in fewer errors and an easier-to-read dispatch statement.

```js
const toggle = () => ({ type: "toggle" });
store.dispatch(toggle());
```

In this code example, `toggle` is the action creator.

Often, before the reducer of an application is even written, Redux programmers will write action creators as a way of planning out which actions will be available to dispatch to the store.

<br>

## Respond to State Changes

Actions dispatched to the `store` can be listened for and responded to using the `store.subscribe()` method. This method accepts a function as argument, called a _listener_, that is executed in response to changes to the `store`‘s state.

```js
const reactToChange = () => console.log(store.getState());
store.subscribe(reactToChange);
```

Each time an action is dispatched to the `store`, and a change to the state occurs, the subscribed listener, `reactToChange()`, will be executed.

Sometimes it is useful to stop the listener from responding to changes to the `store`, so `store.subscribe()` returns an `unsubscribe` function.

```js
const unsubscribe = store.subscribe(reactToChange);
unsubscribe();
```

After `unsubscribe()` is called, it causes `reactToChange()` to no longer be executed in response to further dispatches made to store.

<br>

## Connect the Redux Store to a UI

Connecting a Redux store with any UI - Steps:

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
// // // // //
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
const root = ReactDOM.createRoot(document.getElementById("root"));

const renderListener = () => {
  root.render(<App state={store.getState()} />);
};

renderListener();

// // // // //
const App = function (props) {
  const state = props.state;

  const handleInrement = () => store.dispatch(increment());
  const handleDecrement = () => store.dispatch(decrement());

  store.subscribe(renderListener);

  return (
    <div>
      <p>{state}</p>
      <button onClick={handleInrement}>+</button>
      <button onClick={handleDecrement}>-</button>
    </div>
  );
};
```

<br>
