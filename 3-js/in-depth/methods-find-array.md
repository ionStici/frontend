[&larr; Back](./README.md)

# Find Index or Element

|            1             |              2               |         3          |
| :----------------------: | :--------------------------: | :----------------: |
| [`.indexOf()`](#indexof) | [`.findIndex()`](#findindex) | [`.find()`](#find) |

## indexOf

```js
arr.indexOf("hi"); // 2
```

As argument, we pass the element we want to reference.

**`.indexOf()`** returns the index at which an element is located.

_Note:_ if the argument doesn't exist, it will return `-1`

## findIndex

```js
const idx = arr.findIndex((el) => {
  return el === "John";
});
```

**`.findIndex()`** will return the index of the first element for which the condition is true.

## find

```js
const num = arr.find((el) => {
  return el === "John";
});
```

**`.find()`** will return the first element for which the condition from the callback is true.

<br>
