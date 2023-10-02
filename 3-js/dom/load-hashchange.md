[&larr; Back](./README.md)

# load and hashchange events

```html
<a href="#hello">Click</a>
<!-- https://website.com/#hello -->
```

We can read the ID changes from the URL using JavaScript, and do changes on the page accordingly.

```js
const readID = function () {
  const id = window.location.hash.slice(1);
  if (!id) return;
  cosnole.log(id); // hello
  // change the UI based on the current link's ID
};

// window.addEventListener("hashchange", readID);
// window.addEventListener("load", readID);

["hashchange", "load"].forEach((type) => window.addEventListener(type, readID));
```

- `load` event fires when the page loads.

- `hashchange` event fires when the link's ID changes.

By using the link with the id, the changes would persist.

<br>
