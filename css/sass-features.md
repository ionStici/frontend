[&larr; Back](./README.md)

# Sass Features

## Table of Content

- [Sass Variables](#sass-variables)
- [Sass Nesting](#sass-nesting)
- [Sass Mixins](#sass-mixins)
- [Functions](#functions)
- [Extends](#extends)
- [Imports](#imports)

<br>

## Sass Variables

Defining and Using a Sass variable:

```
$color-text: #333;
p { color: $color-text; }
```

<br>

## Sass Nesting

The `&` ampersand symbol in Sass acts as an selector that follow the path from the root until its current location in the nesting system.

```scss
div {
    li {
        &:first-child {..}
        a:link {..}
    }
}
```

In Sass, it is handy to user `&` for pseudo-classes, e.g. `button { &:hover { } }`

After compiling, the code above will result in:

```
div {}
div li {}
div li:first-child {}
div li a:link {}
```

There is no limit how fat we can nest, however you shouldn't go deeper than the third level.

Other useful way of using nesting, is by combining it with the BEM methodology:

```scss
.header {
  &__logo {
  }
}
```

Here, `&` replaces the `header` word and targets the `header__logo` class, allowing us to create self-contained code blocks.

<br>

## Sass Mixins

_Defining and Using a mixin:_

```css
@mixin mixinName($color) {
  color: $color;
}

p {
  @include mixinName(black);
}
```

A **mixin** is a reusable piece of code. We write some code inside a mixin, and then whenever we use that mixin the code we wrote is then replaced in the place where we used (called) the mixin. Like a huge variable with multiple lines of code. Optionally, mixins can accept arguments.

To use the mixin, we call it by the name right after the `@include` keyword.

Whenever we call the mixin in a selector block, the code it contains is used in that location.

<br>

## Functions

_Sass comes in with a couple of built-in functions:_

```scss
color: darken($color, 15%);
color: lighten($color, 15%);
```

_Declaring and Using a Sass function:_

```scss
@function divide($a, $b) {
  @return $a / $b;
}

div {
  margin: divide(60 / 2) * 1px;
}
```

The function returns a value that replaces its name where it was called.

_Note:_ In case we need specific units, the best practice in Sass is to multiply it by `1px`.

<br>

## Extends

We can write a place holder for a selector, with a bunch of styles in a declaration block, and then have other selectors extend (replace) that placeholder. Useful for cases when more style are common to several selectors.

_Write and Use an extend placeholder:_

```scss
%holder {
  color: red;
  margin: 0 auto;
}

a {
  @extend %holder;
}
p {
  @extend %holder;
}
```

_The output in CSS will be:_

```css
a,
p {
  color: red;
  margin: 0 auto;
}
```

Here, the declaration block of the extend was not copied to the selectors, instead, the selector names were replaced with the placeholder name `%holder`

In case of mixins, all the code from a mixin body is copied into the selector.

<br>

## Imports

```scss
@import "base/utilities";
@import "variables";
```

Using the `@import` statement, we can import all the code from a Sass file to another Sass file.

There's no need to use the underscore or the `.scss` extension, the Sass compiler will understand the path.

<br>
