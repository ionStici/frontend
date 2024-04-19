# HTML

**HTML** stands for _HyperText Markup Language_, and it is the code that structure the webpage and embed content.

- A _markup_ language is a computer language that defines the structure and presentation of raw text.
- _HyperText_ is text displayed on a computer that provides access to other text through links.

## HTML Element Anatomy

HTML consists of elements. They define the content and structure of the webpage.

```HTML
<p> hi </p>  <!-- html element -->
```

`<p>` opening tag + `hi` content + `</p>` closing tag

## HTML General Concepts

- HTML is not case-sensitive, but for consistency use only lowercase letters.
- _Nesting Elements_: Elements placed within other elements.
- _Hierarchy_: _Child_ elements are nested inside _Parent_ elements (the relationship between elements).
- We use indentation and white space to structure the code for better readability.
- White space in HTML is reduced to a single space when the code is rendered.
- `<!-- a html comment -->` Comment syntax in HTML. The browser will ignore this syntax.
- _Self Closing Tags_: (Void) Elements composed of a single tag, usually used to embed something.
- _Non-replaced_ elements: are common elements that usually embed text into the document.
- _Replaced_ elements are replaced by objects, e.g. input elements embed graphical user interface widgets.
- Only the content inside the `<body>` tags of the HTML document will be displayed on the page.
- `<div>` (division) is the most popular html element used to divide the page into sections.
- `<br/>` creates line breaks. `<hr/>` creates a thematic break ("separator" semantic meaning).

## Attributes

**Attributes** provide extra information about and functionality for the element.

```html
<p class="text" id="unique" contenteditable>Hello</p>
```

**Attributes anatomy:**

1. The attribute name followed by an equal sign.
2. The attribute value wrapped in single or double quote marks.

<div></div>

**Characteristics:**

- **Global attributes** can be set on any HTML element.
- Examples: `id class style` - [List of global attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes).

<div></div>

- If a **Boolean attribute** is present, it is always true, otherwise it's not, e.g. `checked`
- Boolean values can either be omitted, empty string, or equal to the name of the attribute.

<div></div>

- **Enumerated attributes** have a default value if the attribute is present but the value is missing.
- The default value depends on the attribute. Attributes aren't automatically "true" if present.

<div></div>

- Attribute values that are part of the HTML specification are _case-insensitive_.
- Attribute values that we define, such as classes, are _case-sensitive_.

<div></div>

- **`data-*="12"`** custom attributes.
- _Custom properties_ are an excellent way of communicating application-specific information via JavaScript.

## Entity References

- Certain characters are part of the HTML syntax `< > " ' &` (reserved characters).
- To include a reserved character in our text we use a [character reference](https://html.spec.whatwg.org/multipage/named-characters.html).
- These are special codes that represent characters, e.g. `&lt;` will evaluate to `<`
- Each character reference begins with an ampersand `&` and ends with a semicolon `;`

## Anchor Elements

Links represent a connection between two resources, one of which is the current document.

```html
<a href="/" target="_blank" href="/file.jpg" download>Google</a>
```

- `href` attribute stands for _hyperlink reference_. It creates a hyperlink to the indicated destination as value.
- `target` attribute specifies how a link should open. `_blank` value will open the link in a new tab.

We can link to a web page, a relative path, a file, email address, anything else a URL can address.

`href="#footer"` using IDs as href values we can jump to certain sections when clicking on links.

We can turn nearly any element (like img) into a link by wrapping that element with an anchor element.

The `download` attribute specifies that the target file from `href` will be downloaded.

## Lists

Creating a list of items:

```html
<ul>
  <li>1</li>
  <li>2</li>
</ul>
```

Each list item must be wrapper in `<li>` (list) tags.

- `<ul>` for unordered lists.
- `<ol>` for ordered lists.

## Description Lists

Description list -> description term -> description definition.

```html
<dl>
  <dt>hi</dt>
  <dd>A friendly, informal, casual greeting said when meeting someone.</dd>
</dl>
```
