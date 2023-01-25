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
