[&larr; Back](./README.md)

# Flexbox

CSS Flexbox is a one-dimensional layout mechanism.

## Table of Content

- [Flexbox Terminology](#flexbox-terminology)
- [Flexbox Properties Overview](#flexbox-properties-overview)

<div></div>

- [Flex Container](#flex-container)
- [flex-direction](#flex-direction)
- [flex-flow shorthand](#flex-flow-shorthand)
- [flex-wrap](#flex-wrap)

<br>

## Flexbox Terminology

- The element on which we use `{ display: flex; }` is called the **Flex Container**.
- All direct children of the flex container are called the **Flex Items**.
- The direction in which Flex Items are displayed is called the **Main Axis**.
- The other perpendicular axis is called **Cross Axis**.

_We can change the direction of the Main Axis using `flex-direction`._

<br>

## Flexbox Properties Overview

| Container Properties | Item Properties |
| :------------------: | :-------------: |
|   `flex-direction`   |  `align-self`   |
|     `flex-wrap`      |     `order`     |
|  `justify-content`   |     `flex`      |
|    `align-items`     |   `flex-grow`   |
|   `align-content`    |  `flex-shrink`  |
|     `flex-flow`      |  `flex-basis`   |

We use properties on the flex container to position and align the flex items. And then some other properties we can directly use on flex items for individual styles.

**p.s.** The flex item can be at the same time a flex container.

<br>

## Flex Container

For an element to become a flex container:

```CSS
.flex {
    display: flex;
}
```

This will change the behavior of the flex container's direct child elements.

By default, the flex items will be aligned from left to right on the main axis (as a row), and if the flex container's width is less than the total width of the flex items, then flex items will shrink to accommodate the flex container's size (not wrapping).

_Note:_ With `gap` property we can insert space between flex items (not on outer edges). But `gap` is not exclusively for flexbox, it also works in grid.

## flex-direction

`flex-direction` is used to switch the axes direction.

```css
.flex {
  flex-direction: column;
}
```

- Properties for main axis: `justify-content` `flex-wrap` `flex-grow` `flex-shrink`.
- Properties for cross axis: `align-items` `align-content`

By changing the main axis to column, then properties for main axis will work for vertical alignment.

`flex-direction` values:

- `row` (default) elements will be positioned from left to right across the parent element starting from the top left corner.
- `column` elements will be positioned from top to bottom of the parent element starting from the top left corner.
- `row-reverse` and `column-reverse` works the same, but reverse the order of the flex items.

**p.s.** Reversing the content happens only visually, screen readers will only consider the order from the HTML.

## flex-wrap

`flex-wrap` controls if flex items will wrap into new lines in case there is no enough space, or not.

```css
.flex {
  flex-wrap: wrap;
}
```

- `nowrap` (default value) prevents flex items from wrapping (items will shrink if there is not enough space).
- `wrap` flex items that don't fit into a row will move down to the next line.
- `wrap-reverse` works as `wrap`, but the order of rows is reversed.

## flex-flow shorthand

`flex-flow` is a shorthand property for `flex-wrap` and `flex-direction`.

```css
.flex {
  flex-flow: column wrap;
}
```

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

### justify-content and align-items

```CSS
.flex {
    justify-content: center;
    align-items: center;

}
```

`justify-content` align the flex items from left to right along the Main Axis.

`align-items` align the items vertically along Cross Axis from top to bottom (only for a single row).

Most used values:

- `flex-start`, `flex-end` and `center` will position all flex items on the left or top, right or bottom, and in the center (no space between them).

- **Values only for `justify-content`:** `space-around`, `space-between`, `space-evenly` will position the flex items as the property name says.

- **Values only for `align-items`:**
  - `baseline` the bottom of the content of all items will be aligned with each other.
  - `stretch` (default value) the items will stretch from top to bottom of the flex container. Items with specified height will not stretch, only items with a minimum height specified or no height at all.

<br>

<br>

### align-content

`align-content` controls how rows are aligned along the cross axis _(when there is more than one row)_.

```css
.flex {
  align-content: center;
}
```

- `stretch` (default value) if a minimum height or no height is specified, the rows of elements will stretch to fill the parent container from top to bottom.
- `flex-start` `flex-end` `center` all rows of elements will be positioned at the top, bottom, center of the parent container with no extra space between
- `space-between` `space-around` all rows will be spaced from top to bottom as the value name says.

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

## Flex Items

_Note:_ A flex item can act as flex container at the same time, we can specify display to flex on flex items too.

_Note:_ Using `margin-right: auto;` on a flex item, will automatically use all the available space as margin.

<br>

## flex-grow

By default, flex items shrink proportionally when the flex container is too small. In case the flex container if bigger, we can use:

`flex-grow` property (declared on flex items) controls how much individual flex items should grow to fill the flex container.

```CSS
.item-one { flex-grow: 1; }
.item-two { flex-grow: 2; }
```

The default value of `flex-grow` is `0`. This will not allow flex items to grow.

As values we use integers that are related to the value of each flex item.

<br>

## flex-shrink

`flex-shrink` property can be used to specify which elements will shrink and in what proportions.

Default value of `flex-shrink` is `1`, which will allow flex items to shrink when the flex container is too small.

```css
.item {
  flex-shrink: 0;
}
```

If we set to `0`, then the element is no longer allowed to shrink.

As `flex-grow`, `flex-shrink` works in relation with other integers of this property on the rest flex items.

<br>

## flex-basis

`flex-basis` is used to specify the width of an item before it stretches or shrinks.

```css
.item {
  flex-basis: 150px;
}
```

<br>

## flex

`flex` is a shorthand property for: `flex-grow` -> `flex-shrink` -> `flex-basis`

```css
.item {
  flex: 2 1 100px;
}
```

<br>

### align-self

```css
.item {
  align-self: center;
}
```

Similar to `align-items`, but `align-self` can be declared separately on flex items.

<br>

### order

Reorder flex items inside its flex container.

```css
.item-1 {
  order: 2;
}

.item-2 {
  order: 1;
}
```

The initial value of `order` is `0` for each flex item.

Flexbox will order flex items according to their `order` number.

<br>
