[&larr; back](./README.md)

# Media Queries in Sass

## Table of Content

- [Media Queries and Sass](#media-queries-and-sass)
- [Media queries and Mixins](#media-queries-and-mixins)
- [Mixins with Arguments](#mixins-with-arguments)
- [Media queries with Sass Variables](#media-queries-with-sass-variables)

<br>

## Media Queries and Sass

```css
.html {
  font-size: 62.5%;

  @media only screen and (min-width: 48em) {
    font-size: 9px;
  }
}
```

In Sass, we can add media queries inside CSS declaration blocks, and then write just the styles in that media query.

This will then be compiled as the traditional way of using media queries in CSS.

<br>

## Media queries and Mixins

```css
@mixin width-600 {
  @media only screen and (max-width: 37.5em) {
    @content;
  }
}

html {
  font-size: 62.5%;

  @include width-600 {
    font-size: 9px;
  }
}
```

We can write a mixin which will insert the media query syntax for us.

`@content` directive allows us to pass a block of code into a mixin.

The code we pass into the mixin will be replaced instead of `@content`.

<br>

## Mixins with Arguments

```
@mixin width($breakpoint) {
    @if $breakpoint === 600 { @media (min-width: 37.5em) { @content } }
    @if $breakpoint === 768 { @media (min-width: 48em) { @content } }
}

html { @include width(600) { font-size: 9px; } }
```

- If `@breakpoint` argument is `600`, then use this media query `(min-width: 37.5em)`.
- `@if` sass directive makes a test, and if the result if true then something happens.

<br>

## Media queries with Sass Variables

Store breakpoint as Sass variables:

```css
@bp-1200: 75em;
```

Then use the Sass variable in your media query:

```css
.header {
  @media only screen and (min-width: $bp-1200);
}
```
