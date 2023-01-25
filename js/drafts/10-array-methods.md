# Array Methods

<!--  -->

# Iterators

The built-in JavaScript array methods that help us iterate are called iteration methods, referred to as iterators.

Iterators are methods called on arrays to manipulate elements and return values.

[Array iterator methods MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Iteration_methods)

<!--  -->

Because Arrays are technically objects, they get access to special built-in methods.

<br>

| Mutate original Array | Return new Array |
| :-------------------: | :--------------: |
|  [`.push()`](#push)   |   [`.map()`]()   |
|     [`.pop()`]()      |      [``]()      |
|   [`.unshift()`]()    |      [``]()      |
|    [`.shift()`]()     |      [``]()      |
|    [`.splice()`]()    |      [``]()      |
|        [``]()         |      [``]()      |
|        [``]()         |      [``]()      |
|        [``]()         |      [``]()      |

<br>

## push()

- Add element(s) to the end of an array.
- Returns the new length.
- Mutates the original array.

```js
arr.push(5);
```

<br>

### pop()

Removes the last element of an Array. Returns the removed element.

```js
arr.pop();
```

<br>

### unshift()

Add element(s) to the beginning of an array. Returns the new length.

```js
arr.unshift(0, 1);
```

<br>

### shift()

Removes the first element of an Array. Returned the removed element.

```js
arr.shift();
```

<br>

### Splice()

`splice()` will delete the selected elements from the original array.

Returns what was deleted.

```js
arr.splice(2, 2); // from index 2, delete 2 elements
arr.splice(-1); // delete last element
```

- Parameter 1: The index from where to start to delete
- Parameter 2: The number of elements to delete

<br>

### reverse()

Will reverse the elements of the original array.

```js
arr.reverse();
```

<br>
