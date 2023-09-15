[&larr; back](./README.md)

Label **Legacy**

# Responsive Design - Media Queries

## Table of Content

- [Responsive Design Overview](#responsive-design-overview)
  - [Resposnive Design Practical Principles](#resposnive-design-practical-principles)
- [Viewport Meta Tag](#viewport-meta-tag)
- [How to Select Breakpoints](#how-to-select-breakpoints)
- [Desktop-First vs. Mobile-First](#mobile-first-vs-desktop-first)
  - [Desktop-First](#desktop-first)
  - [Mobile-First](#mobile-first)
  - [Mobile-First: Pros and Cons](#mobile-first-pros-and-cons)
- [How Media Queries Work](#how-media-queries-work)
  - [Clarification](#clarification)
- [`and` Operator and Comma Separated List](#and-operator-and-comma-separated-list)
- [Range](#range)
- [Units in Media Queries](#units-in-media-queries)
  - [Pixels as root font-size](#pixels-as-root-font-size)
- [Dots Per Inch (DPI)](#dots-per-inch-dpi)
- [hover media feature](#hover-media-feature)

<br>

## Viewport Meta element

Meta element that enables responsive design.

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
</head>
```

- `width=device-width` tells the browser to assume the width of the website is the same as the width of the device.
- `initial-scale=1` tells the browser how much or how little scaling to do, with RD you don't want the browser to do any scaling at all.

<br>

## Responsive Design Overview

**Responsive Design** is a design technique to make a webpage adjust its layout and visual styles to any possible screen sizes, so that we can use the website on all devices.

### Resposnive Design Practical Principles

1. **Fluid Grids And Layouts:** Use relative units like percentages and max-width property when building layouts, this will allow content to adapt to the current viewport width.
2. **Responsive Images:** ensure that images adapt correctly to the current viewport (use `%`).
3. **Media Queries:** allow us to create different version of our website for different widths by changing CSS styles on certain viewport widths (breakpoints).
4. **Responsive Units:** with the `rem` unit we can scale the entire layout automatically.

<br>

## Viewport Meta Tag

Required meta tag - for responsive design to work properly.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

[The Viewport Meta Tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag) allow web pages to be responsive and adapt the content to the user's screen size.

Without the viewport meta tag, browsers on smaller screens will zoom the page out by default until it fits the screen, making media queries not work.

This tag will make the page match the screen size. As written in the attribute value, the width will be equal to the device width, and the scale initially should be 100% `1.0`.

- `name="viewport"` tells the browser to display the web page at the same width as its screen
- `content` defines the values for the `<meta>` tag, including `width` and `initial-scale`
- `width=device-width` key-value pair: controls the size of the viewport in which it sets the width of the viewport to equal the width of the device
- `initial-scale=` key-value pair: sets the initial zoom level

<br>

## How to Select Breakpoints

**Breakpoints** are viewport points at which we set our media queries and want our design to change.

**Selecting Breakpoints:** The best approach is to select breakpoints at places where our design breaks down.

We start at the main screen size, then start decreasing or increasing the screen width, and as soon as the design no longer looks acceptable, we create a new breakpoint.

[List of breakpoints by device widths](https://content.codecademy.com/courses/freelance-1/unit-5/screen-sizes.png?_gl=1*1jl0eun*_ga*MDgzNjExMzUzMi4xNjYyOTc0NjY0*_ga_3LRZM6TM9L*MTY3MzQwNjYxNS4xOTUuMS4xNjczNDEwODc5LjYwLjAuMA..)

**As a rule of thumb**, a media query should work over a range of at least 200 or 300 pixels. We should not add media queries every 50px to fix every single design problem that appears as we scale down the page.

<details>
<summary>General idea</summary>

- Phones: 0 - 600px
- Portrait tablets: 600 - 900 px
- Landscape tablets: 900 - 1200 px
- Desktops: 1200x +
- Big desktops: 1800px +
</details>

<details>
<summary>More detailed</summary>

- Mobile S: 320px
- Mobile M: 375px
- Mobile L: 425px
- Tablet: 768px
- Laptop S: 1024px
- Laptop M: 1440px
- Laptop L: 1920px
</details>

<details>
<summary>More</summary>

- Try to always write a media query at `1200px`.
- We should ensure that our webpage looks good on big screens too `1920px`.

</details>

<br>

## Mobile-First vs. Desktop-First

Two fundamental aspects of modern responsive design are: deciding about doing mobile-first or desktop-first.

### Desktop-First

**Desktop-First Approach** - we start by writing our general CSS for large screens. Then, when we implement responsive design for our website, we write media queries for `max-width` in order to shrink the design to fit smaller screens.

### Mobile-First

**Mobile-First Approch** - we start by writing our general CSS for smaller screens, optimizing for mobile. Then, move up to larger screens using media queries and `min-width`.

### Mobile-First: Pros and Cons

The philosophy behind this strategy: improve the mobile experience by reducing the website to the absolute essentials, in order to end up with a smaller and faster final product, completely optimized for mobile users. Prioritize content over purely aesthetic design. The world is becoming more and more mobile.

<details>
<summary>Pros</summary>

100% optimized for the mobile experience

Reduces websites and apps to the absolute essentials

Results in smaller, faster and more efficient products

Prioritizes content over aesthetic design, which may be desirable

</details>

<details>
<summary>Cons</summary>

The desktop version might feel overly empty and simplistic

More difficult and counterintuitive to develop

Less creative freedom, making it more difficult to create distinctive products

Clients are used to see a desktop version of the site as a prototype

Do your users even use the mobile internet? What’s the purpose of your website?

</details>

<br>

## How Media Queries Work

```css
@media only screen and (max-width: 768px) {
  html {
    font-size: 8px;
  }
}
```

The media query checks if the current viewport meets the specified conditions, and if it does, then all the CSS inside the media query will applied.

In the example above, the CSS styles will apply if the viewport width is less or equal to 500px.

Inside media queries we override specific parts of the global CSS at certain viewport widths.

**The order of media queries is important.**

In a situation when multiple media queries with conflicting CSS declarations are active, then the one which appears last in the code will apply.

### Clarification

Media Queries can detect the size of the current screen and apply different CSS styles depending on the width of the screen.

- `@media` — keyword begins a media query rule and instructs the CSS compiler on how to parse the rest of the rule.
- `only screen` — Indicates the device type — `screen` keyword is the the media type for displaying content, no matter the type of device.
- `and (max-width: 768px)` — _media feature_, instructs the CSS compiler to apply the CSS styles to devices with a width of 768px or smaller. Media features are the conditions that must be met in order to render the CSS within a media query.
- CSS rules are nested inside of the media query's curly braces. The rules will be applied when the media query is met.

<div></div>

- `(min-width)` and `(min-height)` are used to set the minimum width and minimum height.
- `(max-width)` and `(max-height)` set the maximum width and maximum height.

<br>

<br>

## `and` Operator and Comma Separated List

```css
@media only screen and (min-width: 500px), (orientation: landscape) {
}
```

The `and` operator is used to chain multiple media features.

The `and` operator require both media features to be true to apply the CSS within the media query.

The Comma Separated List will apply the media query rule if at least one meadia feature is met.

The `orientation` media feature detects if the page has more width than height: `landscape` if the page is wider; `portrait` if the page is taller;

<br>

## Range

```css
@media only screen and (min-width: 320px) and (max-width: 480px) {
  /* ruleset for 320px - 480px */
}
```

By using multiple widths and heights, we can define a media query for a specific range.

In the example above, CSS rules would apply when the screen size is between 320px and 480px.

<br>

## Units in Media Queries

In the media query rule, `rem` do not respond to the root font-size setting. Instead, `1rem` here will always be the default browser font-size. Besides this, `rem` has some bugs in some browsers when used in media queries.

Also, don't use pixels in media queries because it will not adjust with the user's font-size in the browser in case he will change it (zoom level).

Instead, use `em` (safer). To convert pixels to em, divide pixels by 16px:

- `1200 / 16 = 75em`
- `@media (max-width: 75em) {}`

`1em` in media queries rule will always be equal to the font-size coming from the browser, which is the default 16px. And if the user changes it to 20px, therefore our units will correspond.

<br>

### Pixels as root font-size

[Stack Overflow](https://stackoverflow.com/questions/13237782/safari-doesnt-calculate-rem-units-correct-when-scaling-with-media-width-heigh)

Safari doesn't calculate `rem` units (relative to root font-size) properly when scaling with media queries.

Solution: convert root font-size from percentages to pixels:

- `0.625 * 16 = 10px`
- `0.20 * 16 = 8px`

<br>

## Dots Per Inch (DPI)

Another media feature we can target is screen resolution.

Deliver higher quality media like images or video only to users with screens that can support high resolution media.

Targeting screen resolution helps users avoid downloading high resolution (large file size) images that their screen may not be able to properly display.

To target by resolution, we can use the `min-resolution` and `max-resolution` media features. These media features accept a resolution value in either dots per inch (dpi) or dots per centimeter (dpc).

[About Resolution Measurements](https://en.wikipedia.org/wiki/Dots_per_inch)

```css
@media only screen and (min-resolution: 300dpi) {
  /* CSS for high resolution screens */
}
```

The media query in the example above targets high resolution screens by making sure the screen resolution is at least 300 dots per inch. If the screen resolution query is met, then we can use CSS to display high resolution images and other media.

<br>

## hover media feature

```css
@media (hover: none) {
}
/* @media (hover: hover) {} */
```

`hover` media features can identify if the user can hover over elements or not, we kind of identify touch devices or mouse.

<br>
