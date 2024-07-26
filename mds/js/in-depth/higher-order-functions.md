[&larr; Back](./README.md)

# Higher Order Functions

Higher-order functions are functions that accept other functions as arguments and/or return functions as output. This enables us to build abstractions on other abstractions.

## Table of Contents

- [Functions as Data](#functions-as-data)
- [Functions as Parameters](#functions-as-parameters)
- [Review](#review)

<br>

## Functions as Data

JavaScript functions behave like any other data type in the language. We can assign functions to variables, and we can reassign them to new variables.

```js
const sayHello = function () {
  console.log("Hello");
};

const hello = sayHello;
hello();
```

`hello` is a variable that holds a reference to our original function.

If we could look up the address in memory of `hello` and the address in memory of `sayHello` they would point to the same place.

Our new `hello()` function can be invoked with parentheses as if that was the name we originally gave our function.

We assigned the `sayHello` function without parentheses as the value to the `hello` variable - because we want to assign the value of the function itself, not the value it returns when invoked.

In JavaScript, functions are _first class objects_. This means that, like other objects you’ve encountered, JavaScript functions can have properties and methods.

Since functions are a type of object, they have properties such as `length` and `name`, and methods such as `toString()`

[More about the methods and properties of functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function)

Functions are special because we can invoke them, but we can still treat them like any other type of data.

<br>

## Functions as Parameters

A parameter is a placeholder for the data that gets passed into a function.

Since functions can behave like any other data type, functions can accept other functions as parameters.

A _higher-order function_ is a function that either accepts functions as parameters, returns a function, or both.

Functions passed in as a parameter are called **callback functions**.

Callback functions get invoked during the execution of the higher-order function.

When we invoke a higher-order function, and pass another function in as an argument, we don't invoke the argument function. Invoking it would evaluated to passing in the return value of that function call. With callback functions, we pass in the function itself by typing the function name without the parentheses.

```js
const higherOrderFunction = (callback) => callback();
const hello = () => console.log("Hello");
higherOrderFunction(hello);
higherOrderFunction(() => "hello"); // passing in an anonymous function
```

We can even pass in as argument anonymous functions.

<br>

## Review

- Abstraction allows us to write complicated code in a way that’s easy to reuse, debug, and understand for human readers.
- We can work with functions the same way we work with any other type of data, including reassigning them to new variables.
- JavaScript functions are first-class objects, so they have properties and methods like any other object.
- Functions can be passed into other functions as parameters.
- A higher-order function is a function that either accepts functions as parameters, returns a function, or both.

<br>
