[&larr; Back](./README.md)

# Parsing Numbers

## Table of Content

- [Converting](#convert-a-string-to-a-number)
- [parseInt](#parseint)
- [parseFloat](#parsefloat)
- [isNaN](#isnan)
- [isFinite](#isfinite)
- [isInteger](#isinteger)

<br>

## Convert a string to a number

```js
Number("25"); // 25
+"25"; // 25
```

When JS sees the plus operator, it will do type coercion to number.

_Note:_ Division by `0` results in `Infinity`, a special JS value.

<br>

## parseInt

```js
// Parsing integers
Number.parseInt("24px", 10); // 24
```

**Arg 1:** the string we want to parse. The string must start with the number, otherwise we get `NaN`.

**Arg 2:** the base of the numeral system we are using.

<br>

## parseFloat

```js
// Parsing floating point numbers
Number.parseFloat(" 2.5rem"); // 2.5
```

It will still work if the string contains whitespace.

There are global functions, we can call them without the `Number` object, just `parseFloat()`. But in modern JS, it's more encouraged to call these function on `Number` object, as it provices namespace.

<br>

## isNaN

```js
Number.isNaN(NaN); // true
Number.isNaN(10); // false
Number.isNaN("10"); // false
```

If `10` Not a Number? No, it is a number.

Return true if the argument value evaluates to `NaN`.

<br>

## isFinite

```js
Number.isFinite(20.5); // true
Number.isFinite("20m"); // false
```

Recommended method to verify if a value is a real number (not a string).

<br>

## isInteger

```js
Number.isInteger(20); // true
Number.isInteger(20.0); // true
Number.isInteger(20.5); // false
```

Verify if a value is an integer, and not a decimal.

Useful since JS doesn't have separate data types for integers and floating point numbers.

<br>
