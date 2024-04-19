# Images

[**Accessibility and Images**](./accessibility.md#images)

- Decorative images that are presentational should be applied with CSS.
- When an image adds context to a document, it is content and should be embedded with HTML.

## The img element

```html
<img src="path/filename" alt="descriptive text" />
```

The `src` attribute is used to reference an image resource.

The `alt` attribute - a short and concise description of the image.

## The figure element

```html
<figure>
  <img src="filename" alt="" />
  <figcaption>Image Caption</figcaption>
</figure>
```

- `<figure>` is a semantic way of referencing images, code snippets, example text.
- `<figcaption>` will link a caption (associated description) for that content.

## picture and source

The `<picture>` element is a container for multiple image options listed in an unlimited number of `<source>` elements and a single required `<img>` element.

The `<source>` attributes include: `srcset`, `sizes`, `media`, `width` and `height`.

`<source>` supports image formats defined in the `type` attribute.

The browser will consider each child `<source>` element and choose the best match among them. If no matches are found, the URL of the `<img>` element's `src` attribute is selected. The accessible name comes from the `alt` attribute of the nested `<img>`.

## Lazy loading

```html
<img src="" alt="" loading="lazy" />
```

By setting `loading="lazy"`, the image loading is deferred until it is likely to come into the viewport, based on the distance the image is from the viewport. This is updated as the user scrolls.

_To improve Largest Contentful Paint (LCP) score:_

- Never specify `loading="lazy"` on top images.
- Use `fetchpriority="high"` to prioritize important images above images elsewhere on the page.

## Aspect Ratio

```html
<img width="70" height="112" />
```

```css
img {
  max-width: 100%;
  height: auto;
  /* aspect-ratio: attr(width) / attr(height); */
}
```

The included unitless `height` and `width` values will be overridden with CSS. These attributes should match the intrinsic size of the image.

The purpose of including these attributes is to reserve the space at the right aspect ratio, improving performance by reducing layout shift.

- [MDN: `attr()` CSS function](https://developer.mozilla.org/en-US/docs/Web/CSS/attr)
- [web.dev: Aspect Radio](https://web.dev/learn/html/images/#aspect-ratio)
- [Height and Width on Images](https://www.smashingmagazine.com/2020/03/setting-height-width-images-important-again/)

## Alternative Solution to Aspect Ratio

```html
<div class="img-container">
  <img class="img" src="" />
</div>
```

```css
.img-container {
  width: 250px;
  height: 300px;
}

.img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```
