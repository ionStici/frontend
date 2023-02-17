[&larr; Back](./README.md)

# Style

## Table of Content

- [Inline Styles](#inline-styles)
- [Make a Style Object Variable](#make-a-style-object-variable)
- [Style Name Syntax](#style-name-syntax)
- [Style Value Syntax](#style-value-syntax)
- [Share Styles Across Multiple Components](#share-styles-across-multiple-components)

<br>

## Inline Styles

```jsx
<h1 style={{ color: "red" }}>Hello World</h1>
```

Double curly braces:

1. The outer curly braces inject JavaScript into JSX.
2. The inner curly braces create a JavaScript object literal.

Object literals inside JSX: double curly braces.

This is all we need to apply basic styles in React.

<br>

## Make a Style Object Variable

Better option for using styles in React: Store a style object in a variable and then inject that variable into JSX.

```jsx
const styles = {
  color: "#333",
  fontSize: "20px",
};

<h1 style={styles}>Hello World</h1>;
```

Defining a variable named `style` in the top-level scope would be an extremely bad idea in many JavaScript environments! In React, however, it’s totally fine.

<br>

## Style Name Syntax

In regular JavaScript, style names are written in hyphenated-lowercase:

```js
const styles = {
  "margin-top": "20px",
  "background-color": "green",
};
```

In React, those same names are instead written in camelCase:

```jsx
const styles = {
  marginTop: "20px",
  backgroundColor: "green",
};
```

This has zero effect on style property values, only on style property names.

<br>

## Style Value Syntax

In regular JS, style values are almost always strings. Even if a style value is numeric, you usually have to write it as a string so that you can specify a unit. For example, you have to write `"450px"` or `"20%"`.

In React, if you write a style value as a number, then the unit `"px"` is assumed.

If you want a font size of 30px, you can write:

```jsx
const styles = {
  fontSize: 30,
  padding: "2rem",
};
```

And if you want to use units other than “px,” you can use a string.

Specifying “px” with a string will still work, although it’s redundant.

A few specific styles will not automatically fill in the “px” for you. These are styles where you aren’t likely to use “px” anyway, so you don’t really have to worry about it. [Here is a list of styles that don’t assume “px”.](https://github.com/facebook/react/blob/4131af3e4bf52f3a003537ec95a1655147c81270/src/renderers/dom/shared/CSSProperty.js#L15-L59)

<br>

## Share Styles Across Multiple Components

One way to make styles reusable is to keep them in a separate JavaScript file. This file should export the styles that you want to reuse, via export. You can then import your styles into any component that wants them.

```jsx
export const styles = {};
```

<br>
