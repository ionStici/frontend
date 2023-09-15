[&larr; back](./README.md)

# Sass Introduction

**Sass** is a CSS pre-processor, an extension of CSS that adds new features and tools.

How Sass works? We write Sass code in special `.scss` or `.sass` files, then we run the Sass compiler that converts this code into regular CSS code.

**Sass Source Code -> Sass Compiler -> Compiled CSS Code**

## Sass and Scss

- The **Sass** syntax is indentation sensitive and doesn't use curly braces.

  Code example: `.nav list-style: none` File format: `.sass`

- The **Scss** syntax looks like the oiginal CSS code.

  Code example: `.nav { list-style: none; }` File format: `.scss`

These two syntaxes works in the same way, just look different.

## Main Sass Features

- **Variables:** for reusable values such as colors, font-sizes, spacing, etc.
- **Nesting:** nest selectors inside of one another, allowing us to write less code;
- **Operators:** for mathematical operations right inside of CSS;
- **Partials and Imports:** write CSS in different files and import them all into one single file;
- **Mixins:** write reusable pieces of CSS code;
- **Functions:** similar to mixins, with the difference that they produce a value that can than be used;
- **Extends:** make different selectors inherit declarations that are common to all of them;
- **Control directives:** for writing complex code using conditionals and loops.

<br>
