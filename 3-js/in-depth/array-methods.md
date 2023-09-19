[&larr; Back](./README.md)

# Array Methods

[**Array Methods | MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Iteration_methods)

<br>

## Methods that mutate the original array

|       1       |      2      |          3          |        4        |         5         |          6          |       7       |       8       |
| :-----------: | :---------: | :-----------------: | :-------------: | :---------------: | :-----------------: | :-----------: | :-----------: |
| [push](#push) | [pop](#pop) | [unshift](#unshift) | [shift](#shift) | [splice](#splice) | [reverse](#reverse) | [sort](#sort) | [fill](#fill) |

### push

**`.push()`** add element(s) to the end of an array.

Returns the new length. Mutates the original array.

### pop

**`.pop()`** remove the last element of an array.

Returns the removed element. Mutates the original array.

### unshift

**`.unshift()`** add element(s) to the beginning of an array.

Returns the new length. Mutates the original array.

### shift

**`.shift()`** add element(s) to the beginning of an array.

Returns the removed element. Mutates the original array.

### splice

**`.splice()`** will delete the selected elements from the original array.

Returns what it deleted.

- Arg 1: The index from where to start to delete
- Arg 2: The number of elements to delete

```js
arr.splice(2, 2); // from index 2, delete 2 elements
arr.splice(-1); // delete last element
```

### reverse

**`.reverse()`** will reverse the elements of the original array.

### sort

**`.sort()`** mutates the original array.

```js
strings.sort(); // for strings: sort alphabetically
numbers.sort(); // for numbers: the numbers are converted to strings, then alphabetically ordered
```

_Sorting numbers in ascending or descending order:_

```js
numbers.sort((a, b) => a - b);
```

- (a - b) ascending order, (b - a) descending order
- a - the current element, b - the next element

### fill

**`.fill`** override original array.

```js
arr.fill(1, 2, 4);
```

- Arg 1: the value
- Arg 2: index where we start, inclusive
- Arg 3: index where filling ends, exclusive

### Using a method without mutating the original array

```js
const newArray = arr.slice().sort();
```

<br>
