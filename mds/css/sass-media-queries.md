# Media Queries and Sass

```scss
.html {
  font-size: 62.5%;

  @media only screen and (min-width: 48em) {
    font-size: 50%;
  }
}
```

In Sass, we can nest media queries into CSS declaration blocks resulting in more modular code blocks.

This will then be compiled as the traditional way of using media queries in CSS.

## Media queries and Mixins

```scss
@mixin width-600 {
  @media only screen and (max-width: 37.5em) {
    @content;
  }
}

html {
  font-size: 62.5%;

  @include width-600 {
    font-size: 50%;
  }
}
```

We can write a mixin which will insert the media query syntax for us.

`@content` directive allows us to pass a block of code into a mixin.

The code we pass into the mixin will be replaced instead of `@content`.

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
