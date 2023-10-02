[&larr; Back](./README.md)

# JSDoc

[**JSDoc**](https://jsdoc.app/) - standard technique of writing documentation for JS functions.

- Write Code documentation - make the code easy to understand.

- JSDoc documentaion syntax - multiline comment with 2 asterisks at the beginning.

- Place the JSDoc comment block above the function you want to document.

```js
/**
 * Render the received object to the DOM
 * @param {Object | Object[]} data The data to be rendered (e.g. recipe)
 * @param {boolean} [render=true] If false, create markup string instead of rendering to the DOM
 * @returns {undefined | string} A markup string is returned if render=false
 * @this {Object} View instance
 * @author Jonas Schmedtmann
 * @todo Finish implementation
 */
render (data, render = true) {}
```

- Start with a quick description.

- `@param` describe the function's parameters.

- `@returns` what the function returns. If nothing then specify "undefined"

- `@this` what the "this" keyword is in the context to this function.

- `@todo` indicate what the function needs to be completed.

<br>
