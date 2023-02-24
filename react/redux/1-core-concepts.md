[&larr; Back](./../README.md)

# Introduction to Redux

## Table of Content

- [Introduction](#introduction)
- [One-Way Data Flow](#one-way-data-flow)

<br>

## Introduction

- **The state of the application:** shared data between components.
- **State management:** the process of sharing and updating the state.

**[Redux](https://redux.js.org/)** is a state management library that follows the flux architecture pattern.

In the Flux pattern and Redux, shared information is not stored in components but in a single object.

Components are just given data to render and can request changes using events called actions.

The state is available throughout the application and updates are made in a predictable manner: components are “notified” whenever a change is made to the state.

<br>

## One-Way Data Flow

In most applications, there are three parts:

- **State** - the current data used in the app.
- **View** - the user interface displayed to users.
- **Actions** - events that a user can take to change the state.

The flow of information would go like this:

- The state holds the current data used by the app's components.
- The view components display that state data.
- When a user interacts with the view (click event), the state will be updated.
- The view is updated to display the new state.

Redux helps separate the state, the view, and actions by requiring that the state be managed by a single source.

Requests to change the state are sent to this single source by view components in the form of an action.

Any components of the view that would be affected by these changes are informed by this single source.

<br>

## State

**State** is the current information behind a web application.

With Redux, state can be any JavaScript type.

_Example:_ For a todo app it includes the todo items, completed or not completed, the current order of the items, display filters.

<br>

## Actions

In Redux, actions are represented as plain JS objects. Example:

```js
const action = {
  type: "todos/addTodo",
  payload: "Read",
};
```

- Every action must have a `type` property with a string value which describes the action.
- Typically, an action has a `payload` property with an object value. This includes any information related to the action. In the above example, the payload is a todo text.
- When an action is generated and notifies other parts of the application, we say that the action is _dispatched_.

<br>

## Reducers

**A Reducer** is a plain JS function that defines how the _current state_ and an _action_ are used in combination to create the new state.

- _A reducer will:_

  Defines the app's next state given a current state and a specific action.

  Returns a default initial state if no action is provided.

  Returns the current state if the action is not recognized.

<br>
