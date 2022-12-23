# **Virtual DOM**

- Resource: [The difference between Virtual DOM and DOM](https://reactkungfu.com/2015/10/the-difference-between-virtual-dom-and-dom/)

<br>

## **Understanding the DOM manipulation problem**

Whenever the browser detects a change to the DOM, it rebuilds the _entire_ DOM only for that change, not considering that most elements were not updated. DOM manipulation is a slower process than most JavaScript operations.

_The problem:_ multiple inefficient DOM updates affecting the website performance.

_The solution:_ Virtual DOM.

<br>

## **The Virtual DOM**

By using a Virtual DOM, we prevent unnecessary DOM rebuilds, and only affect the elements that were updated, greatly improving the webpage performance and creating amazing user experiences.

The Virtual DOM is a JavaScript object that represents a copy of the real DOM object.

In React, for every DOM object, there is a correspodning Virtual DOM object.

Manipulating the virtual DOM is faster, because nothing gets drawn on screen.

Frameworks like Vue or React create their own representation of the DOM as a JavaScript object. Whenever a change is going to be made to the DOM, the framework makes a copy of this JavaScript object, make the change to that copy,and compares the two JavaScript objects, to detects what has changed, and then it informs the browser of these changes and only those parts of the DOM are updated.

Making changes to JavaScript objects and comparing so that only specific parts of the real DOM is updated, is far faster than trying to do the same with common DOM manipulation.

<br>

## **How it Works**

When a JSX element is rendered, every single virtual DOM object gets updated.

Then, React compares the virtual DOM with a virtual DOM snapshot that was taken right before the update.

React figures our exactly which virtual DOM objects have changed (process called "diffing").

Then, React updates only the modified object on the real DOM.

React can update only the necessary parts of the DOM, and improving the performance.

### **Summary**

1. The entire virtual DOM gets updated
2. React figures out which objects have changed by comparing the updated virtual DOM with the pre-updated virtual DOM.
3. Only the changed objects get updated on the real DOM.
4. Changes on the real DOM cause the screen to change.
