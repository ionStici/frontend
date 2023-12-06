[&larr; Back](./README.md)

# DOM Events with JavaScript

## Table of Content

- [addEventListener](#addeventlistener)
  - [Named function as Event Handler](#named-function-as-event-handler)
- [on-event properties](#on-event-properties)
- [Removing Event Handlers](#removing-event-handlers)
- [The Event Object](#the-event-object)
- [Event Types](#event-types)
  - [Mouse Events](#mouse-events)
  - [Keyboard Events](#keyboard-events)
- [Handling a Keypress Event](#handling-a-keypress-event)
- [Passing Arguments to Events Handlers](#passing-arguments-to-events-handlers)
- [Lifecycle DOM events](#lifecycle-dom-events)

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

### on-event HTML attributes

We can use `on-event` directly in HTML as attributes.

```html
<button onclick="alert('wrong')">Click</button>
```

This is kind of old school JS from the early days and should not be used.

<br>

## Removing Event Handlers

The `.removeEventListener()` method is used to reverse (remove) the `.addEventListener()` method.

We can't remove an event handler declared as an anonymous function.

So, we need to use a named function as the event handler.

`.removeEventListener()` takes 2 arguments:

1. Arg 1: The event type as a string
2. Arg 2: The event handler function

```js
btn.removeEventListener("click", sayHello);
```

`.removeEventListener()` needs the exact event type name and the name of the event handler that we want to remove, because DOM elements can have multiple event handler functions associated with particular events.

<br>

## The Event Object

[The Event Object](https://developer.mozilla.org/en-US/docs/Web/API/Event)

```js
const sayHello = function (event) {
  console.log(event, event.target, event.type, event.timeStamp);
};

btn.addEventListener("click", sayHello); // Event Object
```

When an event happened, the event object is generated and is passed as an argument to the event handler function.

We get access to the event object through the parameter we specify.

This object will contains related data and functionality about the event as properties and methods.

We can use pre-determined properties associated with the event to see information about the event:

- `event.target` - reference te element that the event is registered to.
- `event.type` - to access the name of the event.
- `event.timeStamp` - the number of milliseconds that passed since the document loaded and the event was triggered.

<br>

## Event Types

[MDN Events Reference](https://developer.mozilla.org/en-US/docs/Web/Events)

Usually, the most important events are the ones related to mouse and keyboard.

Other events: Clipboard, full screen, page resizing , page scroll, etc.

<br>

### Mouse Events

- `click` press and release the mouse button
- `mousedown` press the mouse button down
- `mouseup` release the mouse button
- `mouseover` the mouse enters an element
- `mouseout` the mouse leaves an element
- `wheel` the mouse wheel is rotated

<div></div>

- `mouseenter` the mouse enters an element
- `mouseleave` the mouse leaves an element

`mouseenter` and `mouseleave` do not react to event bubbling, while `mouseover` and `mouseout` do.

<br>

### Keyboard Events

Keyboard Events are triggered by the user interaction with keyboard keys.

- `keypress` event is fired when the user presses a key down and releases it.
- `keydown` event is fired when the user presses a key down.
- `keyup` event is fired when the user releases a key.

Keyboard events have unique properties assigned to their event object.

- `event.key` - they key property stores the values of the key pressed by the user.
- By using the `key` property, we can program the event handler to react to a specific key.

<br>

## Handling a Keypress Event

Keyboard events are called **global events**, because they do not happen on one specific element.

We listen for events everywhere, no matter where they happen on the page, they will always trigger the event handler.

For global events like keyboards event we listen on the whole `document` using `addEventListener()` method.

```js
document.addEventListener("keypress", function (event) {
  if (e.key === "Escape") console.log("esc was pressed");
});
```

The `keypress` event will fire when we press any key on the keyboard.

The information about which key was pressed will be stored in the `key` property of the event object.

Then inside the event handler we can create some logic using the event object and check for the keys we need.

<br>

## Passing Arguments to Events Handlers

We can't pass argument to event handlers like usual because by using parentheses that will result in a function call. The `addEventListener()` method expects as second argument a callback function, and not a value resulted from a function call.

### Old solution

```js
btn.addEventListener("click", function () {
  callback(5, 10);
});
```

### Using the bind() method

```js
btn.addEventListener("click", callback.bind(5));
```

_Reminder:_ `bind()` creates a copy of the function that it's called on, and it will set the `this` keyword in this function call to whatever value that we pass into bind.

This will work because `bind()` returns a new function without calling it.

But.. this is not really an argument, because inside the function body we have to operate with the `this` keyword instead of a real argument.

Besides this, we can pass only one value to `bind`, the one which will become the `this` keyword. If we want to pass additional values into the handler function, we can pass into bind an array with elements.

<br>

## Lifecycle DOM events

Events that occur in the DOM during lifecycle of a webpage - from the moment the page is accessed until the user closes it.

The lifecycle of an HTML page has three important events:

- `DOMContentLoaded`
- `load`
- `beforeunload` / `unload`

### DOMContentLoaded event

```js
document.addEventListener("DOMContentLoaded", callback);
```

`DOMContentLoaded` event is fired by the `document` when:

- The browser completely parsed and fully loaded the HTML and the DOM tree is built.
- Also, all scripts must be downloaded and executed first.
- This event does not wait for images and other external resources like stylesheets to load, so just HTML and JS need to be loaded.

In devTools at Network tab, we can check the time it takes for the event to fire.

With this event, we can execute code that should only be executed after the DOM is available.

### load event

```js
window.addEventListener("load", callback);
```

The `load` event is fired by the `window` object, not only when the HTML is parsed, but also when all the external resources (like images, CSS, etc.) are loaded, so when the complete page has finished loading.

### beforeunload / unload events

```js
window.addEventListener("beforeunload", function (e) {
  e.preventDefault();
  console.log(e);
  e.returnValue = "";
});

window.addEventListener("unload", callback);
```

The `beforeunload` and `unload` events are fired when the user is leaving the page (clicking the close button).

- `unload` event - the user almost left, but we still can initiate some operations, such as sending out statistics.

- `beforeunload` to check if the user has saved their changes and ask them if they really want to leave (shows a browser popup).

  Use cases: when the user is leaving in the middle of filling out a form, or writing a blog post, in situations where data could be lost by accident. Don't abuse this feature.

  Note: in some browsers for this work, we need to call `event.preventDefault()`.

  In order for the popup to be displayed, we need to set the `event.returnValue` value to an empty string (historical reasons).

  The popup is shown with a generic message, we can't customize the message. We used to be able to customize, but the feature was removed because developers started abusing it.

<br>
