[&larr; Back](./README.md)

# DOM Updating Algorithm

Create `update()` function on the parent class (available on all the views) - it will update only text and attributes in the DOM, without having to re-render the entire view.

- The `update()` function will be called by the controller.
- The `update()` function is meant to be used by each view separately, it is not standalone.

<br>

Generate `newMarkup` (but not render it). We will use the new markup to compare it with the current markup to identify and update only the text and attributes that have been changed.

To compare the markup -> convert the markup string to DOM object living in the memory, then compare it with the actual DOM that's on the page.

```js
const newMarkup = this._generateMarkup();
const newDOM = document.createRange().createContextualFragment(newMarkup);

const newElements = Array.from(newDOM.querySelectorAll("*"));
const curElements = Array.from(this._parentElement.querySelectorAll("*"));
```

The above method will convert the markup string into real DOM node objects.

`newDOM` will be the **virtual DOM** living in the app's memory. Then, we select all the elements from the virtual DOM. And, because we need to compare the virtual DOM with the current DOM on the page, we select the current DOM elements as well.

Next, we will loop over the elements from the Virtual DOM to compare them and identify which needs to update.

```js
newElements.forEach((newEl, i) => {
  const curEl = curElements[i];

  if (!newEl.isEqualNote(curEl) && newEl.firstChild?.nodeValue.trim() !== "") {
    // Update Text
    curEl.textContent = newEl.textContent;
  }

  if (!newEl.isEqualNode(curEl)) {
    // Update Attribute
    Array.from(newEl.attributes).forEach((attr) =>
      curEl.setAttribute(attr.name, attr.value)
    );
  }
});
```

In our context, the value of `nodeValue` will return `null` if it is not a text node.

Note that we select the child using `firstChild`, because the child node is what contains the text, we don't need the actual element. Then, we check if it is not an empty string. Add optional chaining because the `firstChild` might not always exist.

Then we also replace the attributes that have changed. `element.attributes` will return an object with all the attributes of an element.

This will update the DOM only in places where it has changed.

## The update() function

[Forkify View Code Example](https://github.com/jonasschmedtmann/complete-javascript-course/blob/master/18-forkify/final/src/js/views/View.js)

```js
update(data) {
    this._data = data;

    const newMarkup = this._generateMarkup();
    const newDOM = document.createRange().createContextualFragment(newMarkup);

    const newElements = Array.from(newDOM.querySelectorAll('*'));
    const curElements = Array.from(this._parentElement.querySelectorAll('*'));

    newElements.forEach((newEl, i) => {
      const curEl = curElements[i];

      // Update TEXT
      if (!newEl.isEqualNode(curEl) && newEl.firstChild?.nodeValue.trim() !== '') {
        curEl.textContent = newEl.textContent;
      }

      // Update ATTRIBUES
      if (!newEl.isEqualNode(curEl)) {
        Array.from(newEl.attributes).forEach(attr => {
            curEl.setAttribute(attr.name, attr.value)
        });
      }
    });
  }
```

<br>
