[&larr; Back](./README.md)

# The Box Model

## Table of Content

- [Box Model Areas](#box-model-areas)
- [box-sizing](#box-sizing)

<br>

## Box Model Areas

All elements on a web page are interpreted by the browser as "living" inside of a box.

Each box is made up of distinc tbox model areas that all do a specific job.

1. **Content Area** - the area that the content lives in (width and height)
2. **Padding** - space between content area and border
3. **Border** - surrounds the padding box
4. **Margin** - space between border and the outside edge of the element

[**Box Model representation on codepen**](https://codepen.io/web-dot-dev/pen/BaReoEV)

By default, the total dimensions of an element, are the sum of the content size, padding, border and margin.

**p.s.** Properties such as `outline` and `box-shadow` are painted on top, so they don't affect the size of our box.

<br>

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

This alternative box model tells CSS to apply the `width` and `height` to the border box instead of the content box. The border thickness and padding will be included inside of the box.

<br>

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

## Table of Content

- [Height and Width](#height-and-width)
- [Border](#border)
- [Padding](#padding)
- [Margin](#margin)
- [Vertical Margin Collapse](#vertical-margin-collapse)
- [Minimum and Maximum Height and Width](#minimum-and-maximum-height-and-width)
- [Overflow](#overflow)
- [Resetting Defaults](#resetting-defaults)
- [Visibility](#visibility)
- [box-sizing](#box-sizing)

<br>

## Height and Width

By default, the dimensions of an HTML box are set to hold the content of the box. We can change that with:

```css
div {
  width: 200px;
  height: 350px;
}
```

<br>

## Border

Border is a line that surrounds an element. It can be set with a specific width, style and color:

```CSS
div {
    border: 2px solid red;
    border-radius: 5px;  /* 50% = circle */
}
```

`border-radius` will change the radius of the corners of an element's border box.

<br>

## Padding

The space between the content and the border of a box.

We can set padding for each side of the box separately.

```css
div {
  padding: 10px 10px 10px 10px; /* top right bottom left */
}
```

Padding is often used to expand the background color of the box.

<!-- Because padding is inside the box, the background of the box will be visible in the space that it creates. If our box has overflow rules set, such as overflow: auto or overflow: scroll, the scrollbars will occupy this space too. -->

<br>

## Margin

The space outside of the box.

```css
div {
  margin: 10px auto;
}
```

Using `margin: 0 auto;` we can center elements. `auto` on left and right instructs the browser to adjust margins until the element is centered within its containing element.

<br>

## Vertical Margin Collapse

Concept not applied to horizontal margin or to padding in general.

_Top and bottom (vertical) margins collapse._

Between two adjacent elements, both with defined margin, only the larger margin is set.

```css
.div-1 {
  margin-bottom: 10px;
}

.div-2 {
  margin-top: 20px;
}
```

In the example above, as this two margins meet, only the 20px padding of div-2 is applied.

<br>

## Minimum and Maximum Height and Width

CSS properties that can limit how narrow or how wide an element's box can be sized to.

```css
div {
  max-width: 600px;
  min-width: 300px;

  max-height: 500px;
  min-height: 200px;
}
```

<br>

## Overflow

`overflow` property is set on a parent element to instruct the browser how to render child elements. It controls what happens to content that spills or overflows outside its box.

```css
div {
  overflow: visible;
}
```

- `visible` (default value) the overflow content will be displayed outside of the containing element.
- `hidden` any content that overflows will be hidden.
- `scroll` (a scrollbar will be added) the rest of the content can be viewed by scrolling.

For vertical or horizontal solutions: `overflow-x` and `overflow-y`.

<br>

## Resetting Defaults

Browsers have a default stylesheet, known as _user agent stylesheets_.

Many properties in CSS have a default value and don’t have to be explicitly set in the stylesheet.

User agent stylesheets usually have default CSS rules that set default values for padding and margin.

Reset margin and padding default values:

```css
* {
  margin: 0;
  padding: 0;
}
```

This is often the first CSS rule in an external stylesheet.

When properties are set to `0`, they do not require a unit of measurement.

<br>

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

<br>
