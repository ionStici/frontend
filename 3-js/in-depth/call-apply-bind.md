[&larr; Back](./README.md)

# Set `this` manually

## Table of Content

- [The call() method](#the-call-method)
- [The apply() method](#the-apply-method)
- [The bind() method](#the-bind-method)

<br>

## The call() method

```js
const obj_A = {
  num: 5,
  calc(p) {
    console.log(p + this.num);
  },
};

const obj_B = { num: 10 };

const add = obj_A.calc;

obj_A.calc(5); // 10
add(10); // Error
add.call(obj_A, 10); // 15
add.call(obj_B, 10); // 20
```

The `add` variable is a reference to the `calc` method.

If we try to call `add`, we get an error because the value of `this.num` outside the object is `undefined`, because `this` points to nowhere in the case of `add`.

Using the `call()` method we can manually indicate which object the `this` keyword should address.

The first argument of `call()` is the object the `this` keyword will point to, then the rest of the arguments we need.

Notice that we didn't call the `add` function directly, it doesn't have its own set of parentheses, instead `call()` is the one that will call `add` function with the `this` keyword set explicitly.

`call()` allows us to manually and explicitly set the `this` keyword of any function.

### The apply() method

The `apply()` method works the same as `call()`, the only difference is that after the first argument, `apply()` accepts an array which it will spread automatically.

```js
const arr = [2, 5];
add.apply(obj_A, arr); // 7

add.call(obj_A, ...arr); // | modern JS solution
```

In modern JS, we can use the spread `...` operator together with the `call()` method.

<br>

## The bind() method

`bind()` returns a new function that has the `this` keyword manually set.

```js
const newAdd = add.bind(obj_A);
newAdd(5); // 10
```

Above, `newAdd` is an independent function with `this` set to `obj_A`.

```js
const newAdd = add.bind(obj_A, 10); // predefined arguments
newAdd(); // 15
```

`bind()` allows us to set predefined arguments, the function will always be called with the same arguments.

### Event listeners and object methods

```js
btn.addEventListener("click", obj_A.calc); // NaN
```

The `this` keyword in an event handler always points to the element on which that handler is attached to.

We can manually define the `this` keyword using the `bind()` method:

```js
btn.addEventListener("click", obj_A.calc.bind(obj_A, 5)); // 10
```

`addEventListener()` expects a callback, due to `bind()` returning a function and not calling it, everything works.

### Partial application: Example

**Partial application** refers to the process of fixing a number of arguments to a function, producing another function of smaller arity.

```js
const addTax = (rate, value) => value + value * rate;
addTax(0.1, 200); // 220
```

We want the `rate` parameter to always be `23%`, resulting in a function that only calculates VAT.

```js
const calcVAT = addTax.bind(null, 0.23); // "this" = null
calcVAT(100); // 123
```

This is an example of _partial application_.

```js
// Partial application: function returning function
const addTax = function (rate) {
  return function (value) {
    return value + value * rate;
  };
};

const calcVAT = addTax(0.23);
calcVAT(100);
```

<br>
