[&larr; Back](./README.md)

# The `this` keyword

The **`this`** keyword is a special variable that is created for every execution context (every function).

- `this` is not static, its value depends on its location and on how the function is called.
- `this` takes the value of the "owner" of the function in which `this` is used.

<br>

_Different Scenarios:_

1. **Method:** `this` === _Object that is calling the method_

   We can access the object itself and its properties from a inner method using the `this` keyword, like: `this.age`

2. **Simple function call:** `this` === `undefined`

   This is only valid in strict mode, in sloppy mode `this` will point to the global `window` object

3. **Arrow functions:** `this` === _the parent's this keyword (lexical this)_

   Arrow functions do not get their own `this` keyword. If you use `this` inside an arrow function, it will point to the parent scope's `this`, usually the `window` object. Don't use arrow functions as methods.

   The arrow function doesn't get its own `this` keyword, nor the `arguments` keyword.

4. **Event Listener:** `this` === _DOM element that the handler function is attached to_

5. **Global Scope:** `this` === _global `window` object_

6. Other Scenarios: `new`, `call`, `apply`, `bind`

<br>
