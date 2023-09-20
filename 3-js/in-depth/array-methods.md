[&larr; Back](./README.md)

# Array Methods

|            1            |           2           |         3         |            4             |
| :---------------------: | :-------------------: | :---------------: | :----------------------: |
| [`forEach()`](#foreach) | [`reduce()`](#reduce) | [`join()`](#join) | [`at()`](#the-at-method) |

## forEach

**`forEach`** executes a callback function for each array element.

```js
arr.forEach((el, i, arr) => console.log(el));
```

_Parameters:_ current element -> current index -> entire array.

Underscore `_` throwaway variable convention, means: we don't use this parameter.

## reduce

Boil down all the elements in an array to one single value.

```js
arr.reduce((acc, el, i, _) => acc + el, 0); // sum
arr.reduce((acc, el) => (acc < el ? el : acc), 0); // max value
```

One more parameter: `(acc, el, i, arr)` - the accumulator.

In each iteration, `reduce()` returns the updated accumulator.

The second argument of `reduce()` is the initial value of the accumulator.

## join

**`.join()`** returns a string created by joining all the array elements.

```js
arrayOfStrings.join(" ");
```

Between each value it will place the separator we pass in as argument.

## The `at` method

Retrieve array elements according to its index.

```js
arr.at[0];
arr.at[-1]; // last element
```

_Use cases:_ retrieve last element. To chain methods.

<br>
