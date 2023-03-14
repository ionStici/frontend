[&larr; Back](./README.md)

# HTML

**HTML** stands for _HyperText Markup Language_, and it is the code that structure the webpage and embed content.

- A _markup_ language is a computer language that defines the structure and presentation of raw text.
- _HyperText_ is text displayed on a computer that provides access to other text through links.

<br>

## Table of Content

- [HTML Elements Anatomy](#html-elements-anatomy)
- [HTML Concepts](#html-concepts)
- [Entity References](#entity-references)
- [Attributes](#attributes)
- [Anchor Element](#anchor-element)
- [Lists](#lists)

<br>

## HTML Elements Anatomy

HTML consists of elements. They define the content and structure of the webpage.

```HTML
<p> hi </p>  <!-- a html element -->
```

HTML element: `<p>` opening tag + `hi` content + `</p>` closing tag

<br>

## HTML Concepts

- _Nesting Elements_: Elements placed within other elements.

- _Hierarchy_: _Child_ elements are nested inside _Parent_ elements (the relationship between elements).

- We use indentation and white space to structure the code for better readability.

- White space in HTML is reduced to a single space when the code is rendered.

- `<!-- a html comment -->` Comment syntax in HTML. The browser will ingnore this syntax.

- _Self Closing Tags_: Elements composed of a single tag, usually used to embed something.

- Only the content inside the `body` tags will be displayed on the page.

- _Headings_: There are six heading levels in HTML `<h1></h1>`.

- `<div>` (division): the most popular html element used to divide the page into sections.

- `<p>` (Paragraph) contain a block of plain text.

- `<span>` contain short pieces of content, used to separate small pieces of content.

- `<em>` emphasizes text (style as _italic_). `<strong>` highlights important text (style as **bold**) - semantic.

- `<br />` tag creates line breaks.

- Embed images with `<img src="img.jpg" />` tag. Inside `src` attribute we indicate the img path.

- `alt` attribute (alternative text) brings meaning to images - define a short description of the image.

<br>

## Entity References

HTML special characters: `<` `>` `"` `'` `&`

They are parts of the HTML syntax.

To include a special character in our text we use a character reference.

These are special codes that represent characters, example: `<` equal to `&lt;`

Each character reference starts with an ampersand `&` and ends with a semicolon `;`

[Character References List](https://html.spec.whatwg.org/multipage/named-characters.html)

<details>
<summary>Entity Examples</summary>

| Literal character | Character reference equivalent |
| :---------------: | :----------------------------: |
|         <         |             `&lt;`             |
|         >         |             `&gt;`             |
|         "         |            `&quot;`            |
|         '         |            `&apos;`            |
|         &         |            `&amp;`             |

</details>

<br>

## Attributes

HTML Elements can have attributes.

```html
<p class="text" open="open" open>Paragraph</p>
```

Attributes anatomy:

1. The attribute name, followed by an equal sign.
2. The attribute value, wrapped in single or double quote marks.

Attributes contain extra information about the element. It will not appear on the page.

_Boolean attributes_ can only have one value which is generally the same as the attribute name.

We can set boolean attribute equal to itself, or leave just the name - both acceptable.

<br>

## Anchor Element

Linking to other web pages.

```html
<a target="_blank" href="https://www.google.com/">Google</a>
```

- `href` attribute stands for _hyperlink reference_. Creates a hyperlink to the indicated destination as value.
- `target` attribute specifies how a link should open. `_blank` value will open the link in a new tab.

We can link to a web page, a relative path, a file, email address, anything else a URL can address.

`href="#footer"` using IDs as href value we can jump to certain sections when clicking on links.

We can turn nearly any element (like img) into a link by wrapping that element with an anchor element.

<br>

## Lists

Creating a list of items:

```html
<ul>
  <li>Hello</li>
  <li>World</li>
</ul>
```

Each list item must be wrapper in `<li>` (list) tags.

- `<ul>` for unordered lists.
- `<ol>` for ordered lists.

<br>
