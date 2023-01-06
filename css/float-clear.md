[&larr; Back](./README.md)

# Float and Clear

## Table of Content

- [Float](#float)
- [Clear](#clear)

<br>

## Float

The `float` property is commonly used for wrapping text around an image.

```css
div {
  float: left; /* right */
}
```

- `left` moves elements as fas left as possible.
- `right` moves elements as far right as possible.

Floated elements must have a width specified, otherwise, the element will assume the full width of its containing element, and changing the float value will not yield any visible results.

<br>

## Clear

When multiple floated elements have different heights, it can affect their layout on the page.

The `clear` property specifies how elements should behave when they bump into each other on the page. Values: `left` `right` `both` `none`.

```css
div {
  width: 500px;
  float: left;
}

div.item {
  clear: left;
}
```

Check MDN for documentation.
