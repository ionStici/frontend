[&larr; Back](./README.md)

# Event Propagation

<details>
<summary>Theory</summary>

<br>

When the DOM generates a click event, the event is generated from the root of the DOM tree. From there, the **capturing phase** begins, where the event travels all the way down from the document root to the target element where the event happened. As the event travels down the tree, it will pass through every single parent element of the target element. When the event reaches the target, the target phase begins, where events can be handled right at the target (usually with `addEventListener`)

<div></div>

After reaching the target, the event then travels all the way up to the document root again in the **bubbling phase**. Just like in the capturing phase, the event passes through all its parent elements only (no through any siblings).

<div></div>

In the bubbling phase, the event acts like it also happened in each of the parent elements of the target element.

<div></div>

Not all types of events do have a capturing and bubbling phase, some of them are created right on the target element.

<div></div>

By default, events can only be handled in the target and in the bubbling phase. However, we can set up event listeners in a way that they listen to events in the capturing phase instead.

</details>

<br>
