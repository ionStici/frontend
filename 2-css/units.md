[&larr; Back](./README.md)

# Units

## Table of Content

- [What you need to know](#what-you-need-to-know)
- [Numbers](#numbers)
- [Percentages](#percentages)
- [Absolute lengths](#absolute-lengths)
- [Font-size-relative units](#font-size-relative-units)
- [Viewport-relative units](#viewport-relative-units)
- [em and rem](#em-and-rem)
- [Px to Rem Workflow](#px-to-rem-workflow)

<br>

## What you need to know

- Each property has an initial value, used if nothing is declared (and if there is no inheritance).
- Browsers specify a `root` `font-size` for each page (usually 16px).
- Percentages and relative values are always converted to pixels after the page is rendered.

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

<br>

## Numbers

Numbers (unitless integers) are used to define: opacity, line-height, transform, etc.

Numbers have meaning depending on their context.

<br>

## Percentages

- Percentages for width and height are measured relative to the dimensions of their parent element.
- Percentages for padding and margin, are measured relative only to the width of the parent element.

<br>

## Absolute lengths

**Absolute Units** are used to size content to _exact dimensions_.

| Unit | Name                | Equivalent to       |
| ---- | ------------------- | ------------------- |
| `cm` | Centimeters         | 1cm = 96px/2.54     |
| `mm` | Millimeters         | 1mm = 1/10th of 1cm |
| `Q`  | Quarter-millimeters | 1Q = 1/40th of 1cm  |
| `in` | Inches              | 1in = 2.54cm = 96px |
| `pc` | Picas               | 1pc = 1/6th of 1in  |
| `pt` | Points              | 1pt = 1/72th of 1in |
| `px` | Pixels              | 1px = 1/96th of 1in |

Absolute lengths are handy for designing print content.

### Miscellaneous units

- Angle units `60deg`
- Resolution units `192dpi`

<br>

## Relative lengths

**Relative Units** are relative to something else.

### Font-size-relative units

| unit  | relative to                                      |
| ----- | ------------------------------------------------ |
| `em`  | relative to the font-size of the closest element |
| `rem` | font-size of the root element (default is 16px)  |

Other units: `ex cap ch ic lh rlh`

### Viewport-relative units

| unit   | relative to                                      |
| ------ | ------------------------------------------------ |
| `em`   | relative to the font-size of the closest element |
| `rem`  | relative to the root font-size                   |
| `vw`   | 1% of viewport's width.                          |
| `vh`   | 1% of viewport's height.                         |
| `vmin` | 1% of the viewport's smaller dimension.          |
| `vmax` | 1% of the viewport's larger dimension.           |

Other units: `vi vb`

<br>

## em and rem

- `rem` sizing elements consistently across the entire website.
- `em` sizing elements in comparison to other elements nearby.

### em

`em` is relative to its own font-size, and in case it's not defined then it is relative to the font-size of its parent elements.

`X em = X em * font-size` - if the font-size is 10px, then `5em` will be 50px

### rem

`rem` stands for _root em_. `rem` is measured relative to the root font-size.

The default root `<html>` font-size is 16px, so by default `rem` is relative to 16px.

But we can change the root font-size, and so `rem` can be adjusted based on one single setting.

<br>

## Px to Rem Workflow

One global setting (the root font-size) to adjust all the measurements on our page.

The `rem` unit is always in relation to the root (html element) font-size. Whatever value we set the font-size of html, that will be equal to `1rem`. Like this, after we adjust the root font-size, the entire design changes (becomes bigger or smaller).

```css
html {
  /* font-size: 10px; */
  font-size: 62.5%;
}

body {
  font-size: 1.6rem; /* 16px */
  padding: 3.5rem; /* 35px */
}
```

**Pixels:** with pixels we override the default browser font-size setting, that the user can manually change in the browser settings. With pixels we remove the ability for users to adjust the website based on their own preference, the root font-size will not be affected by that anymore. We should use percentages instead.

**Percentages:** in this case, the user doesn't lose the ability to change the default font-size in the browser, the user can increase or decrease all the measurements on the page based on their change.

- In font-size, 100% is 16px. To get 10px from percentages: `100 / 16 * 10 = 62.5%`
- 0.625 multiplied by 18px (user changes) = 11.25px (the new root font-size)

<br>
