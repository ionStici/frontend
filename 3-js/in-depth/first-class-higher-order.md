[&larr; Back](./README.md)

# First-class / Higher-order

## First-class and Higher-order Functions

JavaScript supports **first-class functions** _(first-class citizens)_, this means that functions are simply values, because functions are just another type of object. Since functions are objects, we can:

- Store functions in variables or properties
- Pass functions as arguments to other functions
- Return functions from functions

And because functions are objects, they also have methods, which we can call on them in different scenarios.

Due to _first-class functions_, we can write **higher-order functions** - a function that **receive** another function as an argument, or that **returns** a new function, or both.

- _First-class functions_ is just a feature that a programming language either has or not, all it means is that all functions are values, it's just a concept (not practice).
- There are _higher-order functions_ in practice, which are possible because the language supports first-class functions.

_Example of function that receives another function:_ `addEventListener` is a higher-order function because it receives another function as an input. We pass in a callback function, which will be called later by the higher-order function when the event happens.

<br>

## Functions accepting callback functions

```js
const average = (...nums) => nums.reduce((a, n) => a + n, 0) / nums.length;

const log = (ave, ...nums) => {
  console.log(`Numbers: ${nums}`); // Numbers: 3,5,7
  console.log(`Average: ${ave(...nums)}`); // Average: 5
  console.log(ave.name); // average
};

log(average, 3, 5, 7);
```

- `average` is a callback function, because we do not call it ourselves, the `log` function will call it.
- `log` is a higher-order function, because it receives `average` as a parameter under the name `ave`

Note that we pass `average` just as a value, we are not calling the function with parenthesis.

The `name` property indicates the function name.

### Another example

```js
const high5 = () => console.log("hi");

document.body.addEventListener("click", high5);

[1, 2, 3].forEach(high5);
```

The `addEventListener` **higher-order** function receives the `high5` **callback** function.

`forEach` as well is a higher-order function which receives callbacks.

### Callbacks

- Makes it easy to split up our code into reusable and interconnected parts.
- Allow us to create abstractions.

**Abstractions** - hide details of some code implementation. This allows us to think about the problem at a more higher abstract level.

_Higher-order functions_ operates at a higher-level of abstraction, leaving the low-level details to the low level functions.

<br>

## Functions Returning Functions

```js
const greet = function (greeting) {
  return function (name) {
    console.log(`${greeting} ${name}`);
  };
};

const greeterHey = greet("Hey");
greterHey("John"); // Hey John

greet("Hello")("John"); // Hello John
```

`greeterHey` is essentially the inner function that `greet()` function returns. The argument we pass in `greeterHey()` is for the function with the `name` parameter.

The `greet()` function returns a new function that we store into `greeterHey` variable, which actually becomes a functions that we can call.

```js
// the same example using arrow functions
const greet = (greeting) => (name) => console.log(`${greeting} ${name}`);
greet("Hi")("John"); // Hi John
```

<br>
