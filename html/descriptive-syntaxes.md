# Responsive Images

- With **Descriptive Syntaxes**, we provide the browser with information about image sources and how they'll be used, but ultimately leaves the decision-making to the browser.

- With **Prescriptive Syntaxes**, we tell the browser what to do — what source to select, based on specific criteria we've defined.

## Descriptive Syntaxes

How to give the browser a choice of images so that it can make the best decisions about what to display.

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

The `srcset` attribute identifies one or more comma-separated candidates for rendering an image. Each candidates is made up of two things: a URL and a syntax that describes that image source. Each candidate in `srcset` is described by its inherent width `w` or intended density `x`

The `x` syntax is a shorthand for "this source is appropriate for a display with this density". A candidate followed by `2x` is appropriate for a display with a DPR of 2.

For browsers without support for `srcset`, the attribute and its contents will be ignored, and the contents of `src` will be requested, as usual.

**Important:** by indicating the density in `srcset`, we don't tell the browser to use that image in case the display's DPR is 2x, instead we just inform the browser with the density the image has from that URL, and then the browser will do the appropriate decision on its own.

## Describing widths with w

```html
<img src="small.jpg" srcset="small.jpg 600w, large.jpg 1200w" />
```

The `w` syntax describes the inherent width of each candidate source.

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

## Breakpoints

`sizes` accepts a comma-separated set of candidates for the rendered size of the image. Those conditions use the familiar media query syntax. This syntax is first-match: as soon as a media condition matches, the browser stops parsing the `sizes` attribute, and the value specified is applied.

```html
<img
  sizes="(min-width: 1200px) calc(80vw - 2em), 100vw"
  srcset="small.jpg 600w, medium.jpg 1200w, large.jpg 2000w"
  src="fallback.jpg"
/>
```

If the media query doesn't match, the next value `100vw` has no qualifying condition and so it is the one selected.

<br>
