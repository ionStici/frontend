[&larr; Back](./README.md)

# Math and Rounding

The following methods work in a similar way as string methods. Numbers are primitives, and primitives don't have methods, so behind the scenes JS will do **boxing** - transform a number value to a number object, then call the method from that object. When the operation is finished, it will convert the number back to a primitive.

## Table of Content

- [Square Root](#square-root)
- [Minimum and Maximum Value](#minimum-and-maximum-value)
- [Constants](#constants)
- [Random Number](#random-number)
- [Rounding](#rounding)

<br>

## Square Root

```js
Math.sqrt(25); // 5
25 ** (1 / 2); // 5
8 ** (1 / 3); // 2 | cubic root
```

## Minimum and Maximum Value

```js
Math.min(5, "10", 3); // 3
Math.max(5, "10", 3); // 10
```

It does type coercion.

## Constants

```js
Math.PI; // 3.141592653589793
```

## Random Number

```js
Math.random(); // 0.4277832796521357
```

Returns a random number between `0 > x < 1`

<br>

## Rounding

### Rounding Integers

```js
// Remove any decimal part
Math.trunc(23.3); // 23

// Round to the nearest integer
Math.round(23.9); // 24

// Round up
Math.ceil(23.3); // 24

// Round down
Math.floor(23.9); // 23

// Floor: Negative number
Math.floor(-23.3); // 24
```

All these methods do type coercion.

_Note:_ For negative numbers, `floor` rounds from `0` up.

### Rounding Decimals

```js
(2.7).toFixed(0); // '3' - returns as string data type
(2.7).toFixed(3); // '2.700'
+(2.759).toFixed(2); // 2.75 - number data type
```

`toFixed()` accepts an integer representing the number of decimals to trim or add.

If we specify `0`, it will round the number.

Since `toFixed()` returns a string, we can use the plus sign in front of the syntax to convert the return value to a number.

<br>
