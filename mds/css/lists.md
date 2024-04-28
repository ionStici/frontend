# Lists

All `<li>` elements have `{ display: list-item; }` set, and the browser renders a `::marker` by default.

## List Styles

- `list-style-position` move the bullet point to either `inside` or `outside` the list-item's contents.

- `list-style-image` replace the list's bullet points with images using the `url()` function, or use `none` to remove the bullet point.

- `list-style-type` changes the bullet point to known style keywords, custom strings, emojis and [more](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type).

- `list-style` shorthand, any order.

## ::marker pseudo-element

Every `<li>` element has a `::marker` pseudo-element with some browser default styles.

If we declare `{ display: list-item; }` to any type of element, it will get a `::marker` pseudo-element that we can then style.

The marker box is their container that contains the bullet or number. We can style this marker box using the `::marker` selector.

`::marker` styling properties available: `animation-* transition-* color direction font-* content unicode-bidi white-space`
