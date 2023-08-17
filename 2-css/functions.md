[&larr; back](./README.md)

# Functions

## Table of Content

- [Introduction](#introduction)
- [attr](#attr)
- [url](#url)
- [calc](#calc)
- [min() and max()](#min-and-max)
- [clamp](#clamp)

<br>

## Introduction

A **function** is a named, self-contained piece of code that completes a specific task.

[**CSS built-in Functions | MDN**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Functions)

**Examples:**

- Functional selectors: `:is()` `:not()`
- `var()` is a function that returns a pre-declared value.
- Color functions: rgb(), rgba(), hsl(), hsla(), hwb(), lab() and lch().

## attr

```css
a::after {
  content: attr(href);
}
```

The `attr()` function will return the value of the attribute that we pass in.

## url

```css
.img {
  background-image: url("/path/image.jpg");
}
```

The `url()` function takes a string URL and is used to load images, fonts and content.

## calc

The `calc()` function takes a single mathematical expression as its parameter. Units can be mixed.

We can nest `calc()` inside another `calc()`, and also we can use `var()` inside `calc()`.

```css
.box {
  width: calc(100% - 2rem);
}
```

## min() and max()

The `min()` and `max()` functions return the samllest or largest computed value of one or more passeed arguments.

```css
.box {
  width: min(20vw, 30rem);
  height: max(20vh, 20rem);
}
```

## clamp

The `clamp()` function takes three arguments: the minimum size, the ideal size and the maximum.

```css
h1 {
  font-size: clamp(2rem, 1rem + 3vw, 3rem);
}
```

In this example, the `font-size` will be fluid based on the width of the viewport.

<br>
