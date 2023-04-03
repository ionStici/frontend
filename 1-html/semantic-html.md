[&larr; Back](./README.md)

# Semantic HTML

**Semantic elements** = elements with a meaning.

**Non-semantic** elements: `<div>` and `<span>` - tells nothing about its content.

_Why Semantic elements?_ Accessibility + SEO + Easy to read the source code.

<br>

## Key Semantic Elements

- **`<header>`** is an introductory container.

  - It should contain introductory content `<h1>`, or navigational links `<nav>`.
  - If `header` is top level, it is the site `banner` (landmark role).
  - If `header` is nested within another section, it is identified as the header for that section (no landmark).

<br>

- **`<nav>`** identifies content as navigation.

  - If `nav` is nested in the site header, it is the main navigation.
  - If `nav` is nested within an `<article>` or `<section>`, it will be the internal navigation for that section only.

<br>

- **`<main>`** for the main content of the document.

  - There should be only one `<main>` per page (landmark).

<br>

- **`<aside>`** is for content that is indirectly related to the document's main content.

  - `aside` is a landmark with the implicit role of `complementary`. Used for additional information.

<br>

- **`<article>`** (nested in main) represents a complete section of content.

  - _Usecases:_ articles, blogs, comments, magazines.

<br>

- **`<section>`** is used to define a standalone section of the document (no landmark).

  - Sections usually should have a heading. `article` elements can be separated in sections.

<br>

- **`<h1>`** to **`<h6>`** six heading levels.

  - When a heading is nested in a document banner `header`, it is the heading for the whole website.
  - When it is nested in the `main` container, it is the heading for that page, not the whole site.
  - When nested in an `article` or `section`, it is the heading for that sub-section of the page.
  - `h1` the main heading / `h2` as headings for sub-sections / `h3` for sections of sub-sections.

<br>

- **`<footer>`** placed at the bottom of the page (landmark), contains information such as: contact info wrapped in an `<address>` element, copyright info, terms of use, site map.

  - If `footer` is placed within another section, it will be considered the footer of that section (not landmark).

<br>

## The role attribute

The **`role`** attribute provide semantic meaning to elements and their content.

It informs the screen reader user how to interact with an interactive element once it has focus.

Interactive elements, such as buttons, links, and checkboxes, all have implicit roles.

With `role='button'` we can turn any element semantically into a button.

We should not use the `role` attribute on semantic elements such as `<button>`

Using too many landmark roles can create "noise" in screen readers, making it difficult to understand the overall layout of the page.

<br>

### Role Img

```html
<div role="img" aria-label="Img description"></div>
```

In case we use an element as an image using the CSS `background-image` property, we should define `role="img"` on that element.

Then, using the `aria-label` attribute, we define a short description of the image, just like the `alt` attribute does.

<br>
