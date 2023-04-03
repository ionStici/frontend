[&larr; Back](./README.md)

# Images

- Decorative images that are presentational should be applied with CSS.
- But when an image adds context to a document, it is content and should be embedded with HTML.

<br>

## Table of Content

- [Img](#img)
- [Figure](#figure)
- [picture and source](#picture-and-source)

<br>

## Img

```html
<img src="path/filename" alt="descriptive text" />
```

The `src` attribute is used to reference an image resource.

### alt

- The `alt` attribute (alternative text) brings meaning to images. Define a short and concise description of the image.
- If the image is of SVG file type, include `role="img"`, which is necessary due to VoiceOver bugs.
- When using images for iconography, convey the meaning of the icon. E.g. the magnifying glass icon's `alt` attribute is _search_.
- If the image doesn't provide additional information and is purely decorative, the `alt` attribute should be an empty string and the `role` equal to `none`.

<br>

## figure

```html
<figure>
  <img src="filename" alt="" />
  <figcaption>Image Caption</figcaption>
</figure>
```

- `<figure>` is a semantic way of referencing images, code snippets, example text.
- Then `<figcaption>` will link a caption (associated description) for that content.
- When including a `<figcaption>` make sure it is the first or last child nested within the `<figure>`.

<br>

## picture and source

The `<picture>` element is a container for multiple image options listed in an unlimited number of `<source>` elements and a single required `<img>` element.

The `<source>` attributes include: `srcset`, `sizes`, `media`, `width` and `height`.

`<source>` supports image formats defined in the `type` attribute.

The browser will consider each child `<source>` element and choose the best match among them. If no matches are found, the URL of the `<img>` element's `src` attribute is selected. The accessible name comes from the `alt` attribute of the nested `<img>`.

<br>

## Lazy loading

```html
<img src="" alt="" loading="lazy" />
```

By setting `loading="lazy"`, the image loading is deferred until it is likely to come into the viewport, based on the distance the image is from the viewport. This is updated as the user scrolls.

<br>

## Aspect Ratio

```html
<img width="70" height="112" />
```

```css
img {
  max-width: 100%;
  height: auto;
  aspect-ratio: attr(width) / attr(height);
}
```

The included unitless `height` and `width` values will be overridden with CSS.

The purpose of including these attributes is to reserve the space at the right aspect ratio, improving performance by reducing layout shift.

- [MDN: `attr()` CSS function](https://developer.mozilla.org/en-US/docs/Web/CSS/attr)
- [web.dev: Aspect Radio](https://web.dev/learn/html/images/#aspect-ratio)
- [Height and Width on Images](https://www.smashingmagazine.com/2020/03/setting-height-width-images-important-again/)

<br>