[&larr; Back](./README.md)

# Arrays

## Table of Content

- [Creating an Array](#creating-an-array)
- [Accessing Elements](#accessing-elements)
- [Add and Update Array Elements](#add-and-update-array-elements)
  - [Arrays with let or const](#arrays-with-let-or-const)
- [The .length property](#the-length-property)
- [Array Methods](#array-methods)
  - [The .push() method](#the-push-method)
  - [The .pop() method](#the-pop-method)
  - [unshift() and shift() methods](#unshift-and-shift-methods)
- [Arrays and Functions](#arrays-and-functions)
- [Nested Arrays](#nested-arrays)

<br>

## Creating an Array

Creating an array using an array literal syntax:

```js
[true, 'JavaScript', 25];
const arr = [1, 2, 3];
```

- An array literal creates an array by wrapping items (elements) in square brackets `[]`.
- The array elements are separated by commas. We can save arrays in variables.
- Arrays can store any data type, arrays inside arrays, calculate and do expressions.

Another way of creating Arrays using the `Array()` function:

```js
const arr = new Array(1, 2, 3);
```

<br>

## Accessing Elements

Each element in an array has a numbered position known as its **index**.

We can access individual items using their index. The first element is at index `0`.

Arrays in JavaScript are zero-based (zero-indexed), meaning the positions start counting from `0`.

```js
const arr = [true, 'js', 25];
arr[0]; // true
const x = arr[2]; // access and store an array element
```

Access array element using the name of the array, then bracket notation `[]` with the element index.

This will access the spot in memory and reference the stored element.

Using the same technique, we can access individual characters in a string `'abc'[1] // b`.

<br>

## Add and Update Array Elements

```js
const arr = [1, 3]; // [1, 3]
arr[1] = 2; // [1, 2]  update / replace
arr[2] = 3; // [1, 2, 3]  add
```

Above, first we replaced the second element with another value, then we added a third element.

<br>

### Arrays with let or const

As a practice habit, always declare your arrays with `const`. Only primitive value are immutable.

Elements in an array declared with `const` remain mutable, we can change the content of a `const` array.

But, we cannot reassign a completely new array or a different value. Example:

```js
const arr = [1];
let arr_2 = [1];

arr[1] = 2; // [1, 2]
arr = [1, 2]; // ERROR
arr_2 = [1, 2]; // [1, 2]
```

We can add or update _individual_ elements of a `const` array, but not replace the entire array.

<br>

## The .length property

The built-in array property `length` returns the number of elements in an array.

The result is gonna be the exact amount of elements (not zero based).

```js
const arr = [1, 2, 3];
arr.length; // 3
```

We chain the array name with the `length` property using _dot notation_.

Using `length`, we can Automatically access the last element of any array, without counting how many elements are in the array:

```js
arr[arr.length - 1]; // 3
```

<br>

## Array Methods

Built-in JavaScript Array methods. [Codecademy Array Resource](https://www.codecademy.com/resources/docs/javascript/arrays).

<br>

### The .push() method

Add an element to the end of an array.

```js
const arr = ['js'];
let newLength = arr.push('html', 'css'); // ['js', 'html', 'css']
```

- We access the `push` method using dot notation.
- Technically, `push` is a function, so we call it with parentheses.
- `push()` can take one or multiple arguments separated by commas.
- `push()` will append its arguments to the end of the array.
- Because `push` mutates the initial array, it is referred as a _destructive array method_.

<div></div>

- Since `push` is a function, it will return the new length of the new array.
- To capture that value, we can store the whole statement in a variable.

  _Note:_ This actually executes the push function at the same time.

<br>

### The .pop() method

`pop()` removes the last item of an array.

- No arguments needed.
- Mutates the initial array.

```js
let val = arr.pop(); // 'css'
```

`pop` returns the removed element. We can save it in a variable.

<br>

### unshift() and shift() methods

`unshift()` adds elements to the beginning of an array. It works like push, returns the new length.

```js
arr.unshift('The First');
```

`shift()` removes the first element from an array. No arguments required, returns the removed element.

```js
arr.shift();
```

<br>

## Arrays and Functions

```js
const webTech = ['css'];

const mutate = function (arr, data) {
  arr.push(data);
  console.log(webTech);
};

mutate(webTech, 'JS'); // ['css', 'JS']
```

If we pass an array into a function as an argument, and if the array is mutated inside the function, that change will also be reflected outside the function, mutating the original array.

Concept explained as pass-by-reference since what we’re actually passing to the function is a reference to where the variable memory is stored and changing the memory.

<br>

## Nested Arrays

```js
const nestedArr = [1, [2], [3, [4]]];
nestedArr[2][1][0]; // 4
```

To access elements within the nested array we can chain more bracket notation with index values.

<br>
