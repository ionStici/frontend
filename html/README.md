# HTML

## Table of Content

[**&larr; Back to the Main Page**](./../README.md)

<div></div>

- [HTML Basics](./html-basics.md)
- [HTML document](./html-document.md)
- [Metadata](./metadata.md)
- [Semantic HTML](./semantic-html.md)
- [Attributes](./attributes.md)
- [Forms](./forms.md)
- [Images](./images.md)
- [Audio and Video](./audio-video.md)

<br>

## HTML APIs

- The DOM (Document Object Model) is an API for accessing and manipulating documents.
- The DOM is the tree of all the nodes in the document (this includes elements, attributes, text nodes).

<br>

- The AOM (Accessibility Object Model) is based off the DOM.
- Similarly, the AOM tree contains objects representing all the markup elements, attributes, and text nodes.

<br>
<hr>

Every node in the document tree is an object that can be manipulated with JavaScript.

With HTML interface APIs we can access all the information that an HTML element holds.

Most HTML elements have an associated DOM interface.

The base interface for all elements is aptly named [`Element`](https://developer.mozilla.org/en-US/docs/Web/API/Element).

Then, the [`HTMLElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement) inherits from Element and all HTML element-specific interfaces inherit from it.

Element-specific interface example: `HTMLAnchorElement` - `<a>`

[List of element-specific interfaces.](https://web.dev/learn/html/apis/#available-element-interfaces)

The naming convention is "HTML" followed by an element name, followed by "Element".

Over 30 elements don't have an associated DOM interface other than `HTMLElement`.

<br>
<hr>

For collection of elements, there are also come collection interfaces.

[`HTMLCollection.namedItem()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection/namedItem) method returns the first element in the collection whose `id` or `name` attribute matches the parameter, or null if no element matches.

<br>
<hr>
