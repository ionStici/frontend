[&larr; Back](./README.md)

# Strings

- String methods always return a new string.
- All string methods are case sensitive.

```js
const greet = "Hello World";
let str = "JavaScript";

str[0]; // "J"
str.length; // 10

str.indexOf("va"); // 2 | returns the index of the first character
str.lastIndexOf("a"); // 3 | counts from the end
```

## Extracting

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
