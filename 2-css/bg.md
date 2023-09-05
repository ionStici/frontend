[&larr; Back](./README.md)

# Backgrounds

## Table of Content

- [Background Images](#background-images)
- [background-repeat](#background-repeat)
- [background-position](#background-position)
- [background-size](#background-size)
- [background-attachment](#background-attachment)
- [background-origin](#background-origin)
- [background-clip](#background-clip)
- [background shorthand](#background-shorthand)

<br>

## Background Images

**`background-image`** property sets a background Image or a Gradient.

Add multiple backgrounds by adding multiple sources that are comma separated.

The first background is the closest to the user, while the last background is the furthest from the user.

A background image may fail to load, set a `background-color` on the final layer to ensure good contrast.

<br>

## background-repeat

By default, background images repeat horizontally and vertically to fill the entire space of the background layer.

The **`background-repeat`** property can change this behavior. Values: `repeat ` `round ` `space ` `no-repeat `

If 2 values are used, first = horizontal axis, second = vertical axis.

[background-repeat on mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/background-repeat)

<br>

## background-position

The [`background-position`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-position) property allows you to change the position of the image.

The initial position of background images is ` top left`

_p.s._ The first value represents the horizontal axis and the second the vertical axis.

_p.s._ In case we skip one value, the omitted value resolves to `50%`

It accepts from 1 to 4 pars. Length units & Keywords ` top bottom left right center`.

<br>

## background-size

[`background-size`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-size) property sets the size of background images.

By default, background images are sized based on their actual width.

`background-size` requires percentage and length values or keywords.

The property accepts up to 2 parameters corresponding to width and height.

- `auto` default

- `cover` covers the entire area of the background layer

  The image may get stretched or cropped.

- `contain` sizes the image to fill the space without stretching or cropping.

  As a result empty space can remain that will cause the image to repeat.

<br>

## background-attachment

[`background-attachment`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-attachment)

- `scroll` default

- `fixed` the background is fixed relative to the viewport. See [DEMO](https://codepen.io/web-dot-dev/pen/MWoozvN)

- `local` The background is fixed relative to the element's contents. If the element has a scrolling mechanism, the background scrolls along with the element's contents.

<br>

## background-origin

[`background-origin`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-origin)

- See [DEMO](https://codepen.io/web-dot-dev/pen/ExvyXeZ)
- Keywords the property accepts `border-box padding-box content-box`

<br>

## background-clip

[`background-clip`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-clip)

- See [DEMO](https://codepen.io/web-dot-dev/pen/vYJKZba)
- Keywords the property accepts `border-box padding-box content-box`

<br>

## background shorthand

```
.box {
  background:
    <background-image>
    <background-position> / <background-size>
    <background-repeat>
    <background-attachment>
    <background-origin>
    <background-clip>
    <background-color>
  ;
}
```

Order is important. The position and size values must both be provided, separated by a slash `/`.

_p.s._ Any background proeprties omitted in the shorthand are set to their initial values.

<br>
