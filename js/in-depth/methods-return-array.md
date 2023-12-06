[&larr; Back](./README.md)

# Methods: Return new array

|        1         |           2            |          3           |           4            |               5                |                 6                 |
| :--------------: | :--------------------: | :------------------: | :--------------------: | :----------------------------: | :-------------------------------: |
| [`.map()`](#map) | [`.filter()`](#filter) | [`.slice()`](#slice) | [`.concat()`](#concat) | [`.flat()`](#flat-and-flatmap) | [`.flatMap()`](#flat-and-flatmap) |

## map

**`.map()`** loops over the array it is called on. In each iteration it will execute the callback function and replace the element from the current iteration with what the callback returns.

```js
const newArr = arr.map((el, i) => el * i);
```

## filter

**`.filter()`** - the array element for which the condition from the callback is true, will make it into the new array.

```js
const newArr = arr.filter((el) => el > 5);
```

## slice

**`.slice()`** - extracting parts of an array.

**Arg 1:** start index (inclusive) / **Arg 2:** end index (exclusive)

- If only 1 argument, then it will extract until the end of the array.
- A negative argument will counts from the end.

```js
arr.slice(2, 4); // index 2 and 3
arr.slice(-1)[0]; // the last element
arr.slice(); // a shallow copy
```

## concat

**`.concat()`** - concatenate 2 arrays.

```js
const newArr = arr.concat(arr2);
const newArr = [...arr, ...arr2];
```

## flat and flatMap

**`.flat()`** - spreads inner arrays. Argument: The depth level specifying how deep a nested array structure should be flattened.

**`.flatMap()`** - first the map method iterates, then the array is flattened only 1 level.

```js
arr.flat(2);
arr.flatMap((el) => el * 5);
```

<br>
