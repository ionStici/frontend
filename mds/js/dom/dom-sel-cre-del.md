[&larr; Back](./README.md)

# DOM: Select, Create, Delete

## Table of Contents

- [The document object](#the-document-object)

<div></div>

- [Selecting DOM elements](#selecting-dom-elements)
  - [Selecting the entire HTML document](#selecting-the-entire-html-document)
  - [Selecting the `head` and `body` elements](#selecting-the-head-and-body-elements)
  - [querySelector method](#queryselector-method)
  - [querySelectorAll method](#queryselectorall-method)
  - [getElementByID](#getelementbyid)
  - [getElementsByTagName and getElementsByClassName](#getelementsbytagname-and-getelementsbyclassname)
  - [Selecting and updating the text content of an element](#selecting-and-updating-the-text-content-of-an-element)
  - [Selecting and updating the value of an input element](#selecting-and-updating-the-value-of-an-input-element)

<div></div>

- [Creating and Inserting elements](#creating-and-inserting-elements)
  - [createElement and appendChild methods](#createelement-and-appendchild-methods)
  - [insertAdjacentHTML method](#insertadjacenthtml-method)
  - [innerHTML property](#innerhtml-property)
  - [prepend and append methods](#prepend-and-append-methods)
  - [before and after methods](#before-and-after-methods)

<div></div>

- [Deleting an element](#deleting-an-element)
  - [remove() method](#remove-method)
  - [removeChild() method](#removechild-method)
  - [hidden property](#hidden-property)

<br>
 
## The document object

The `document` object in JavaScript is the door to the DOM structure. It allows you to access the root node of the DOM tree.

The `document` object allows scripts to access children of the DOM as properties. `document.body` here we access the `<body>` element, by using the `body` property of the `document` object.

[A comprehensive list of all document properties](https://developer.mozilla.org/en-US/docs/Web/API/Document)

<br>

## Selecting DOM elements

### Selecting the entire HTML document

```js
document.documentElement;
```

### Selecting the `head` and `body` elements

```js
document.head;
document.body;
```

### querySelector method

```js
document.querySelector("div"); // by tab
document.querySelector(".class"); // by class
document.querySelector("#id"); // by id
```

We call the `querySelector()` method on the `document` object.

It will return the first element that matches the selector.

### querySelectorAll method

```js
const divs = document.querySelectorAll("div"); // .forEach();
[...divs]; // convert the nodeList into an array of html elements.
```

`querySelectorAll()` method will return a nodeList (similar to an array) with all the elements that have the given selector. Even though nodeList is not an array, we can still call the `forEach` loop on a nodeList.

### getElementByID

```js
document.getElementByID("id-name");
```

It will return the first instance with the given ID.

No hash needed inside the quotes, just the id name.

### getElementsByTagName and getElementsByClassName

```js
document.getElementsByTagName("button");
document.getElementsByClassName("btn");
```

`getElementsByTagName` and `getElementsByClassName` methods returns a live HTML collection (!== nodeList).

If the DOM changes, then the HTML collection is also update automatically.

If we delete an element from a nodeList after the nodeList has been created, we still have the element in the nodeList because it doesn't update itself like the HTML collection does.

### Selecting and updating the text content of an element

```js
document.querySelector(".p").textContent; //
document.querySelector(".p").textContent = "Hello World";
```

With `.textContent` property we can select the content of an element.

By setting the `textContent` property equal to a string, we update the content of the element.

### Selecting and updating the value of an input element

```js
document.querySelector("input").value;
document.querySelector("input").value = 23;
```

For `input` elements, we use the `.value` property.

<br>

## Creating and Inserting elements

### createElement and appendChild methods

```js
const newImg = document.createElement("img");

newImg.setAttribute("src", "./img.jpg");
newImg.classList.add("big-img");
newImg.id = "unique-img";
// setAttribute can also set IDs
```

`createElement()` method returns a new DOM element based on the specified tag name passed into it as an argument. Here, we then store that new element into a variable. Then we attach the necessary attributes to the newly created `<img>`.

This new element is not yet anywhere in the DOM, we have to manually insert it into the page.

So, we append our newly created element to the DOM with `appendChild()` method:

```js
document.body.appendChild(newImg);
```

The `appendChild()` method will append the element passed in as an argument as the LAST child node of the element on which the method is called.

### insertAdjacentHTML method

```js
containerEl.insertAdjacentHTML("afterBegin", `<p>Hello World</p>`);
```

- Arg 1: A string representing the position relative to the element.
- Arg 2: A string representing the HTML code that will be inserted into the tree.

Possible positions for the inserted content

```html
<!-- beforebegin -->
<p>
  <!-- afterbegin -->

  <!-- beforeend -->
</p>
<!-- afterend -->
```

### innerHTML property

```js
div.innerHTML = "";
```

The `innerHTML` property overrides the HTML code of the element to which it is assigned.

If we set equal to empty string, it will make the element empty.

It can add any valid HTML elements (written as a string).

### prepend and append methods

```js
element.prepend(paragraph);
element.append(paragraph);
```

- `prepend` inserts its argument as the first child of the element.
- `append` inserts its argument as the last child of the element.

If we insert an element twice with prepend and append, in practice the element will be inserted only once, because the `paragraph` element is now a live element living in the DOM. Therefore, it cannot be in multiple places at the same time.

First we preprended the element, then we appended it, so append moved the element from being the first child to being the last child. It moved the element, and didn't really insert it, because it was already inserted by prepend.

What this means is that we can use the prepend and append methods not only to insert elements, but also to move them, that is because a DOM element is unique, it can always only exist at one place at a time.

If we want to insert multiple copies of the same element, we can duplicate the element with `cloneNode()`:

```js
element.append(paragraph.cloneNode(true));
```

First the paragraph is cloned, then the clone is appended.

As argument to `cloneNode()` we type `true`, which means that all the child elements will also be copied.

### before and after methods

```js
element.before(paragraph);
element.after(paragraph);
```

- `before` will insert the `paragraph` before the element.
- `after` will insert the `paragraph` after the element.

<br>

## Deleting an element

### remove() method

```js
newImg.remove();
```

The `remove()` method (new) removes the element from the DOM.

### removeChild() method

Before the `remove()` method was introduced, we had to select the parent element first and then remove the child from there:

```js
paragraph.parentElement.removeChild(message);
```

### hidden property

```js
paragraph.hidden = true;
```

The `hidden` property set to `true` will hide the element from the DOM and not delete it completely.
