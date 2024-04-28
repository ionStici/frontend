# Overflow

- `overflow` control overflow in the box model.
- `text-overflow` clipping individual lines of text.

## text-overflow

`text-overflow` works for text nodes, for example `<p>` elements.

It specifies how the text appears when it doesn't fit in the available space of the element.

Display text with ellipsis:

```css
p {
  text-overflow: ellipsis;
  width: 500px;
  overflow: hidden;
  white-space: nowrap;
}
```

_p.s._ All of the above properties must be defined for the ellipse effect to work.

## Overflow

We use overflow properties on a parent element to control what happens when its children need more space than it has available.

`overflow` property controls overflow. If 2 keywords are specified, the first applies to `overflow-x`, and second to `overflow-y`.

- `overflow-x` horizontal axis, left and right.
- `overflow-y` vertical axis, up and down.

### Values

- `visible` default
- `hidden` the content is clipped in the specified direction, no scrollbars.
- `scroll` enables scrollbars to allow users to scroll through content.
- `clip` content is clipped. Clip forbids all scrolling.
- `auto` gives responsibility for scrolling to the user and browser.

## Scroll properties

- [`scroll-behavior`](https://developer.mozilla.org/en-US/docs/Web/CSS/scroll-behavior) sets the behavior for a scrolling box. Use along with `prefers-reduced-motion`
- [`overscroll-behavior`](https://developer.mozilla.org/en-US/docs/Web/CSS/overscroll-behavior) sets what a browser does when reaching the boundary of a scrolling area.

## Hide Scrollbar But Keep Functionality

```css
/* Hide scrollbar for Chrome, Safari and Opera */
.example::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for IE, Edge and Firefox */
.example {
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}
```

## Scrolling and accessibility

Scrollable areas must accept focus so that keyboard users can tab to the box, and then use arrow keys to scroll.

```html
<div tabindex="0" role="region" aria-labelledby="id-of-text">content</div>
```

```
[role][aria-labelledby][tabindex] { overflow: auto; }
[role][aria-labelledby][tabindex]:focus { outline: 0.1em solid blue; }
```
