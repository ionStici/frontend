[&larr; Back](./README.md)

# Mutating Array Methods

|       1       |      2      |          3          |        4        |          5          |         6         |       7       |       8       |
| :-----------: | :---------: | :-----------------: | :-------------: | :-----------------: | :---------------: | :-----------: | :-----------: |
| [push](#push) | [pop](#pop) | [unshift](#unshift) | [shift](#shift) | [reverse](#reverse) | [splice](#splice) | [sort](#sort) | [fill](#fill) |

```js
// trick: using a method without mutating the original array
const newArray = arr.slice().sort();
```

### push

**`.push()`** - add element(s) to the end of an array. Return: new length.

### pop

**`.pop()`** - remove the last element of an array. Return: the removed element.

### unshift

**`.unshift()`** - add element(s) to the beginning of an array. Return: new length.

### shift

**`.shift()`** - add element(s) to the beginning of an array. Return: the removed element.

### reverse

**`.reverse()`** - reverse the elements of an array.

### splice

**`.splice()`** - delete elements from an array. Return: deleted elements.

**Arg 1:** start index / **Arg 2:** how many elements to delete

```js
arr.splice(2, 2); // from index 2, delete 2 elements
arr.splice(-1); // delete last element
```

### sort

```js
// calling sort() without arguments
strings.sort(); // for strings: sort alphabetically
numbers.sort(); // for numbers: the numbers are converted to strings, then alphabetically ordered
```

```js
// Sorting numbers in ascending or descending order
numbers.sort((a, b) => a - b); // ascending
numbers.sort((a, b) => b - a); // descending
```

### fill

**`.fill`** override original array.

```js
arr.fill(1, 2, 4);
```

**Arg 1:** value / **Arg 2:** start index (inclusive) / **Arg 3:** end index (exclusive)

<br>
