[&larr; back](./README.md)

# Functions

## Table of Content

- [Introduction](#introduction)
- [attr](#attr)
- [url](#url)

<br>

## Introduction

A **function** is a named, self-contained piece of code that completes a specific task.

[**CSS built-in Functions | MDN**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Functions)

- Functional selectors: `:is()` `:not()`
- `var()` is a function that returns a pre-declared value.
- Color functions: rgb(), rgba(), hsl(), hsla(), hwb(), lab() and lch().

<br>

## attr

```css
a::after {
  content: attr(href);
}
```

The `attr()` function will return the value of the attribute that we pass in.

<br>

## url

```css
.img {
  background-image: url("/path/image.jpg");
}
```

The `url()` function takes a string URL and is used to load images, fonts and content.

<br>

## calc

<!-- CSS function calc() - in here we can do mathematical operation. We can even mix units.
SASS calc() function - in sass we can’t mix different units as we can in the native CSS calc() function.
We make a Sass variable work in a CSS calc() function by wrapping the value like: #{$color} -->

<br>
