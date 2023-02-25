[&larr; Back](./../README.md)

# Introduction to Redux

**The State of an Application** - all data that exists in memory when the app is running.

**State Management** - the process of sharing and updating this state.

**[Redux](https://redux.js.org/)** is a library for managing and updating application state based on the Flux architecture.

- In a Redux application, _data flows in one direction_: from **state** to **view** to **action**, back to state and so on.

- **State** is the current information (data) used in a web application.

- **View** - the user interface displayed to users.

- **Actions** are objects describing an event that a user can take to change the state in the application. They help components communicate and share data with each other.

- A **Reducer** is a function that determines how the current state and an action are used in combination to create the application’s next state. A reducer function must be a pure function and it must update the state immutably. [**Rules of Reducer Functions**](https://redux.js.org/tutorials/fundamentals/part-3-state-actions-reducers#rules-of-reducers).

- **Store** - Redux uses a special object called the _store_. The _store_ is a container for state, it provides a way to dispatch actions, and it calls the reducer when actions are dispatched (only one _store_ object per app).

- **Data flow**

  1. The store initializes the state with a default value.

  2. The view displays that state.

  3. When a user interacts with the view, like clicking a button, an action is dispatched to the store.

  4. The dispatched action and the current state are combined in the store’s reducer to determine the next state.

  5. The view is updated to display the new state.

<br>
