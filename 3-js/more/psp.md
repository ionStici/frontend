[&larr; Back](./README.md)

## Event Handlers in MVC

Listen and handle events in MVC architecture - **Publisher-Subscriber Pattern**.

Everything related to the DOM (e.g. UI events) should be inside of a view.

We want to handle events in the controller, because otherwise, we would have app logic in the view. On the other hand, we want to listen for events in the view, because otherwise we would need DOM elements in the controller, which leads to having presentation logic in the controller.

Event listeners should be attached to DOM elements in the view, but the events should then be handled by the controller function that live in the controller module.

In MVC, the view doesn't know anything about the controller, we can't call controller related functions from view, it only works other way around.

**Solution - Publisher-Subscriber Design Pattern.**

Design patterns in programming are standard solutions to certain kinds of problems.

<br>

### Publisher-Subscriber Pattern

**The Publisher** - "view" code that knows when to react, as a result of an event.

**The Subscriber** - "control" code that wants to react. Code that should be executed when the event happens, which is a control function from the controller, that handles app logic.

We subscribe the control function that handles application logic - to the publisher function from the view that listens to events.

At this point, the 2 functions are connected. As soon as the event happens, the control function in the controller module will be called as the callback of `addEventListener` in the view.

This logic allows us to keep the control function in the controller, and the listener in the view, keeping everything separated. In summary, the control function subscribes to the publisher, which is the listener in this case, and then as the publisher publishes an event, the subscriber is executed.

```js
// Scenario 1
let A = () => "Hi";
let B = () => A();
B();
```

```js
// Scenario 2
let A = () => "Hi";
let B = (X) => X();
B(A);
```

Notice the profound difference between these 2 scenarios.

1. When `B()` is calling `A()` directly, `B()` is in control.

2. In the second scenario, `B()` has no direct control, it has to execute whatever function it receives.

It is all about control.

<br>

### Code Example

```js
// searchView.js Module

export default class SearchView {
  // ...
  addHandlerRender(handler) {
    // PUBLISHER
    btn.addEventListener("click", handler);
  }
  // ...
}
```

```js
// controller.js Module
import SearchView from "searchView";

const controlSearches = function () {
  // app logic
};

const init = function () {
  // SUBSCRIBER
  SearchView.addHandlerRender(controlSearches);
};

init();
```

- As soon as the program starts the `init()` function executes.
- `init()` will call `addHandlerRender` from `SearchView` module.
- Now, `addHandlerRender` from `SearchView` will listen for events right in the view.
- As soon as the event from `addHandlerRender` happens, the controller function `controlSearches` will be called dealing with the application logic.
- `controlSearches` is accessed from the view, because we passed it to `addHandlerRender`, which in turn it is used as an event handler.

<br>
