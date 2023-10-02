[&larr; Back](./README.md)

# Regular expressions

- [Regular expressions by MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions)
- [Regular expression syntax cheat sheet by MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Cheatsheet)
- [regex 101: build, text, debug](https://regex101.com/)
- [JavaScript Regex by Programiz](https://www.programiz.com/javascript/regex)

<br>

Regular expressions are patterns used to match character combinations in strings. In JavaScript, regular expressions are also objects.

These patterns are used with `exec()` and `test()` methods of `RegExp`, and with `match()`, `matchAll()`, `replace()`, `replaceAll()`, `search()`, `split()` methods of `String`.

_Creating a Regular expression:_

```js
// Regex literal, a pattern enclosed between slashes:
const re = /ab+c/;

//  RegExp object constructor function:
const re = new RegExp("ab+c");
```

<br>
