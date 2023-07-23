[&larr; back](./README.md)

# Prescriptive Syntaxes

The `<picture>` element acts as a decision engine for an inner `<img/>` element, telling it what to render from a list of `<source>` elements.

That inner `<img>` also provides you with a reliable fallback pattern for older browsers without support for responsive images.

<br>

## Table of Content

- ["Art directed" images](#art-directed-images)
- [The type attribute](#the-type-attribute)

<br>

## "Art directed" images

Each `<source>` element has attributes defining the conditions for the selection of the image.

```html
<picture>
  <source media="(min-width: 800px)" srcset="lg.jpg 1600w, sm.jpg 1000w" />
  <source srcset="lge.jpg 1200w, sml.jpg 800w" />
  <img src="fallback.jpg" alt="…" sizes="calc(100vw - 2em)" />
</picture>
```

If you're using `min-width` media queries, we must define largest sources first. When using `max-width` media queries, we should put the smallest source first.

When a source is chosen based on the criteria we've specified, the `srcset` attribute is passed along to the `<img` as though it were defined on `<img>` itself - meaning you're free to use sizes to optimize art directed image sources as well.

Recent addition to the HTML: use `height` and `width` attributes on `<source>` elements. These work to reduce layout shifts just as well as they do on `<img>`, with the appropriate space reserved in your layout for whatever `<source>` element is selected.

<br>

## The type attribute

<br>
