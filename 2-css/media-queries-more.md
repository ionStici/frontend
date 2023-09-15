[&larr; Back](./README.md)

# Media Queries

## Table of Content

- []()

<br>

## hover

The `hover` media feature - test whether the user's primary input mechanism can hover over elements.

- `(hover: hover)` the primary input mechanism can hover over elements (cursor).

- `(hover: none)` no primary pointing input mechanism (e.g., many mobile devices emulate hovering when the user performs an inconvenient long tap).

<br>

## inputmode attribute

```html
<input type="number" inputmode="numeric" />
```

[Read more on MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/inputmode)

<br>

## prefers-reduced-motion

`prefers-reduced-motion` feature query - detects user's settings relating to motion.

```css
a:hover {
  transform: scale(150%);
}
@media (prefers-reduced-motion: no-preference) {
  a {
    transition-duration: 0.4s;
    transition-property: transform;
  }
}
```

- `no-preference` the user didn't specify any motion preference.
- `reduce` the user enabled the setting on their device for reduced motion.

<br>
