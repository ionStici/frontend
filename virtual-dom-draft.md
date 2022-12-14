## **Virtual DOM**

DOM is a representation of a webpage created by and stored in the users browsers. The browsers takes the site's HTML, transforms it into a DOM and then paints the DOM to the users screen making the site visible to the user. DOM is a tree of nodes representing a webpage.

Whenever the browser detects a change to the DOM, it repreints the entire page using the new version of the DOM. But do we really need to change the whole page? Why not only an element?

For DOM to determine what parts have changed is time-consuming. It is faster for browsers to repaint the entire page whenever the user is interacting with the site instead of determining what if anything has changed.

There is a faster way to make this comparisons.

**Virtual DOM**

Frameworks like Vue or React create their own representation of the DOM as a JS object. Whenever a change is going to be made to the DOM, the framework makes a copy of this JS object, make the change to that copy, and compares the two JS objects, to see what has changed, then it informs the browser of these changes and only those parts of the DOM are repainted.

Making changes to JS objects and comparing them is far faster than trying to do the same with DOMs.

Using JS objects can quickly determine what to repaint in a way that we couldn't by just relying on the browser.

Since this DOM is stored in memory as a JS object, it is called a Virtual DOM.

Using a Virtual DOM, allows:

1. Prevents unnecessary repaints
2. Only repaints updated elements
3. Groups together repaints

So that one user interaction doesn't required the entire page to be repainted multiple times.

Repainting a page takes time, and modern web apps constantly have tons of small changes. Attemptign to repaint the whole page for each one makes sites slow and buggy, using a virtual DOM allows us to only repaint what is necessary. Greatly improving page performance and creating even more amazing user experiences.
