[&larr; Back](./README.md)

# The Module Pattern

```js
const buy = (function () {
  const cart = [];
  const product = "MacBook";
  const price = 10;

  const addToCart = (product, quantity, price) => {
    cart.push({ product, quantity, price });
  };

  return { cart, product, price, addToCart };
})();

buy.addToCart(buy.product, 3, buy.price);
console.log(buy.cart);
// [{ product: "MacBook", quantity: 3, price: 30 }];
```

**Module Pattern Goal:** encapsulate functionality, private data, expose a public API.

**To make a public API**, we return an object which contains the methods and properties we want to be available, and assign a variable to IIFE that will become the returned object.

**The Module Pattern** - Now, the `buy` object is like a module, the properties we didn't export are not accessible, they are private to the function.

In case you are wondering how this works, considering that the function has returned and then we are able to use properties and methods from inside of it, the answer is **Closures**.

Closures: the IIFE `buy` function is the birthplace of `addToCart`. This birthplace includes all of the IIFE scope, the `cart` as well.

<!-- This pattern was used for a long time by developers, long before ES6 modules even existed in JS. The problem is, if we wanted one module per file, like we have with ES6 modules, then we would have to create different scripts and link all of them in the HTML file. And that creates a couple of problems, like we have to be careful with the order in which we declare them in html, and we would have all of the variables living in the global scope, and we also couldn’t bundle them together using a module bundler. Using a module bundler is very important in modern JS. So the module pattern that we just learned about, does indeed work quite good, but it has some limitations. That’s the reason why native modules were added to the language in ES6. -->

<br>
