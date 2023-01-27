[&larr; Back](./README.md)

# DOM: Select, Create, Delete

## Table of Content

- [The document object](#the-document-object)
- [Selecting DOM elements](#selecting-dom-elements)
  - [Selecting the entire HTML document](#selecting-the-entire-html-document)
  - [Selecting the `head` and `body` elements](#selecting-the-head-and-body-elements)
  - [querySelector method](#queryselector-method)
  - [querySelectorAll method](#queryselectorall-method)
  - [getElementByID](#getelementbyid)
  - [getElementsByTagName and getElementsByClassName](#getelementsbytagname-and-getelementsbyclassname)
  - [Selecting and updating the text content of an element](#selecting-and-updating-the-text-content-of-an-element)
  - [Selecting and updating the value of an input element](#selecting-and-updating-the-value-of-an-input-element)
- [Creating and Inserting elements](#creating-and-inserting-elements)

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
document.querySelectorAll("div"); // .forEach();
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
