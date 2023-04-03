# HTML APIs

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

## The node interface

Every type of DOM node is represented by an interface based on [Node](https://developer.mozilla.org/en-US/docs/Web/API/Node), which provides information and methods as elements relate to the DOM tree. The Node interface enables querying and adding nodes to the node tree.

<br>

## Document and HTML Document interfaces

The [`Document`](https://developer.mozilla.org/en-US/docs/Web/API/Document) interface inherits from `Node` and `HTMLDocument` interfaces.

`Document` represents the web page loaded in the browser.

- The `document` enables quick access to node types and the ability to create collections of specific element types, such as `document.body` and `document.styleSheets`.

- The `HTMLDocument` enables accessing information relevant to the document that are not found in HTML nodes, such as the `Document.location`, `Document.lastModified`, and `Document.Cookie`.

Several APIs are available based on features surfaced through the document interface, including the [Drag and Drop API](https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API) and the [FullScreen API](https://developer.mozilla.org/en-US/docs/Web/API/Fullscreen_API). Both inherit from `Element`.

<br>

## The Window interface

The Window interface includes globally available items beyond the DOM that can be used to manipulate the DOM. Window provides functions, namespaces, objects, and constructors documented in MDN's [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) and [DOM References](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model).

The Window interface is the API for the object containing the document. The global window object is the window in which the script is running. Every browser tab contains its own Window object. The Window interface can query the contents of the tab as well as the overall window and device.

<br>
