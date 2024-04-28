# Functions

A **function** is a named, self-contained piece of code that completes a specific task.

We call a function by its name, and pass arguments into its parenthesis.

Functions can be nested within each other in some contexts, giving more flexibility.

Functions that return a value (e.g. `attr()`): you pass one or more arguments, and use them on the right side of the CSS declaration.

Functional selectors: `:is()` `:not()` into these functions we pass CSS selectors, and if there is a match, the CSS rule will apply to them.

Other examples of CSS functions: `var()` `minmax()` `fit-content()` `rgb()` `clamp()`

- The `attr(href)` function is returning the value of the attribute we pass in.

- The `url()` function takes a string URL and is used to load images, fonts, content.

- Color functions: `rgb()` `hsl()` `hwb()` `lab()` `lch()`

- The `calc()` function for calculations, you ca mix units and nest calc inside another calc.

- The `min()` and `max()` functions returns the smallest or largest computed value of the one or more passed arguments.

- Shapes properties: `clip-path` `offset-path` `shape-outside`. Shape functions: `circle()` `ellipse()` `inset()` `polygon()`

- Other functions: `transform` functions, animate, gradients, filters.
