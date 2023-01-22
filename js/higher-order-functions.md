# Higher Order Functions

How to use _abstractions_ by writing functions.

Functions help us make clear, readable programs and reuse code.

Higher-order functions are functions that accept other functions as arguments and/or return functions as output. This enables us to build abstractions on other abstractions.

Using abstraction allows us to write more modular code, which is easier to read and debug.

<br>

## Table of Content

- []()
- []()
- []()

<br>

## Functions as Data

JavaScript functions behave like any other data type in the language. We can assign functions to variables, and we can reassign them to new variables.

```js
const sayHello = function () {
  console.log('Hello');
};

const hello = sayHello;
hello();
```

`hello` is a variable that holds a reference to our original function.

If we could look up the address in memory of `hello` and the address in memory of `sayHello` they would point to the same place.

Our new `hello()` function can be invoked with parentheses as if that was the name we originally gave our function.

We assigned the `sayHello` function without parentheses as the value to the `hello` variable - because we want to assign the value of the function itself, not the value it returns when invoked.

In JavaScript, functions are _first class objects_. This means that, like other objects you’ve encountered, JavaScript functions can have properties and methods.

Since functions are a type of object, they have properties such as `length` and `name`, and methods such as `toString()`.

[More about the methods and properties of functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function)

Functions are special because we can invoke them, but we can still treat them like any other type of data.

<br>

## Functions as Parameters
