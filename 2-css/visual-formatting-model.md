[&larr; Back](./README.md)

# The Visual Formatting Model

**The Visual Formatting Model** is an algorithm that determines the overall layout by calculating the dimensions of each element in the render tree.

The algorithm takes in account:

- Box dimensions (the box model) and Box types (set by `display`)
- Positioning scheme (normal flow, float, absolute positioning)
- Stacking Contexts and Other elements present in the document tree
- External information such as viewport size, intrinsic dimensions of images, etc.

All these concepts together determine how the website will look in the browser.
