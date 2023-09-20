[&larr; Back](./README.md)

# How argument passing works

_How primitives and objects work in the context of functions._

```js
const sayHello = "Hello";
const user = { name: "John" };

const welcome = function (p1, p2) {
  p1 = `Welcome, ${p2.name}`;
  p2.name = "Mr. " + p2.name;
  console.log(p1); // Welcome, John
};

welcome(sayHello, user);

console.log(sayHello); // Hello
console.log(user.name); // Mr. John
```

### Primitive types

We passed `sayHello` variable into the function as argument under the parameter `p1`

Inside the function body, `p1` is a regular variable, completely different from `sayHello`

This would be like writing: `const p1 = sayHello`, in other words, `p1` becomes a copy of the original value.

That's why if we change `p1` in the function, it will not affect the outside `sayHello` variable.

### Reference types

We passed `user` object into the function as argument under the parameter `p2`

Then we updated the `p2` object inside the function body, which in turn affected the `user` object too.

When we pass a reference type to a function, it is copied only the reference address to that object in the memory heap, exactly like: `const p2 = user`

Again, we copy only the reference address to the object in the memory heap, and this address points to the same object in memory. That's why when we manipulate the `p2` object, it is exactly the same as manipulating the `user` object, because they are both the same object in the memory heap.

### Summary

- Passing a primitive type to a function results in creating a copy.
- When we pass an object to a function, it results in creating a new identifier pointing to the same object in the memory heap.

_Note:_ JavaScript does not have passing by reference, only passing by value.

<br>
