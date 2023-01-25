[&larr; Back](./README.md)

# DOM

**DOM** _(Document Object Model)_ is a structured representation of HTML documents (tree-like structure).

The DOM is implemented by browsers to allow JavaScript to access, modify, and update the structure of HTML web pages. This allows JavaScript to access HTML elements and styles to manipulate them.

We can think of DOM like the connection point between HTML documents and JavaScript code.

The DOM starts with the **document** object, which serves as an entry point into the DOM object.

Then, the first child element of _document_ object is usually the `<html>` element. Next, `<html>` has 2 child elements, `<head>` and `<body>`. Then, the nested html structure goes deeper and deeper.

A **Node** - is an intersecting point in a tree.

So, for each HTML element, there is one node element in the DOM tree, and we can access and interact with each of the nodes using JavaScript.

A DOM tree has more than just element nodes. It also has nodes for all the text itself, attributes, comments and other stuff, because the rule is that whatever is in the HTML document, also has to be in the DOM as a node. So, DOM is a complete representation of of the HTML document, so that we can manipulate it in complex ways.

DOM is automatically created by the browser as soon as the html page loads, and it is stored in a tree structure, where in this tree, each html element is one object.

**DOM manipulation** - the technical term of JavaScript interacting with a webpage.

### DOM hierarchy terminology

- _Parent Node_ - any node that is a direct ancestor of another node.
- _Child Node_ a direct descendant of another node.
- _Sibling Node_ - nodes on the same hierarchical level under the same parent node

### DOM !== JavaScript

DOM is not part of the JavaScript language. DOM and DOM methods are part of web APIs.

<br>

## How the DOM works

DOM is the connection between JS code and HTML documents.

With the DOM API we can: Create, modily, delete html elements & Set styles, classes, attributes & Listen and respond to events.

DOM is a complex API that contains lots of methods and properties for interacting with the DOM tree.

The DOM tree is a tree-like structure made out of nodes and is generated from a HTML document.

### Nodes

Each **Node** is of type node and is represented in JavaScript by an object.

**Node Types:** element type, text type, comment type, document type.

For example, if an element contains text, the text gets its own node of type text.

The same is true for comments, because the rule is that everything inside HTML has to be in the DOM as well.

In JavaScript, each node, or each object, gets access to methods and properties based on its type (element, text, etc.). For example, text nodes will get access to `textContent` property.

The **element type** has internally an HTMLElement child type. This HTMLElement type has one child type for each HTML element that exists in HTML. So we have a HTMLElement type for buttons, images, links, and so on. Each of these HTML elements can have different unique properties. For example, an `img` element has a `src` attribute in HTML which no other element has, or the anchor element with the `href` attribute.

**Inheritance** means that node types will inherit the methods and properties of their parent node types.

The **Document Node Type** contains methods such as `querySelector`, `createElement`, etc.

**EventTarget** node type contains the `addEventListener` method, and this node type also is the parent for the **node type** and for the **window node type**. Therefore, thanks to inheritance, we can call `addEventListener` on every single type of node in the DOM API as if it was their own mehod, because all elements as well as document and window, and even text and comments, will inherit this method. EventTarget object is created automatically behind the scenes to make all the functionality work as expected.
