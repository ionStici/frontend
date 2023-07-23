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

The `type` attribute allows you to use the `<picture>` element's single-request decision engine to only serve image formats to browsers that support them.

```html
<picture>
  <source type="image/webp" srcset="pic.webp" />
  <img src="pic.jpg" alt="..." />
</picture>
```

In the `type` attribute, you provide the [Media Type (formerly MIME type)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) of the image source specified in the `srcset` attribute of each `<source>`. This provides the browser with all the information it needs to immediately determine whether the image candidate provided by that `source` can be decoded without making any external requests—if the media type isn't recognized, the `<source>` and all its candidates are disregarded, and the browser moves on.

<br>

## Automating compression and encoding

When choosing encodings for a directory of photographic images, AVIF is the clear winner for quality and transfer size but has limited support, WebP provides an optimized, modern fallback, and JPEG is the most reliable default.

<br>

## Local development tools and workflows

Task-runners and bundlers like Grunt, Gulp, or Webpack can be used to optimize image assets alongside other common performance-related tasks, such as minification of CSS and JavaScript.

<br>

## Other Resources

- [Responsive image markup in practice](https://web.dev/learn/images/automating/#responsive-image-markup-in-practice)
- [Site Generators, frameworks, and CMSs](https://web.dev/learn/images/cms/)
- [Image content delivery networks](https://web.dev/learn/images/cdn/)

<br>
