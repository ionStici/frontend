[&larr; Back](./README.md)

# Positioning

## Table of Content

- [Flow of HTML](#flow-of-html)
- [Positioning in CSS](#positioning-in-css)
- [Position](#position)
  - [static](#static)
  - [relative](#relative)
  - [absolute](#absolute)
  - [fixed](#fixed)
  - [sticky](#sticky)
- [Stacking Contexts and z-index](#stacking-contexts-and-z-index)

<br>

## Flow of HTML

A browser will render the elements of an HTML document that has no CSS from left to right, top to bottom, in the same order as they exist in the document. This is called the _flow of elements in HTML_.

CSS provides properties that change how a browser _positions_ elements.

| `position` | `display` | `z-index` | `float` | `clear` |
| ---------- | --------- | --------- | ------- | ------- |

<br>

## Positioning in CSS

Three positioning chemes:

1. **Normal Flow** - _by defaut_ and `position: relative` - elements are laid out on the page in a natural order, no changes are made to their layout.

2. **Floats** - the `float` property causes an element to be completely taken out of the normal flow and shifted to the left or right as far as possible, until it touches the edge of its containing box, or another floated element. When this happens, text and inline elements will wrap around the floated element. Also, when an element is floated, its container will not adjust his height to the element, which sometimes can be problematic - the usual solutions for this is the use of "clear fix".

3. **Absolute Positioning** - `position: absolute` or `fixed` - the element is taken out of the normal flow, it has no impact on surrounding content or elements at all, it can overlap them.

<br>

## Position

`position` property can change the default position behaviour of elements.

<br>

### static

`static` (default value) normal flow.

<br>

### relative

Normal flow. With coordination properties we can move the element relative to itself.

Offset (coordinates) properties: `top` `right` `bottom` `left`

The offset does not affect the position of any other elements. It is as if the old position was kept and everything else just flow around it as it was never moved.

This will create new stacking context when the value of `z-index` is not `auto`.

```css
div {
  position: relative;
  top: 10px;
  left: -25px;
}
```

<br>

### absolute

The element is removed from the normal flow of the document, no space is created for the element in the page layout.

It is positioned relative to the closest parent which has the position set to relative, if any; otherwise, it is placed relative to the initial containing block.

Its final position is determined by the values of `top` `right` `bottom` `left`.

Creates stacking context (when `z-indez` ≠ `auto`).

```css
div {
  position: absolute;
  right: 15px;
  bottom: -50px;
}
```

Position in relation to the nearest non-static element.

<br>

### fixed

The element is removed from the normal document flow, no space is created for the element in the page layout.

It is positioned relative to the initial containing block established by the viewport (with some exceptions, check documentation).

Its final position is determined by the values of `top` `right` `bottom` `left`.

This value always creates a new stacking context.

In printed documents, the element is placed in the same position on every page.

```css
div {
  position: fixed;
  top: 0;
  left: 50px;
}
```

<br>

### sticky

The element is positioned according to the normal flow of the document, and then offset relative to its nearest scrolling ancestor and containing block (nearest block-level ancestor).

Offset based on the values of `top` `right` `bottom` `left`.

The offset does not affect the position of any other elements.

This value always creates a new stacking context.

```css
div {
  position: sticky;
  top: 0;
}
```

<br>

## Stacking Contexts and z-index

Stacking Contexts are like layers that form a stack.

The **Stacking Contexts** is a three-dimensional conceptualization of HTML elements along an imaginary z-axis relative to the user, who is assumed to be facing the viewport or the webpage.

Stacking Context can be created by different CSS properties, not only from `position` and `z-index`.

MDN documentation about stacking context [here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)

_Point of View:_ Multiple boxes of different positions overlap with each other..

`z-index` property controls how far back or how far forward an element should appear on the web page when elements overlap.

```css
.div-1 {
  z-index: -5;
}

.div-2 {
  z-index: 1;
}
```

`z-index` accepts integer values. Depending on their values, the integers instruct the browser on the order in which elements should be layered on the web page.

`z-index` does not work with static `elements`. Use `relative` instead to create stacking context with `z-index`.
