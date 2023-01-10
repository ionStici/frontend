[&larr; Back](./README.md)

# Units in CSS

**Absolute Units** (like `px`) are used to size content to _exact dimensions_.

_Note:_ Pixels are used to ensure hard limits on the dimensions of elements.

**Relative Units** are relative to something else, like:

- The size of the parent element.
- The font size of the root or parent elements.
- The size of the viewport.

<br>

## Table of Content

- [em]()
- [rem]()
- [Percentages]()
- [Value Processing]()

<br>

## em

- The `em` unit (for length) is measured relative to the font-size of the current or parent element.
- The `em` unit (for fonts) is measured relative to the font-size of the parent element.

`X em = X em * font-size`

This means that if the font-size of the current element is 10px, then `5em` will be 50px.

In case the font-size of the current element is not specified, then `em` will be relative to the base font-size defined by the browser, which is usually `16px`.

<br>

## rem

`rem` stands for _root em_.

`rem` is measured relative to the root font-size. The root element is the `<html>` tag.

Most browsers set the font-size of the `<html>` element to 16px, so by default `rem` will be relative to that value.

But we can change the root font-size:

```css
html {
  font-size: 10px;
}

div {
  width: 15rem;
}
```

Here, the `width` of the `div` element will be `150px`, because `15rem = 15 (rem) * 10 (px)`.

Rem advantage: all elements are measured relative to the same font-size value.

- `rem` sizing elements consistently across the entire website.
- `em` sizing elements in comparison to other elements nearby.

<br>

## Percentages

- Percentages for width and height are measured relative to the dimensions of their parent element.
- Percentages for padding and margin, are measured relative only to the width of the parent element.

<br>

## Value Processing

How values (units) are processed in the CSS parsing phase.

All relative units will ultimately be converted to pixels.

1. Declared value (author declarations)
2. Cascaded value (after the cascade)
3. Specified value (defaulting, if there is no cascaded value)
4. Computed value (converting relative values to absolute)
5. Used value (final calculations, based on layout)
6. Actual value (browser and device restrictions)

_What you need to know:_

- Each property has an initial value, used if nothing is declared (and if there is no inheritance).
- Browsers specify a `root` `font-size` for each page (usually 16px).
- Percentages and relative values are always converted to pixels.

<div></div>

- Percentages for `font-size`, are measured relative to their parent's `font-size`
- Percentages for `lengths`, are measured relative to their parent's `width`

<div></div>

- `em` for `font-size`, are measured relative to their parent `font-size`
- `em` for `lengths`, are measured relative to their current `font-size`

<div></div>

- `rem` are always measured relative to the **document's root** `font-size`
- `vh` and `vw` are percentage measurements of the viewport's `height` and `width`

<div></div>
