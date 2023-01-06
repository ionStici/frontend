[&larr; Back](./README.md)

# CSS

**CSS** stands for Cascading Style Sheets. Definition:

- is a style sheet language;
- the code that styles web content;
- selectively style HTML elements.

<br>

## Table of Content

- [Anatomy of a CSS syntax](#anatomy-of-a-css-syntax)
- [CSS Types](#css-types)
- [Aspects to keep in mind](#aspects-to-keep-in-mind)

<br>

## Anatomy of a CSS syntax

```CSS
span {
    color: red;
}
```

The whole syntax is called a **CSS ruleset**.

- `span` Selector
- `{ color: red; }` Declaration block
- `color: red;` Declaration
- `color` Property
- `red` Value
- `/*  */` CSS comment syntax

<br>

## CSS Types

### Inline CSS

```html
<h1 style="color: red;">Hello</h1>
```

CSS declarations in the `style` attribute of HTML elements.

### Internal / Embedded CSS

```html
<style>
  h1 {
    style: red;
  }
</style>
```

CSS ruelsets inside `<style>` and `<head>` tags.

### External CSS

```html
<link rel="stylesheet" href="style.css" />
```

CSS code inside an external `style.css` file.

Link the css file with the html document via the tag above.

### CSS Types Priority

(1) Inline CSS -> (2) -> Internal CSS -> (3) External CSS

<br>

## Aspects to keep in mind

<br>

### Responsive Design

- Fluid layouts
- Media queries
- Responsive images
- Correct units
- Desktop-first vs Mobile-first

<br>

### Maintainable and scalable code

- Clean
- Easy to understand
- Growth
- Reusable
- How to organize files
- How to name classes
- How to structure HTML

<br>

### Web performance

- Less HTTP requests
- Less code
- Compress code
- Use a CSS preprocessor
- Less images
- Compress images

<br>
