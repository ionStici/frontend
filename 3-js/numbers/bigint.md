[&larr; Back](./README.md)

# Working with BigInt

**BigInt** is one of the primitive data types, it is a special type of integers that was introduced in ES2020.

Numbers are represented internally as 64 bits, this means that there are exactly 64 `1`s and `0`s to represent any given number. Of these 64 bits on ly 53 are used to store the digits themselves, the rest are for storing the position of the decimal point and the sign. Now, if there are only 53 bits to store a number, that means that there is a limit of how big numbers can be, and we can calculate that number.

```js
2 ** 53 - 1; // 9_007_199_254_740_991
Number.MAX_SAFE_INTEGER; // 9007199254740991
```

This essentially is the biggest number that JavaScript can safely represent.

This number is so important that it is even stored into the number namespace.

Any integer that is larger than this, is not safe, which means that it cannot ne represented accurately.

If we do calculations that a bigger than **max safe number**, then we might lose precision. In some numbers it does work, because JS behind the scenes uses some tricks to still represent some of the **unsafe numbers**.

This can be a problem sometimes, because in some situations we might need numbers bigger than max safe, for example for database IDs, and these number are actually used in other languages. For example, we get a number larger than max safe from an API, and then we have no way of storing that in JS. At least not until now, because startin from ES2020, a new primitive was added, called **BigInt**.

<br>

## BigInt

**BigInt** (big integer) can be used to store numbers as large as we want, no matter how big.

```js
4356789009807656789543576890n;
```

We just place the `n` letter at the end of a number, and it will transform a regular number into a BigInt number.

Note: The `BigInt(4838430148342043)` function should only be used with small numbers.

BigInt new primitive data type adds new capabilities to the JavaScript language, when you need to work with really huge numbers.

<br>

## Operations with BigInt

- All the usual operators still work the same.
- We can't mix BigInt with regular numbers. We can try to convert a regular number to BigInt using the `BigInt` function and then perform the operation.
- `Math` methods does not work with BigInt.

```js
123n * 321n; // 39483n
Math.sqrt(16n); // error
2n + 5n; // error
```

### Exception 1: Comparison

```js
20n > 15; // true

20n === 20; // false

20n == 20; // true
20n == "20"; // true
```

When comparing using the triple operator, we get `false` because the triple operator does not do type coercion, so it results 2 different primitives.

When using the loose equal operator `==`, JS does type coercion, after which they're both the same.

### Exception 2: string concatenation

_The BigInt number is converted to a string:_

```js
100n + " apples"; // 100 apples
```

### Division

BigInt are integers, it doesn't operate with decimals.

```js
10n / 3n; // 3n
11n / 3n; // 3n
10 / 3; // 3.333
```

BigInt returns the closest BigInt, it simply cuts off the decimal part.

<br>
