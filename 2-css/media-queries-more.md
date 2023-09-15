[&larr; Back](./README.md)

# Media Queries

## prefers-reduced-motion

`prefers-reduced-motion` feature query - detects user's settings relating to motion.

- `no-preference` the user didn't specify any motion preference.
- `reduce` the user enabled the setting on their device for reduced motion.

```css
a:hover {
  transform: scale(150%);
}
@media (prefers-reduced-motion: no-preference) {
  a {
    transition: 0.4s transform;
  }
}
```

## resolution Media Feature

You can adjust your styles for different pixel densities using the [`resolution`](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/resolution) media feature. It comes in three varieties: minimum, maximum, and exact. `dpi` - dots per inch

```css
@media (min-resolution: 300dpi) { // The display has a pixel density of at least 300 dots per inch. }
@media (max-resolution: 300dpi) { // The display has a pixel density less than 300 dots per inch. }
@media (resolution: 300dpi) { // The display has a pixel density of exactly 300 dots per inch. }
```

Usually we don't need `resolution` MQ, because we define pixel density directly in HTML.

## hover

The `hover` media feature - test whether the user's primary input mechanism can hover over elements.

- `(hover: hover)` the primary input mechanism can hover over elements (cursor).

- `(hover: none)` no primary pointing input mechanism (e.g., many mobile devices emulate hovering when the user performs an inconvenient long tap).

<br>
