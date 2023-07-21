[&larr; back](./README.md)

# Responsive Images

- With **Descriptive Syntaxes**, we provide the browser with information about image sources and how they'll be used, but ultimately leaves the decision-making to the browser.

- With **Prescriptive Syntaxes**, we tell the browser what to do—what source to select, based on specific criteria we've defined.

<br>

## Table of Content

- [Descriptive Syntaxes](#descriptive-syntaxes)
- [Describing density with x](#describing-density-with-x)
  - [The srcset attribute](#the-srcset-attribute)
- [Describing widths with w](#describing-widths-with-w)
- [Describing usage with sizes](#describing-usage-with-sizes)
- [Walkthrough](#walkthrough)

<br>

## Descriptive Syntaxes

How to give the browser a choice of images so that it can make the best decisions about what to display.

<br>

## Describing density with x

- **Physical pixels:** the actual number of pixels a device has.
- **Logical pixels:** equals with the CSS unit of absolute length px.

The ratio between a device's logical pixels and physical pixels is the **device pixel ration** (PDR). PDR is calculated by dividing the device's actual screen resolution by a viewport's CSS pixels.

```js
window.devicePixelRatio; // 2 | (2560 x 1600 = 4.096.000) / (1920 x 1080 = 2.073.600) ≈ 2
```

A DPR of `2` means that the physical resolution of the screen is double the logical resolution.

If you view a 400px-wide image on a display with a DPR of `2`, each logical pixel is being rendered across 4 of the display's physical pixels: two horizontal and two vertical. The image doesn't benefit from the high-density display — it will look the same as it would on a display with a DPR of 1.

In order for images to benefit higher resolutions, we have to provide wider images for such resolutions. For example, a 800px image scaled down to fit a space of 400 logical pixels wide, will make the image look sharper. This 800-pixel image source has double the pixel density, resulting in logical pixels filling more physical pixels.

Besides this, on a low-density display, an image suitable for higher-density displays will look like any other low-density image.

### The srcset attribute

```html
<img src="low-density.jpg" srcset="double-density.jpg 2x" />
```

The `srcset` attribute identifies one or more comma-separated candidates for rendering an image. Each candidates is made up of two things: a URL and a syntax that describes that image source. Each candidate is `srcset` is described by its inherent width `w` or intended density `x`

The `x` syntax is a shorthand for "this source is appropriate for a display with this density". A candidate followed by `2x` is appropriate for a display with a DPR of 2.

For browsers without support for `srcset`, the attribute and its contents will be ignored, and the contents of `src` will be requested, as usual.

**Important:** by indicating the density in `srcset`, we don't tell the browser to use that image in case the display's DPR is 2x, instead we just inform the browser with the density the image has from that URL, and then the browser will do the appropriate decision on its own.

<br>

## Describing widths with w

```html
<img src="small.jpg" srcset="small.jpg 600w, large.jpg 1200w" />
```

The `w` syntax describes the inherent width of each candidate source.

<br>

## Describing usage with sizes

Accessible browser-level information: the size of the user's viewport, the pixel density of the user's display, user preferences, and so on.

Even so, we need to provide the browser with information through markup for further requests for the appropriate images.

```html
<img
  sizes="80vw"
  srcset="small.jpg 600w, medium.jpg 1200w, large.jpg 2000w"
  src="fallback.jpg"
/>
```

The `sizes` attribute - "here is the size of the rendered image in the layout." - the way we describe the image is relative to the viewport.

Above, `sizes` value informs the browser that the space in our layout that the `img` occupies has a width of `80vw` = 80% of the viewport. Remember that this is a description of the image's size in the page layout.

As a developer, your job is done. You've accurately described a list of candidate sources in `srcset` and the width of your image in `sizes`, the rest is up to the browser.

## Walkthrough

We've informed the browser that the image will take up 80% of the available viewport, on a device with a 1000 pixel-wide viewport, the image will occupy 800 pixels. The browser will then take that value and divide each of the image source candidates we specified in `srcset`.

600÷800=**.75** | 1200÷800=**1.5** | 2000÷800=**2.5** these results are DPR options specifically tailored to the user's viewport size. Since the browser also has information on the user's display density at hand, it makes a series of decisions:

On the current 1000px viewport, `small.jpg` is discarded, because a DPR lower than 1 would require upscaling. On a device with a DPR of 1, `medium.jpg` provides the closest match with a DPR of 1.5, a little larger than necessary, but downscaling is a visually seamless process. On a device with a DPR of 2, `large.jpg` is the closest match.

If the same image is rendered on a 600 pixel wide viewport, the result of all that math would be completely different: `80vw` is now `480px`. When we divide our sources' widths against that, we get 1.25, 2.5, and 4.16. At this viewport size, `small.jpg` will be chosen on `1x` devices, and `medium.jpg` will match on `2x` devices.

By using a descriptive syntax rather than a prescriptive one, we don't need to manually set breakpoints and consider future viewports and DPRs — we simply supply the browser with information and allow it to determine the answers for us.

## sizes and calc()

Because our `sizes` value is relative to the viewport and completely independent of the page layout, it adds a layer of complication. It's rare to have an image that only occupies a percentage of the viewport, without any fixed-width margins, padding, or influence from other elements on the page. You'll frequently need to express the width of an image using a combination of units; percentages, em, px, and so on.

```html
<img sizes="calc(100vw-2em)" />
```

We can use `calc()`, allowing us to mix-and-match CSS units—for example, an image that occupies the full width of the user's viewport, minus a 1em margin on either side.

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

- [Responsive Images Overview](#responsive-images-overview)
- [Image Optimizations](#image-optimizations)
- [Responsive Images in CSS](#responsive-images-in-css)
- [Art Direction](#art-direction)
- [Density Switching](#art-direction)
- [Density and Resolution Switching](#density-and-resolution-switching)

<br>
 
## Responsive Images Overview

Responsive images is a concept about providing the right image to the right screen size, resolution, pixel ratio.

Responsive images is also an aspect of web performance (not downloading unnecessary images on smaller screens). For instance, an image of 2mb is ok for a desktop computer, but for a phone we should deliver a compressed version of the image.

**Three use cases for Responsive Images:**

1. **Art Direction:** deliver a different version of the image for a different screen size (design reasons).

2. **Resolution Switching:** for smaller screens, deliver the same image but with a smaller resolution.

3. **Density Switching:** deliver the right image based on the pixel density of the device screen.

<br>

## Image Optimizations

Image Optimizations in terms of dimensions and of file size.

**Rule:** The image size should be double of the size that it is displayed on the screen.

High density screens needs 2px of the image to display 1px in the design.

**Step 1:** Start with a big image, and when we finish the design, check the largest width that the image would have on the page. Example: largest 200px, so double to 400px. Now resize the image width to 400px.

**Step 2:** Compress the images

- Compress the images in order to reduce the file size. Tool for compressing images [squoosh](https://squoosh.app/)
- Recommended file format: _WebP_. Better alternative, which increases the quality and reduces image size.
- Because not all browsers support WebP, check for browser support.

**Deliver WebP and PNG based on browser support**

```html
<picture>
  <source srcset="./img.webp" type="image/webp" />
  <source srcset="./img.png" type="image/png" />
  <img src="./img.png" class="img" alt="" />
</picture>
```

Inside the `<picture>` element, we define possible alternatives for the `<img>` with the `<source>` element.

In the `type` attribute we define the image format.

The browser will select which of these 2 images can display better based on browsers support.

We still have to include `<img>` tag with its `class` and `alt` attributes, because these are the ones that will be used. The browser will replace the `src` of `<img>` with one of the alternatives from `<source>`.

Also, the `src` from `<img>` will act as a fallback in case the browser doesn't understand the `<source` element.

<br>

## Responsive Images in CSS

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

## Art Direction

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

_Note:_ you have to include the `<img>` element with its `src` attribute in order for `<source>` tags to work properly.

<br>

## Density Switching

Serve a larger version of the same image for high resolution screens, and serve a smaller version of the same image for a low density screen.

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

## Density and Resolution Switching

Let the browser choose the best image for the current viewport and for the pixel density:

```html
<img
  srcset="nat-1.jpg 300w, nat-1-large.jpg 1000w"
  sizes="(max-width: 900px) 20vw, (max-width: 600px) 30vw, 300px"
  src="nat-1-large.jpg"
/>
```

`srcset` - 2 images, 300px and 1000px width. Instead of density descriptors, we specify the **width descriptors**. We inform the browser of the width for each image, without the browser having to download them to get access to that information. Knowing the image width is not enough for the browser to choose the right image, we still need the sizes attribute.

`sizes` - inform the browser about the approximate width of the image at different viewport width. As values - breakpoints approximately that the width of the image will be.

- _900px_ - then the image width 20vw (20% of the screen width viewport).
- _600px_ - here the image width is 30% of the screen width, 30vw.
- At the end, specify the default size, approximately 300px, if none of the before conditions apply.
- Don’t forget about the alt attribute.

With both srcset and sizes - the browser can figure out which is the perfect image to use for the current viewport width and the current display resolution.

`src` - we should include this too, in case the user is using an older browser which doesn’t support srcset or sizes. If the browser cant understand any of those, he can still use the src attribute.

This example will take care for both, resolution and density switching. We gave the browser enough information to figure out exactly what to do depending on both the viewport and the pixel density (screen resolution).

<br>
