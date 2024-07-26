# CSS Box Model

## Table of Contents

- [Box Model Areas](#box-model-areas)
- [box-sizing](#box-sizing)
- [Height and Width](#height-and-width)
- [Border](#border)
- [Outline](#outline)
- [Padding](#padding)
- [margin](#margin)
- [Min and Max Height and Width](#min-and-max-height-and-width)
- [Resetting Default Styles](#resetting-default-styles)
- [Overflow](#overflow)
- [Visibility](#visibility)

## Box Model Areas

All elements on a web page are interpreted by the browser as "living" inside of a box.

Each box is made up of distinct box model areas that all do a specific job.

1. **Content Area** - the area that the content lives in (width and height)
2. **Padding** - space between content area and border
3. **Border** - surrounds the padding box
4. **Margin** - space between border and the outside edge of the element

[**Illustration of the Box Model**](https://codepen.io/web-dot-dev/pen/BaReoEV)

By default, the total dimensions of an element are the sum of the content size, padding, border and margin.

**p.s.** Properties such as `outline` and `box-shadow` are painted on top, so they don't affect the size of our box.

## box-sizing

`box-sizing` property tells the box how to calculate its box size.

By default, all elements have this user agent style: `{ box-sizing: content-box; }`

This means that when you set dimensions such as `width` and `height`, they will be applied to the `content area`. If you then set `padding` and `border`, these values will be added to the content box's size.

We can reset this behavior of the box model for all html elements with:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

This CSS rule selects every element in the document and every `::before` and `::after` pseudo element and applies `box-sizing: border-box`. This means that every element will now have this alternative box model.

This alternative box model tells CSS to apply the `width` and `height` to the border box instead of the content box, which means that the border thickness and padding will be included inside of the box.

## Height and Width

By default, the dimensions of an HTML box are set to hold the content of the box.

```css
div {
  width: 200px;
  height: 350px;
}
```

## Border

[Border](https://web.dev/learn/css/borders/) is a line that surrounds an element.

It can be set with a specific width, style and color.

```CSS
div {
    border: 2px solid red;
    border-radius: 5px;  /* 50% = circle */
}
```

`border-radius` will change the radius of the corners of an element's border.

### Outline

**`outline`** property (works as border) is for outside of the element styling, and is not part of the box model.

```css
.box {
  outline: solid 1px #999; /* use "none" to remove outline */
}
```

- `outline-offset: 1rem;` sets the amount of space between an outline and the edge or border of an element.

In some _focus_ situations, we should use `box-shadow` instead of `outline`, because outline will insert some visual space, and it doesn’t adapt to rounded corners, it is always square.

_p.s._ Shadows don't show up in Windows High Contrast Mode, so in this situation it's not a good idea to replace outline with shadows for focus use cases.

## Padding

The space between the content and the border of a box.

We can set padding for each side of the box separately.

```css
div {
  padding: 10px 10px 10px 10px; /* top right bottom left */
}
```

Padding can be used to expand the background color of the box.

## Margin

The space outside of the box.

```css
div {
  margin: 10px auto -100px auto;
}
```

- `margin: 0 auto;` will center block elements. `auto` on left and right instructs the browser to adjust margins until the element is centered within its containing element.

- Negative margin will reduce the outer space, potentially overlapping elements.

- **Vertical Margin Collapse:** between two adjacent elements, both with defined margin, only the larger margin will apply (only block margins collapse).

## Min and Max Height and Width

CSS properties that can limit how narrow or how wide an element's box can be sized to.

```css
div {
  max-width: 600px;
  min-width: 300px;
  max-height: 500px;
  min-height: 200px;
}
```

## Resetting Default Styles

[**A Modern CSS Reset**](https://andy-bell.co.uk/a-modern-css-reset/)

Web browsers apply default styles to elements via user agent stylesheets, which can lead to inconsistencies across different browsers. To standardize styling and ease cross-browser design, developers often use a CSS reset:

```css
* {
  margin: 0;
  padding: 0;
}
```

This reset removes default padding and margin, setting a consistent starting point for styling.

When properties are set to `0`, they do not require a unit of measurement.

## Overflow

`overflow` property is set on a parent element to instruct the browser how to render child elements. It controls what happens to content that overflows outside its box.

```css
div {
  overflow: visible;
}
```

- `visible` (default value) the overflow content will be displayed outside of the containing element.
- `hidden` any content that overflows will be hidden.
- `scroll` (a scrollbar will be added) the rest of the content can be viewed by scrolling.

For vertical or horizontal solutions: `overflow-x` and `overflow-y`.

## Visibility

```css
div {
  visibility: visible;
}
```

- `hidden` hides an element
- `visible` (default) displays an element
- `collapse` collapses an element

_Difference between display and visibility:_

- `display: none;` will completely remove an element from the document.
- `visibility: hidden` the element will not be visible, but the space reserved for it will. The element is rendered, it just isn't seen on the page.
