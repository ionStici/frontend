[&larr; Back](./README.md)

# DOM: Styles, Attributes, Classes

## Table of Contents

- [The style property in JavaScript](#the-style-property-in-javascript)
  - [getComputedStyle() method](#getcomputedstyle-method)
  - [CSS Custom Properties (CSS variables)](#css-custom-properties-css-variables)
  - [cssText property](#csstext-property)

<div></div>

- [DOM elements and Attributes](#dom-elements-and-attributes)
  - [getAttribute() method](#getattribute-method)
  - [setAttribute() method](#setattribute-method)
  - [data attributes](#data-attributes)

<div></div>

- [Classes and DOM elements](#classes-and-dom-elements)
  - [Adding a class](#adding-a-class)
  - [Removing a class](#removing-a-class)
  - [Check if an element has a certain class](#check-if-an-element-has-a-certain-class)
  - [Replace a class](#replace-a-class)
  - [toggle a class](#toggle-a-class)

<div></div>

<br>

## The style property in JavaScript

DOM manipulation - Set or change styles.

The `.style` property of a DOM element provides access to the inline style on that HTML tag.

The syntax format: `element.style.cssProperty = "value";`

In JavaScript, all the css properties that have two or more words are using the camel case notation.

Example: CSS `background-color` / JS `backgroundColor`.

After we chained the CSS property, we set it equal to a CSS value in quotes.

```js
el.style.width = "150px";
el.style.width; // 150px
el.style.height; // nothing
```

Note: These are inline styles, we are not changing the CSS file.

Additionally, we can read inline styles of a DOM element like this.

However, by using this technique we can't read embedded or external CSS styles.

### getComputedStyle() method

The `getComputedStyle()` method will return an object with all the styles and values of a DOM element.

```js
getComputedStyle(el).width; // 150px
getComputedStyle(el).height; // 43.6667px
```

Then, for a particular style value, we just chain it, and we get a string with its style value.

This method returns the computed values of a DOM element (as they appear on the page).

This works even for properties we didn't specify, because the browser had to calculate them in order to render the element on the page.

**`getComputedStyle` in practice:**

```js
el.style.height = `${
  Number.parseFloat(getComputedStyle(el).height, 10) + 50
}px`;
```

Increase the height by 50px.

### CSS Custom Properties (CSS variables)

We can update the CSS custom properties from JavaScript.

We define them in the document root `document.documentElement`.

```js
const root = document.documentElement;
root.style.setProperty("--color", "red");
```

On the `style` property of the document root, we chain the `setProperty()` method which the following arguments:

- Arg 1: the name of the CSS variable.
- Arg 2: the css value.

### cssText property

```js
el.style.cssText = `
    color: red;
    width: 150px;
`;
```

The `cssText` property will set multiple inline CSS declarations.

Note: `cssText` will override the previous inline styles (only the inline styles).

<br>

## DOM elements and Attributes

We can access and edit HTML attributes of DOM elements from JavaScript.

We can read attributes from DOM elements like properties:

```html
<img class="logo" src="./img/logo.png" designer="John" />
```

```js
logo.src; // http://127.0.0.1:8080/img/logo.png | absolute URL
logo.className; // logo | className is for class attributes, because of historical reasons

logo.alt = "Logo"; // setting an attribute
logo.alt; // Logo

logo.designer; // undefined
```

By setting the attribute property equal to a value, we define an attribute from the DOM.

For standard attributes (attributes which are expected to be in elements), JavaScript will create for them properties on the element object. But if we add an attribute that is not a standard, we will not find it in the element object.

### getAttribute() method

The `getAttribute()` method returns the value of a specified attribute on the element.

```js
logo.getAttribute("src"); // img/logo.png | relative URL
logo.getAttribute("designer"); // John
```

- We can read values of non-standard attributes with `getAttribute`
- `getAttribute` will return the relative path of assets (images, href).

### setAttribute() method

The `setAttribute()` method sets the value of an attribute of the specified element.

If the attribute already exists, the value is updated.

Otherwise a new attribute is added with the specified name and value.

Also, it works for non-standard attributes.

```js
logo.setAttribute("alt", "The company logo");
```

### data attributes

[About the data attribute MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*)

The `data-*` attribute allow proprietary information to be exchanged between HTML and its DOM representation by scripts.

It starts with the keyword `data-` plus a hyphen and then out own text.

```html
<p data-about="it says hello" data-meta-info="5">Hello World</p>
```

```js
p.dataset.about; // it says hello
p.dataset.metaInfo; // 5
```

- In JavaScript, `dataset` is an object on a DOM element with all the `data-*` attributes specified.
- To read its value, pn the DOM element we chain the `dataset` property, and then a `data-*` property.
- In JS we use camelCase when reading multi-word `data-*` properties , while in html we used hyphens.
- We use `data-*` attributes to build a bridge between HTML elements and JavaScript code (building UI).

<br>

## Classes and DOM elements

Manipulating classes with JavaScript.

In practice, adding and removing classes is the main way how we update the user interface.

Example: Exporting the styles into a class and then adding and removing the class with JavaScript.

With the `classList` property we can manipulate the classes of a DOM element.

### Adding a class

```js
logo.classList.add("logo");
logo.classList.add("logo", "logo--big"); // adding multiple classes
// logo.classList = "logo"; // this will override all the existing classes
```

### Removing a class

```js
logo.classList.remove("logo--big");
```

### Check if an element has a certain class

```js
logo.classList.contains("logo"); // true or false
```

### Replace a class

```js
logo.classList.replace("logo", "header__logo");
```

If the class we want to replace doesn't exist, then `replace` will return false without adding the new class.

### toggle a class

```js
logo.classList.toggle("logo");
```

`toggle` will add the class if the element doesn't have it, or remove it if the element contains the class.

<br>
