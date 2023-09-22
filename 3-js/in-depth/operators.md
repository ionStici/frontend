[&larr; Back](./README.md)

# Operators

## Table of Content

- [Short Circuiting](#short-circuiting)
- [The nullish coalescing operator](#the-nullish-coalescing-operator)
- [Logical Assignment Operators](#logical-assignment-operators)
- [Optional Chaining](#optional-chaining)

<br>

## Short Circuiting

_Three characteristics about boolean operators:_

- They can process any data type
- They can return any data type
- They can do Short Circuiting Evaluation

### `||` OR Short Circuiting

`||` will return the first truthy value. If all are falsy, then it will return the last one.

```js
undefined || "John" || true; // "John"
undefined || null; // null
data.name || "invalid"; // check if "name" property exists
```

### `&&` AND Short Circuiting

`&&` will return the first falsy value. If all are truthy, then it will return the last one.

```js
0 && "John"; // 0
7 && "hi" && true; // true
obj.method && obj.method(); // execute method if it exists
```

<br>

## The nullish coalescing operator

`??` operator works the same as the `||` OR operator, but with the concept of nullish values instead of falsy value.

Nulish values are `undefined` and `null`, it doesn't include zero `0` or empty string `""`

```js
0 ?? -1; // 0
```

<br>

## Logical Assignment Operators

_ES2021_ Operators

**Old way** - add a property to an object if the object does not have one.

```js
obj.num = obj.num || 10;
```

If `num` exists then nothing happens, it not then it will add `num` to the object.

### OR assignment operator `||=`

```js
obj.num ||= 10;
```

This operator assigns a value to a variable if it is currently falsy.

### The logical nullish assignment operator `??=`

```js
obj.num ??= 10;
```

This works as OR assignment, but for zero and empty string as well.

### AND assignment operator `&&=`

```js
obj.num &&= "Hello";
```

Replacing an existing value to a new one (if it is truthy).

<br>

## Optional Chaining

_for objects and arrays_

If a certain property that is before `?.` does not exists, then `undefined` is returned, if it exists then the next property will be evaluated from there.

```js
data?.property;
obj.method?.(); // check if a method exists before we call it
```

Without optional chaining we would get an error, because we can't read properties from `undefined`.

_Note:_ `?.` operator works with the nullish concept, reacts only to `undefined` and `null`

### Optional Chaining and Arrays

```js
// check if array is empty
arr[0]?.property;
```

Only if `arr[0]` exists then `.property` will be evaluated.

<br>
