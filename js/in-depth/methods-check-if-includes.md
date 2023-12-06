[&larr; Back](./README.md)

# Check if it includes

|             1             |         2         |          3          |
| :-----------------------: | :---------------: | :-----------------: |
| [`includes()`](#includes) | [`some()`](#some) | [`every()`](#every) |

<br>

## includes

**`includes()`** uses strict equality for comparison.

```js
arr.includes(2); // true
```

Returns true if a certain element is in the array, and false if not.

## some

**`some()`** returns true if at least 1 element in the array satisfy the condition.

```js
arr.some((el) => el > 250); // true
```

## every

**`every()`** returns true if _every_ element in the array satisfy the condition.

```js
arr.every((el) => el > 250); // false
```

<br>
