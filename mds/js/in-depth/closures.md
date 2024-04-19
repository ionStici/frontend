[&larr; Back](./README.md)

# Closures

```js
const add = function () {
  let num = 0;

  return function () {
    num++;
    console.log(num);
  };
};

const count = add();

count(); // 1
count(); // 2
count(); // 3
```

The `add` function ran, returned another function, then finished executing, so the execution context of `add` is no longer on the stack. How can the `count` function access and update the `num` variable that comes from an inactive execution context?

**Closure** - preserve variables from the outer scope of a function in the inner scope of a function.

_A function has access to the variable environment of the execution context in which it was created._

In our code example, the `count` function was created in the execution context of the `add` function, so `count` will get access to the variable environment containing the `num` variable. It's this connection that we call **closure**.

When a function attempts to access a variable that is not in the current scope, JavaScript will immediately look into the closure to see if it can find the variable there. It does this even before looking at the scope chain. So the closure has priority over the scope chain.

```js
console.dir(count); // 0: Closure (add) {num: 3}
```

Using `console.dir` method, we can take a look at the scope's internal properties.

A closure gives a function access to all the variables of its parent function, even after that parent function has returned. The function keeps a reference to its outer scope, which preserves the scope chain throughout time.

Note: We do NOT have to manually create closures, this is a JavaScript feature that happens automatically. We can't even access closed-over variables explicitly. a closure is NOT a tangible JavaScript object.

<br>

### Another Closure example

```js
let f;

const g = function () {
  const a = 22.5;
  f = () => console.log(a * 2);
};

g();
f(); // 45
```

- The `g` function assigned a function to the `f` variable.
- The `f` function accessed the `a` variable located in the `g` function that already executed.

### Example using a timer

```js
const multiply = (x) => {
  const y = 3;
  let result = x * y;

  setTimeout(() => {
    console.log(`${x} * ${y} = ${result}`);
  }, 1000);
};

multiply(7); // 21
```

<br>
