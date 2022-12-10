# **Responsive Images**

<br>

## **Table of Content**

- [Responsive Images Overview]()
- [Responsive Images in CSS]()
- [Art Direction]()
- [Density Switching]()

<br>

## **Responsive Images Overview**

Responsive images is a concept about providing the right image to the right screen size, resolution, pixel ratio.

Responsive images is also an aspect of web performance (not downloading unnecessary images on smaller screens). For instance, an image of 2mb is ok for a desktop computer, but for a phone we should deliver a compressed version of the image.

**Three use cases for Responsive Images:**

1. **Art Direction:** deliver a different version of the image for a different screen size (design reasons).

2. **Resolution Switching:** for smaller screens, deliver the same image but with a smaller resolution.

3. **Density Switching:** deliver the right image based on the pixel density of the device screen.

<br>

## **Responsive Images in CSS**

In HTML, images are embedded using the `<img>` tag, and then in CSS we use the `background-image` property.

Responsive images in CSS refers to the practice of writing media queries to load different images for different situations.

Another type of media query: **device resolution**.

_Reference_: **192 dpi** (dots per inch) is the resolution that apple retina screens use high resolution screens

```CSS
.header {
    background-image: url(./img-small.jpg);

    @media (min-resolution: 192dpi) and (min-width: 37.5em),
           (-webkit-min-device-pixel-ratio: 2) and (min-width: 37.5em),
           (min-width: 125em) {
                background-image: url(./img.jpg);
            }
}
```

The code above translates to:

- Normally (for small resolution screens), load a small image.
- Whenever the resolution is higher than 192 dots per inch, and the screen width is higher than 600px, then load a high resolution image.
- As second condition, for cases when the screen is huge (starting at 2000px) and have 1x resolution, then also load the high quality image.

In addition to 192 dpi, we also include a min-width of 600px too, because there might be phones with high resolution but with small screens, so there is no need to load a big image for them.

Safari doesn't support (min-resolution: 192dpi). For safari we use device-pixel-ratio property and then equal to 2, which means 2x (same as having 192dpi).

<br>

## **Art Direction**

Art Direction is like using media queries but in HTML. We make images depend on the screen width, so that different images will be used on different screen widths in the same place.

```HTML
<picture>
    <source srcset="logo-x1.png 1x, logo-2x.png 2x" media="(max-width: 37.5em)" />
    <source srcset="logo-big-x1.png 1x, logo-big-2x.png 2x" media="(max-width: 50em)" />
    <img srcset="logo-onex.png 1x, logo-twox 2x" src="logo-twox.png" />
</picture>
```

Inside the `media` attribute we specify the breakpoint.

We can have multiple `<source>` elements for different breakpoints.

`<img>` will act like a fallback in case the browser doesn't support the feature.

<br>

## **Density Switching**

Serve a larger version of the same image for high resolution screens, and serve a smaller version of the same image for a low desnity screen.

In the `srcset` attribute we specify 2 images and the **density descriptor** `1x 2x` for each.

```HTML
<img  srcset="logo-1x.png 1x, logo-2x.png 2x" />
```

The browser will choose the best option according to the screen that is displaying the webpage. For low density screens, it will use the 1x image. And then for high resolution screens the 2x image will be used.

_Explanation:_ Pixel density is the amount of pixels found in an inch.

There are low resolution screens and high resolution screens. If we want our images to look sharp on high-resolution screens, we need to provide a proper image.

- _Low resolution screens_ (**1x**) are typical PC screens which uses 1px to display 1px of the design. If we say an image should be 100px, then these screens would use 100 physical pixels in the screen to display these 100px.
- _High resolution screens_ (**2x**) uses 2 physical pixels to display one pixel of our design. If we say an image should be 100px high, it will use 200px in a physical screen.

<br>

## ** Resolution Switching**
