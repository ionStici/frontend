[&larr; Back](./README.md)

# DOM Traversing

## Going downwards: Child selecting

```js
// child selecting:
div.querySelector(".hi");

// Select all children:
div.querySelectorAll(".hi");

// array of direct children:
div.children; // HTML live collection

// first or last child element:
div.firstElementChild; // element
div.lastElementChild; // element

div.firstChild; // node
div.lastChild; // node
```

<br>

## Going upwards: Parents

```js
// parent node
div.parentNode;

// parent element
div.parentElement;

// selects the closest parent element
div.closest(".hi"); // opposite of querySelector
```

<br>

## Going sideways: Siblings

- We can access only direct siblings, the previous and the next one.
- It will return `null` if the element doesn't have any siblings.

```js
div.previousElementSibling; // element
div.nextElementSibling; // element
div.previousSibling; // node
div.nextSibling; // node
```

_Select all the siblings using `parentElement` and `children` properties:_

```js
[...div.parentElement.children];
```

<br>
