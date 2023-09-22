[&larr; Back](./README.md)

# Spread and Rest

## The Spread Operator

_The Spread Operator_ `...` expands an iterable - array or string - into all its elements.

```js
const arr = [1, 2, 3];
console.log(...arr); // 1 2 3
```

We can use the spread operator whenever we would otherwise write multiple values separated by commas.

```js
// 1. create a shallow copy
const newArr = [...oldArr];

// 2. merge arrays
const arr = [...arr1, ...obj.arr, 5];

// 3. arguments - function call
const log = (a, b, c) => console.log(a, b, c);
log(...arr); // 1 2 3
```

Since 2018, **the spread operator works on objects**, even though objects are not iterables.

```js
// Object Shallow Copy
const me = {
  name: "John",
  ...data,
};
```

This will copy all the properties from `data` object into `me`, similar to `Object.assign()`.

<br>

## Rest Pattern

**Rest Pattern** - collect multiple elements and pack them into an array.

We use the rest pattern on the left of the assignment operator.

```js
const [a, ...rest] = [1, 2, 3]; // a = 1 | rest = (2) [2, 3]
```

The remaining elements are destructured in the `rest` array. The rest syntax collects all the remaining elements after the last variable.

**Rest pattern in objects:**

```js
const { john, ...otherPeople } = people;
```

First, the `john` property was destructured. After which, all the remaining properties were destructured in `otherPeople` variable.

### Rest Parameters

The **rest parameter** syntax allows a function to accept an indefinite number of arguments as an array.

```js
const log = (...nums) => console.log(nums);
log(1, 2, 3); // (3) [1, 2, 3]
```

<br>
