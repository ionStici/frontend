# **Selectors**

A selector is used to target specific HTML elements to be styled by the declaration.

<br>

## **Table of Content**

- [1. Universal Selector](#1-universal-selector)
- [2. Type Selector](#2-type-selector)
- [3. Class Selector](#3-class-selector)
- [4. ID Selector](#4-id-selector)
- [5. Selector list](#5-selector-list)
- [6. Attribute Selector](#6-attribute-selector)
- [7. Specificity](#7-specificity)

<br>

## **1. Universal Selector**

```
* { }
```

The universal selector `*` selects all elements of any type. Useful use cases:

- resetting default browser styling;
- selecting all children of a parent element `div * {}` or `div > * {}`

Besides this, avoid using the universal selector as it adds too much weight to the webpage.

<br>

## **2. Type Selector**

Element / Tag / Type

```
p { }
```

Selects all elements that have the given tag element.

<br>

## **3. Class Selector**

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

In the code example below, we chain 2 classes:

```
.btn.big { }
```

This translates to: the `.big` class is applied only when the `.btn` class is already applied.

<br>

## **4. ID Selector**

```
#id { }
```

Selects an element based on the value of its ID attribute.

There should be only one ID value in a document. We use IDs to uniquely select elements in CSS.

<br>

## **5. Selector list**

```
p, .class, #id, { }
```

The comma acts as a grouping method, it selects all the matching nodes.

<br>

## **6. Attribute Selector**

```
[href] { }  /* the most basic syntax */
```

Target html elements by their attribute or attribute value.

Additional resources: [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors) / [CSS Tricks](https://css-tricks.com/almanac/selectors/a/attribute/)

<br>

## **7. Specificity**
