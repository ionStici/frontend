# Image Formats

## Table of Content

- [SVG Vector Images](#svg-vector-images)
- [Raster Images](#raster-images)
- [Squoosh Tool](#squoosh-tool)
- [GIF](#gif)
- [PNG](#png)
- [JPEG](#jpeg)
- [WebP](#webp)
- [AVIF](#avif)

<br>

## SVG Vector Images

**Vector graphics** are a method of communicating a series of shapes, coordinates, and paths to their rendering context. They are a set of instructions for how an image should be drawn.

**Scalable Vector Graphics (SVG)** is an XML-based markup language developed by the W3C. It is a vector image format designed for the modern web.

We can convert images to SVG. SVG can be styled with CSS, or contain JavaScript that builds behaviors and interactions into the images themselves.

[MDN SVG Tutorial](https://developer.mozilla.org/docs/Web/SVG/Tutorial/Introduction)

## Raster Images

Common raster image formats: JPEG, GIF, PNG, WebP.

Raster Images - a set of pixel-by-pixel instructions for rendering a two-dimensional grid.

The way different image formats compresses and encodes these instructions differs, resulting in a huge variance between file sizes, where the same end user image has no discernible difference in quality.

For artwork containing real world levels of detail, raster images are the right tool for the job.

Choosing the appropriate type of raster image ultimately comes down to the use case.

A server doesn't send an image over the wire to a browser, but a stream of bytes describing the pixel grid that makes up that image for the client to recompose.

## Squoosh Tool

[**Squoosh**](https://squoosh.app/) - maintained by the Chrome team - provides a side-by-side comparison between different methods of encoding and configuring image outputs, with configuration options ranging from a 0-100 global "quality" slider, to the ability to fine-tune details of chrominance vs. luminance resampling. The lower the "quality" number, the higher the compression, and the smaller the resulting file will be.

## GIF

GIF (Graphics Interchange Format)

How GIF supports its flipbook-like animation: a single frame is drawn to the logical screen, then replaced by another, then another.

The GIF's pixel grid is build using color indexing technique.

In practice, the combination of lossless compression and palette quantization means that GIF isn't very useful in modern web development. Lossless compression doesn't do enough to reduce file sizes, and a reduced palette means an obvious reduction in quality.

## PNG

PNG (Portable Network Graphics)

PNG uses _lossless compression_, meaning that the image data will be compressed without any loss of visual fidelity.

- PNG supports “alpha channel” transparency, meaning that each pixel can be set to a level of transparency between 0 (fully transparent) and 255 (fully opaque).
- GIF treats transparency as a binary proposition — a pixel is either an opaque color, or fully transparent.

PNG will never reduce visual quality, but this results in excessively large file sizes compared to more modern web-friendly encodings, such as WebP (which btw also supports semi-transparency).

In practical terms, PNG is a sound choice for maintaining a manageable-sized “canonical” version of a source image, saved in your local development environment or committed to a project repository in case future versions of that image need to be edited or re-saved in alternate formats. Also, it may be used as a fallback version.

## JPEG

File extension: `.jpg` or `.jpeg`

JPEG (Joint Photographic Experts Group) - the most common type of image used on the web. JPEG-style encoding is much, much more efficient.

### Progressive JPEG

Progressive JPEG (PJPEG) effectively reorders the process of rendering a JPEG.

- "Baseline" JPEGs are rendered from top to bottom as the transfer progresses.
- Progressive JPEG breaks rendering into a set of full-sized "scans", with each scan increasing the quality of the image. The entire image appears immediately, albeit blurry, and grows clearer as the transfer continues.

PJPEG can feel faster than a baseline JPEG to the end user.

Decoding PJPEG is more complex on the client side, which means putting a little more strain on the browser and device's hardware—during rendering.

## WebP

**WebP** is an unbelievably versatile format, it supports: lossless compression, PNG-like alpha channel transparency, GIF-like animation, JPEG-style lossy compression.

WebP features: block prediction and adaptive block quantization.

- **Block Prediction:** the process through which the contents of each chrominance and luminance block are predicted based on the values of their surrounding blocks.

  The results provided by each prediction mode are then compared to the real image data, and the closest predictive match is selected.

- **Adaptive block quantization** - WebP takes an adaptive approach to quantization: an image is broken into up to four visually similar segments, and compression parameters for those segments are tuned independently.

Squoosh will serve well for encoding WebP.

## AVIF

AV1 Image File Format (AVIF) is an encoding based on the open source AV1 video codec.

AVIF is even newer than WebP, only supported in Chrome and Opera since 2020, Firefox in 2021, and Safari in 2022.

As with WebP, AVIF aims to address every conceivable use case for raster images on the web: GIF-like animation, PNG-like transparency, and improved perceptual quality at file sizes smaller than JPEG or WebP.

### Browser Support

Support for GIF, PNG, and JPEG is guaranteed across all browsers, and has been for decades. Relative to those legacy image formats, AVIF is brand new, and while support for WebP is excellent across modern browsers, it isn't a given across the entire web.

A browser that doesn't support a given encoding won't be able to parse that image file at all. The browser will request the image data, attempt to parse it, and upon failing, will discard it without rendering anything at all.

<br>
