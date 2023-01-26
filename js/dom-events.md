[&larr; Back](./README.md)

# DOM Events with JavaScript

## Table of Content

- [addEventListener](#addeventlistener)
  - [Named function as Event Handler](#named-function-as-event-handler)

<br>

## addEventListener

Using the `.addEventListener()` method, we can have a DOM element listen for a specific event and execute a block of code when the event is detected.

For example, a click on a button, first we select the button, and then on that button element we call the `.addEventListener()` method and register the click event.

- **Event Target**: the DOM element that listens for an event.
- **Event Handler**: the block of code that runs when the event happens.

```js
const btn = document.querySelector("button");

btn.addEventListener("click", function () {
  console.log("You clicked me!");
});
```

- We selected the _event target_ from the DOM.
- We used the `.addEventListener()` method on the `eventTarget` DOM element.
- The `.addEventListener()` methods takes two arguments
- Arg 1: the type name of the event in string format
- Arg 2: An event handler (a function which will execute when the click event happens)
- Here, we used the `'click'` event, which fires when the user clicks on the `eventTarget`
- The code block in the event handler function will execute when the `'click'` event is detected
- We say that this is an anonymous handler function, because it doesn't have a name.
- We don't call this handler function, we only define it, the JS engine will call it when the event happens.

[MDN Event Reference](https://developer.mozilla.org/en-US/docs/Web/Events)

<br>

### Named function as Event Handler

Instead of using an anonymous function as the event handler, it's best practice to create and use a named event handler function. Your code will remain organized and reusable this way.

```js
const sayHello = () => console.log("Hello");
btn.addEventListener("click", sayHello);
```

The named function `sayHello` is passed without parentheses as the second argument of the `.addEventListener()` method.

We don't call the function, so we are not using parentheses here. With parentheses, JS would immediately call the function as soon as it reaches the line of code.

But, we want the event handler function to be executed only when the click event happens. So we just register it, and then JS will call it when the click event happens.

<br>

## on-event properties

Another way of attaching an event listener is by using on-event properties directly on DOM elements.

This works by appending an element with `.on` followed by the lowercased event type name.

```js
// btn.onmouseenter = sayHello;
btn.onclick = sayHello;
```

Here, on a DOM element, we use the `.onclick` property and set its value to the `sayHello` event handler.

For each event that is on the reference table, there is one on-event property.

This is the old way of listening to events, now we usually always use addEventListener.

Anyway, both `.onclick` property and `.addEventListener()` method will register event listeners, but:

With the `.addEventListener()` method we can attach multiple event handler functions. But the `.on-event` property allows for only one event handler function to be attached to the event target, so the last event will override the others.

Additionally, we can remove an event handler attached with `.addEventListener()` method, which is not possible with `.on-event` properties.

<br>
