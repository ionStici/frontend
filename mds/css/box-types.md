# Box Types

Every HTML element has a default `display` value that dictates how the box behaves. If it shares horizontal space with other elements, if it fills the entire browser area from left to right, etc.

We can change this default behavior using the `display` property.

## Table of Content

- [Inline Elements](#inline-elements)
- [Block-level Elements](#block-level-elements)
- [Inline-Block Elements](#inline-block-elements)
- [Display: none](#display-none)

## Inline Elements

```css
div {
  display: inline;
}
```

- Content is distributed in lines. No line-breaks.
- Occupies only the space that its content needs.
- We cannot use `height` or `width` on inline boxes.
- We can specify only horizontal padding and margin for inline elements.

## Block-level Elements

```css
div {
  display: block;
}
```

- 100% of parent's width.
- Create line breaks after and before it.
- Vertically, one after another.

## Inline-Block Elements

```css
div {
  display: inline-block;
}
```

Inline-block elements are technically also inline elements, but which works as a block-level element on the inside. Inline-block combines both features.

So since they're technically inline elements, they use only the content's space, cause no line breaks, and can appear next to each other.

But since they work as a block-level box in the inside, we can use `width` and `height` properties on them, and also vertical padding and margin.

## Display: none

```css
div {
  display: none;
}
```

It will completely remove the element from the document, the accessibility tree, and will no longer be announced by screen readers.
