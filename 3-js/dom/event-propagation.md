[&larr; Back](./README.md)

# Event Propagation

**DOM Event Propagation** occurs in 2 phases: _capturing phase_ and _bubbling phase_.

1. **Event Targeting:** a click event occurred on a button -> the event starts at the target element where it occurred.

2. **Capturing Phase:** (irrelevant) the event travels from the root of the DOM tree down to the target element.

3. **Target Phase:** the event reaches the target element -> any event handlers attached to that element are executed.

4. **Bubbling Phase:** After the target phase, the event starts bubbling up the DOM tree from the target element back to the root. During this phase, if the target element has any parent elements with event listeners for the same event type, those event handlers are also executed in order from the closest parent to the root of the document (not through siblings).

**Note:** If the target element does not have a click event, the bubbling phase is still valid, event handlers attached to parent elements will still run (if the event type coincide).

Note: Not all event types have capturing and bubbling phases, some of them are created right on the target element.

```html
<header onclick="console.log(`header`)">
  <nav onclick="console.log(`nav`)">
    <a onclick="console.log(`link`)"> Click! </a>
  </nav>
</header>

<!-- a click event occurs on the anchor tag -->
<!-- Logs: (1) link > (2) nav > (3) header  -->
```

Event bubbling is useful for performance optimization - it allows us to use a single `addEventListener` method for handling events on multiple elements.

For each event, the event handler will receive an event object with information about the actual event that occurred.

```js
link.addEventListener("click", function (event) {
  console.log(event); // event object
});
```

- We named the event object: `event`
- `event.target` the element where the event occurred.
- `event.currentTarget` the element on which the event handler is attached.
- `event.stopPropagation()` stop event propagation (not good idea).

<br>

## Practical Example

We attach an event handler to a `div` element that contains link elements. When the user clicks on a link, all the logic is handled in the same event handler.

```js
// smooth scrolling to sections according to ids
div.addEventListener("click", function (e) {
  e.preventDefault();

  if (e.target.classList.contains("nav-links")) {
    const ids = e.target.getAttribute("href");
    document.querySelector(ids).scrollIntoView({ behavior: "smooth" });
  }
});
```

<br>
