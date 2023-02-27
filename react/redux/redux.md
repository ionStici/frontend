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
