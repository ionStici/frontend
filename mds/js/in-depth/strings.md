[&larr; Back](./README.md)

# Strings

- String methods always return a new string.
- All string methods are case sensitive.

## Table of Contents

- [Introduction](#introduction)
- [Extracting using slice](#extracting-using-slice)
- [Why strings have methods](#why-strings-have-methods)
- [toUpperCase and toLowerCase](#touppercase-and-tolowercase)
- [trim whitespace](#trim-whitespace)
- [replace() parts of strings](#replace-parts-of-strings)
- [Methods that return boolean](#methods-that-return-boolean)
- [split() method](#split-method)
- [join() method](#join-method)
- [Padding a string](#padding-a-string)
- [repeat() method](#repeat-method4)

<br>

## Introduction

_Strings are iterables._

```js
const greet = "Hello World";
let str = "JavaScript";

str[0]; // "J"
str.length; // 10

str.indexOf("va"); // 2 | returns the index of the first character
str.lastIndexOf("a"); // 3 | counts from the end
```

<br>

## Extracting using slice

```js
str.slice(4); // "Script"
str.slice(0, 4); // "Java"

greet.slice(-5); // "World" | negative argument: counts from the end

greet.slice(0, greet.indexOf(" ")); // "Hello" | extract the first work
greet.slice(greet.indexOf(" ") + 1); // "World" | extract the last word
```

- **Arg 1:** index where the extraction begins (inclusive).
- **Arg 2:** extraction stops before this index (exclusive).
- If no second argument, then it will extract until the end of the string.

<br>

## Why strings have methods

Strings are primitives, why do they have methods?

When we call a method on a string, JavaScript will convert that string primitive to a string object. Then it's on that object where the method is called. This process is called **boxing**.

When we call a method on a string, what will JavaScript do behind the scenes:

```js
new String("Hello"); // String {'Hello'} === object
```

When the operation is done, the object is converted back to a regular string primitive.

```js
typeof new String("John").slice(1); // string
```

<br>

## toUpperCase and toLowerCase

```js
str.toUpperCase(); // JAVASCRIPT
str.toLowerCase(); // javascript
```

<br>

## trim whitespace

Remove whitespace on the sides of a string, or just from one side.

```js
str.trim();
str.trimStart();
str.trimEnd();
```

<br>

## replace() parts of strings

```js
str.repace("Java", "Type"); // TypeScript | replace only the first occurrence
str.repaceAll("Java", "Type"); // TypeScript | replace all occurrences
```

- **Arg 1:** part of the string we intend to replace
- **Arg 2:** new piece of string to replace with

<br>

## Methods that return boolean

```js
str.includes("Script"); // true
str.startsWith("Java"); // true
str.endsWith("Script"); // true
```

<br>

## split() method

Split a string into multiple parts and store them in an array.

As an argument to `split()`, we specify a separator string.

```js
"Hello World".split(" "); // (2) ["Hello", "World"]
const [firstName, lastName] = "John Stici".split(" ");
```

As `split()` returns an array, we can use desctructuring to create variables directly.

<br>

## join() method

Using `join()` we can concatenate an array of strings into a single string.

```js
["Java", "Script"].join(""); // JavaScript
```

As an argument to `join()`, we specify a separator string to be placed between each concatenated string.

<br>

## Padding a string

Padding a string refers to adding a number of characters to the string until it has a certain desired length.

Add characters to the beginning or end of a string:

```js
"World".padStart(7, "++").padEnd(9, "++"); // ++World++
```

- **Arg 1:** the length that we want the string to be.
- **Arg 2:** the character to pad the string with.

<br>

## repeat() method

Repeat a string multiple times:

```js
"Hello ".repeat(3); // Hello Hello Hello
```

<br>
