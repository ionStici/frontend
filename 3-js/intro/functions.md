[&larr; Back](./README.md)

# Functions

A **function** is a reusable block of code that groups together a sequence of statements to perform a specific task.

<br>

## Table of Content

- [Function Declaration](#function-declaration)
- [Parameters and Arguments](#parameters-and-arguments)
- [Default Parameters](#default-parameters)
- [Return](#return)
- [Helper Functions](#helper-functions)
- [Function Expression](#function-expression)
- [Arrow function](#arrow-function)
- [Reviewing functions](#reviewing-functions)

<br>

## Function Declaration

We bind a function to an identifier name.

```js
greet("World"); // calling the function before it is defined

function greet() {
  console.log(`Hello`);
}
```

A function declaration consists of:

- `function` keyword
- The name of the function followed by parentheses `()`
- The function body enclosed in curly braces `{}`, where the code is executed

Calling the function:

- The code inside a function body runs (executes), ONLY when the function is called.
- To call a function, type the function name followed by parentheses `greet();`
- This _function call_ executes the code between the curly braces of the function.
- We can call the same function as many times as we want.
- Due to **Hoisting**, we can call a _function declaration_ before it is defined.
- Since **hoisting** isn't considered a good practice, avoid this kind of calling the function.

`console.log('Hello')` and `Number("25")` are _build-in JavaScript functions_.

We call them using parentheses and also we pass in arguments like normal functions.

<br>

## Parameters and Arguments

Functions can have **parameters** and **arguments**. These allow functions to accept and process inputs.

We use parameters as placeholders for information that will be passed as arguments to the function when it is called.

```js
function greet(str, num) {
  console.log(`Hello ` + str);
}
greet("World");
```

Parameters:

- Parameters (optional) are specified between the parentheses `(str, num)`
- Inside the function body, parameters act just like regular variables, that are specific only to this function.
- `str` and `num` act as placeholders for values that will be defined and passed when the function will be called.
- The function parameters are not related to other function parameters if they both have the same parameter names. Or to any other variable name.

Arguments:

- When calling a function that has parameters, we need to specify the actual values for the parameters.
- The values that are passed to the function when it is called are called **arguments**.
- Arguments can be passed to the function as values or variables.
- If we don't specify the arguments, inside the function they will get the value of `undefined`.
- The order in which arguments are passed follows the order that the parameters are declared.
- The values declared as arguments will take the place of the parameters inside the function body.
- In the code example above, `str` will take the value `'Hello'`, and `num` of `undefined` (bc it was not declared).

<br>

## Default Parameters

**Default Parameters** (ES6) allow parameters to have a predetermined value in case there is no argument passed into the function or if the argument is undefined when called.

```js
function greet(str = "World") {
  console.log("Hello " + str);
}
greet(undefined);
```

To assign a default parameter:

- Inside the parentheses, after the parameter name, use the equal sign followed by a default value.
- The argument will override the default parameter if it is declared.
- If there isn't an argument, the default value will be used.
- Default parameters can contain any expression `2 + 5`
- We can use the values of previous parameters `p2 = 5 + p1`, but not forward.
- If we want to leave a parameter at default, use `undefined` as argument.

### Default Parameters ES5

```js
function greet(str) {
  str = str || "World";
}
```

Since an empty parameter will take the value `undefined`, we can use short-circuiting.

<br>

## Return

Once the function is executed, it will produce a result.

At the line of code where the function was called with its name, will be replaced by the resulting value of the function.

By default the resulting value is `undefined`.

```js
function greet() {
  console.log("Hello");
}
console.log(greet()); // undefined
```

Here, `greet()` function doesn't produce a value, because we don't return anything inside the function body.

So by default `greet()` will return `undefined`.

For a function to produce a resulting value, we can use the `return` statement:

```js
function hello() {
  return "Hello";
  return "Hey";
}
console.log(hello()); // Hello
```

- To create a return statement, use the `return` keyword followed by a value.
- The execution of the function will stop at the line of code where `return` is.
- The `return` keyword immediately exit the function. So it will return the value, and then the function is done. Any code after `return` will not work. Again, the code after the first `return` statement will not be executed.
- With `return`, the function will produce and output a value.

We can store the output value of the function to a variable:

```js
const sayHello = hello(); // store and call the function at the same time
console.log(sayHello); // Hello
```

<br>

## Helper Functions

We can use the return value of a function inside another function. These functions being called within another function are often referred to as _helper functions_. Since each function is carrying out a specific task, it makes our code easier to read and debug if necessary.

We can use functions to section off small bits of logic or tasks, then use them when we need to. Writing helper functions can help take large and difficult tasks and break them into smaller and more manageable tasks.

<br>

## Function Expression

Another type of function.

```js
const greet = function (str) {
  return "Hello " + str;
};
greet("World");
```

- In a function expression, the function name is omitted.
- A function with no name is called an _anonymous function_.
- A function expression is often stored in a variable in order to refer to it.

To declare a function expression:

1. Declare a variable which will be the identifier of the function.
2. Assign to that variable an anonymous function `function() {}`

To invoke a function expression, write the name of the variable in which the function is stored, followed by parentheses.

Note: Function expressions are not hoisted so they cannot be called before they are defined.

<br>

## Arrow function

Arrow functions syntax (ES6 feature) a shorter way to write functions.

We can refactor the arrow function syntax in different ways depending on their complexity.

```js
// Arrow function complexity Depending on parameters
const greet = (str, num) => {}; // two or more parameters
// prettier-ignore
const greet = str => {}; // One parameter
const greet = () => {}; // zero parameters
```

Single-line arrow functions (_implicit return_):

```js
const greet = (str) => {
  return `Hello ` + str;
};

// refactoring to a single-line arrow function
const greet = (str) => "Hello " + str;
```

A function body composed of a single-line block does not need curly braces or the return statement.

In this case, the return happens implicitly, the value after the arrow will automatically be returned without us having to explicitly write the return keyword.

The most condensed form of the function is known as _concise body_.

<br>

## Reviewing functions

Three types of functions. All - receive input data, transform data, output data.

### Function declaration

Function that can be called before it's declared.

```js
function greet(str) {
  return "Hello " + str;
}
```

### Function expression

A function value stored in a variable.

```js
const greet = function (str) {
  return "Hello " + str;
};
```

### Arrow functions

Great for quick one-line functions.

```js
const greet = (str) => "Hello " + str;
```

### The structure of a function

1.  The function **name**

2.  A function can have **parameters**

    Parameters are essentially placeholders that receive input values. These are like local variables of a function that are defined only inside of this function.

3.  **Function Body**

    The block of code enclosed in curly braces that we can reuse and process input data.

4.  The **`return`** statement

    At the end of the function, we can have a **`return`** statement, which will output a value from the function.

5.  Calling, running, or invoking a function, using the function and and parentheses `()`

6.  **Arguments**

    Inside parentheses when calling the function, we pass in **arguments**, which are the actual values of the parameters.

7.  When calling the function, the function name will be replaced with the returned value. We can use a variable to store the returned value that was outputted from the function.

    The variable storing the function are calling the functiona at the same time.

<br>
