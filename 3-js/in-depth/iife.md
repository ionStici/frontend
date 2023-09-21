[&larr; Back](./README.md)

# IIFE

**IIFE** - _Immediately invoked function expression._

A function that executes once, and then never again.

### IIFE Regular functions

```js
(function () {
  console.log("IIFE");
})();
```

We trick JavaScript into considering that this is an expression, by wrapping the anonymous function into parentheses, and then we add `()` to execute the function immediately.

```js
// IIFE Arrow Functions
(() => console.log("IIFE"))();
```

### Why was this pattern invented?

Functions create scopes. Inner scopes would have access to anything defined in the global scope, but the global scope does not have access to any data defined inside of an inner scope (created by a function in our case).

Therefore: **data defined inside a scope is private, or is encapsulated.**

Data encapsulation and data privacy are extremely important concepts in programming. Many times we need to protect our variables from being accidentally overwritten by some other parts of the program, or even with external scripts or libraries.

_It's important to hide variables, and scopes are a good tool for doing this._ This is also the reason why IIFE was invented. IIFE is not really a feature of the JS language, it's more of a pattern that developers came up with, and then started to being used by many other developers.

**Starting with ES6**, variables declared with `let` and `const` creates their own scope inside a block.

```js
{
  const isPrivate = 10;
  var notPrivate = 5;
}

console.log(isPrivate); // Error
console.log(notPrivate); // 5
```

Outside curly braces, `isPrivate` is not accessible.

This is the reason why in modern JavaScript, IIFE is not that used anymore. If all we want is to create a new scope for data privacy, using the pattern above is enough.

On the other hand, if we want a function that will execute only once, then the IIFE pattern is still the way to do.

<br>
