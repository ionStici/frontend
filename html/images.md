# Images

<br>

## Note

- Decorative images that are presentational should be applied with CSS.
- But when an image adds context to a document, it is content and should be embedded with HTML.

<br>

## Img

```html
<img src="path/filename" alt="descriptive text" />
```

The `src` attribute is used to reference an image resource.

<br>

### alt

- The `alt` attribute (alternative text) brings meaning to images. Define a short and concise description of the image.

- If the image is of SVG file type, include `role="img"`, which is necessary due to VoiceOver bugs.

- When using images for iconography, convey the meaning of the icon. For example, the magnifying glass icon's alt attribute is _search_.

- If the image provides no additional information or is purely decorative, the attribute should still be there, just as an empty string.

- The magazine, being purely decorative, has an empty alt attribute, and a role of none as the image is a purely presentational SVG.

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

`<source>` supports image formats defined in the type attribute.

The browser will consider each child `<source>` element and choose the best match among them. If no matches are found, the URL of the `<img>` element's `src` attribute is selected. The accessible name comes from the `alt` attribute of the nested `<img>`.

<br>

## Lazy loading

```html
<img src="" alt="" loading="lazy" />
```

By setting `loading="lazy"`, the image loading is deferred until it is likely to come into the viewport, based on the distance the image is from the viewport. This is updated as the user scrolls.

<br>
