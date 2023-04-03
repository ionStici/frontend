[&larr; Back](./README.md)

# CSS

**CSS** stands for Cascading Style Sheets. It is a style sheet language used to selectively style web content.

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

## How CSS works behind the scenes

As the browser parses the HTML, it finds / loads, and starts parsing the stylesheet included in the HTML head.

_Two main steps during the CSS parsing phase:_

1. Conflicing CSS declarations are resolved through a process knows as **cascade**.
2. Processing final CSS values (converting relative units to pixels).

The final CSS is stored in a tree-like structure, called: **CSS Object Model**. Now, the parsed HTML and CSS files form the so-called **Render Tree**.

Now, the parsed and stored HTML document and CSS file, these together form the so-called Render tree - with that, we finally have everything we need to render the page.
