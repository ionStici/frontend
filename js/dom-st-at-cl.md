# DOM: Styles, Attributes, Classes

## Table of Content

- [The style property in JavaScript](#the-style-property-in-javascript)
  - [getComputedStyle() method](#getcomputedstyle-method)
  - [CSS Custom Properties (CSS variables)](#css-custom-properties-css-variables)
  - [cssText property](#csstext-property)

<div></div>

- [DOM elements and Attributes](#dom-elements-and-attributes)

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
