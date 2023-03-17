[&larr; Back](./README.md)

# Semantic HTML

**Semantic** _relating to meaning_.

**Semantic elements** provide information about the content between the opening and closing tags.

### Why use Semantic HTML?

- **Accessibility:** With Semantic html Screen readers and browsers interpret the code better, making the page accessible for mobile devices and for people with disabilities.
- **SEO:** Semantic html improves website's Search Engine Optimization.
- **Easy to Understand** and read the source code for us and for other web developers.

<br>

## Header and Nav

- `<header>` is an introductory container for navigational links within `<nav>` or introductory content containing `<h1>` to `<h6>` headings.

  When the `header` is top level, it is the site `banner` (landmark role).

  Whne a `header` is nested in `main article section`, it identifies it as the header for that section and isn't a landmark.

- `<nav>` identifies content as navigation.

  If `nav` is nested in the site heading, it is the main navigation.

  if `nav` is nested in an `<article>` or `<section>`, it would be internal navigation for that section only.

<br>

## Key Semantic Elements

- The `<main>` element identifies the main content of the document.

  There should be only one `<main>` per page.

- `<aside>` is for content that is indirectly or tangentially related to the document's main content.

  Usecases: Bibliographies, Endnotes, Comments, Pull quotes, Editorial sidebars, Additional information.

  `<aside>` is a landmark with the implicit role of `complementary`

- `<article>` (nested in main) represents a complete section of content.

  Usecases: articles, blogs, comments, magazines.

- The `<section>` element is used to define generaic standalone sections of a document (no landmark).

  Sections usually should have a heading. `<article>` elements can be separated in sections.

- `<h1>` to `<h6>` six headings, each represents one of the six levels of section headings.

  When a heading is nested in a document banner `<header>`, it is the heading for the whole site.

  When it is nested in the `<main>`, it is the header for that page, not the whole site.

  Headings when nested in an `<article>` or `<section>`, it is the header for that subsection of the page.

  `<h1>` the main heading / `<h2>` as headings for sub-sections / `<h3>` for sections of sub-sections.

- `<figure>` is used to mark up a photo `<img />` and then `<figcaption` to define a caption for the photo.

<br>

## Footer and address

`<footer>` placed at the bottom of the page (landmark), contains information such as: contact info, copyright info, terms of use, site map.

```html
<footer>
  <p>Copyright</p>
  <address>contact information</address>
</footer>
```

Footers are often where you will find contact information, wrapped in an `<address>` element (for contact information).

If `footer` is placed within sections, it will be considered the footer of that section (not landmark).

<br>

## The role attribute

The `role` attribute describes the role an element has in the context of the document.

The role informs the screen reader user how to interact with an interactive element once it has focus.

Interactive elements, such as buttons, links, and checkboxes, all have implicit roles.

With `role='button'` we can turn any element semantically into a button.

We should not use the `role` attribute on semantic elements such as `<button>`. For semantic purposes, we should instead use elements with the default implicit role.

Using too many landmark roles can create "noise" in screen readers, making it difficult to understand the overall layout of the page.

### Role img

```html
<div role="img" aria-label="Img description"></div>
```

- In case we use an element as an image using the CSS `background-image` property, we should define `role="img"` on that element.
- Then, using the `aria-label` attribute, we define a short description of the image, just like the `alt` attribute does.

<br>
