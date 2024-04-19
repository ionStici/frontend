# Selectors

In CSS, a selector is used to target and style specific HTML elements.

## Table of Content

- [1. Universal Selector](#1-universal-selector)
- [2. Type Selector](#2-type-selector)
- [3. Class Selector](#3-class-selector)
- [4. ID Selector](#4-id-selector)
- [5. Attribute Selector](#5-attribute-selector)
- [6. Grouping selectors](#6-grouping-selectors)
- [7. Chaining](#7-chaining)
- [8. Descendant Combinator](#8-descendant-combinator)

## 1. Universal Selector

```
* { }
```

The universal selector `*` selects all elements of any type. Useful use cases:

- resetting default browser styling;
- selecting all children of a parent element `div * {}` or `div > * {}`

Besides this, avoid using the universal selector as it adds too much weight to the webpage.

## 2. Type Selector

Element / Tag / Type

```
p { }
```

A type selector matches a HTML element directly.

## 3. Class Selector

```
.class { }
```

Selects all elements that have the given class.

Note: HTML elements can have multiple classes

```html
<p class="text color class">text</p>
```

Then we can use all of them in CSS separately as selectors. We can't do the same with IDs.

The last class takes precedence over the previous class, so we can override declarations.

## 4. ID Selector

```
#id { }
```

Selects an element based on the value of its ID attribute.

There should be only one ID value in a document. We use IDs to uniquely select elements in CSS.

## 5. Attribute Selector

```
[href] { }  /* the most basic syntax */
```

Target html elements by their attribute or attribute value.

Additional resources: [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors) / [CSS Tricks](https://css-tricks.com/almanac/selectors/a/attribute/)

## 6. Grouping selectors

```
p, .class, #id, { }
```

The ruleset is applied to all above selectors.

The comma acts as a grouping method, it selects all the matching nodes.

## 7. Compound selectors

Chaining - combining selectors to increase specificity and readability.

```
h1.heading-1 { }
```

This translates to: target `h1` elements that have a class of `heading-1`

## 8. Descendant Combinator

```
ul li { }
```

This will select all `li` elements within an `ul` element.

Node: adding more than one tag, class or ID to a CSS selector, it will increase the specificity of that selector.
