[&larr; Back](./../README.md)

# Modules

- [MDN JavaScript Modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
- [About Modules (Theory)](./modules-theory.md)

<br>

## Table of Content

- [Introduction](#introduction)
- [Importing a Module](#importing-a-module)
- [ES6 Named Exports and Imports](#es6-named-exports-and-imports)
  - [Renaming Imports to Avoid Naming Collisions](#renaming-imports-to-avoid-naming-collisions)
  - [Import all the exports of a module](#import-all-the-exports-of-a-module)
- [Imports are a live connection to exports](#imports-are-a-live-connection-to-exports)

<br>

## Introduction

- Modules are JavaScript files.
- The camelCase for naming your module files.
- To start using modules, in the `script` tag of the main importing module, define the `type` attribute set to `module`.
- No need to specify strict mode when using modules, all modules are executed in strict mode by default.

<br>

## Importing a Module

```
project-directory/
| -- import.js
| -- export.js
```

```js
// export.js | EXPORTING MODULE
console.log("Exporting module");
const data = "sensitive data";
```

```js
// import.js | IMPORTING MODULE
import "./export.js";
console.log("Importing module");
console.log(data);
```

```
// Console
Exporting module
Importing module
Uncaught ReferenceError: data is not defined
```

To import the whole module: `import` keyword + a string with the location of the module.

This technique is used when we just want the exported module to be executed, without its data to interact with the importing module.

The code from the exported module is executed before any code from the importing module.

The code in `import.js` is parsed and before it is executed, all the code from import modules is executed first.

The same is true when we place the `import` statement at the end of our code in the main module. All the `import` statements are hoisted to the top.

Variables declared inside a module, are scoped to its module. The module itself is like the top-level scope, this means that all top-level variables are private inside the module. In traditional scripts, top-level variables are global scoped.

This is why by default, inside the importing module, we can't use variables from the exporting module, we will get a reference error. Again, the variables are scoped to the current module.

If we want to use any variable in the importing module from other modules, we have to export them first.

In ES6 mdoules, there are 2 types of exports and imports: **Named** and **Default**.

<br>

## ES6 Named Exports and Imports

- **Exporting multiple values as named exports:** pass the values you want to export in the curly braces of the `export` syntax separated by commas.
- **Exporting individual values as named exports:** place the `export` keyword in front of the variable declarations.

```
project-directory/
| -- import.js
| -- export.js
```

```js
// export.js | EXPORTING MODULE
export const data = "DATA";
let sayHello = () => console.log("HELLO");
export { data, sayHello };
```

The exported variables are now available to be imported as **named exports** and used by other file modules.

```js
// import.js | IMPORTING MODULE
import { data, sayHello } from "./export.js";
```

From an `import` statement, we call the variables we want to import by their names inside curly braces, and then specify the module file path from where we want to import.

Now, from the main importing module, we can use the variables or functions we imported like it was defined here in the same scope.

Exports always need to happen in the top-level code. We can't export values inside a function body or an `if` block.

### Renaming Imports to Avoid Naming Collisions

```js
// import.js | IMPORTING MODULE
import { data as list, sayHello } from "./export.js";
```

- Use the `as` keyword to rename imports.
- From out example, the `data` exported variable will be identifed in the imported module as `list`.
- We can rename variables when importing in both cases, when exporting and when importing.

### Import all the exports of a module

```js
// import.js | IMPORTING MODULE
import * as NewData from "./export.js";
NewData.data; // "DATA"
```

- We can import all the exports of a module at the same time using the `*` symbol.
- The meaning of `*` is _"everything"_. The the data will be stored in an object.
- Convention: when importing everything, start the name of the object with a capital letter.
- This will create an object containing everything that is exporting from the module we specified.
- Then, we access the exported variables or functions of the object that was created as usual: `NewData.data`.
- This exporting module is like a public API (like a class). Everything else stays private inside the module.

<br>

## Default Exports and Imports

**Default exports** are used for exporting a single value per module to represent the entire module.

In practice, often, but not always, the default export value is an object containing the entire set of functions and data values of a module.

For default exports we use the `default` keyword, and it works only for one value per module.

```
project-directory/
| -- import.js
| -- export.js
```

Syntax 1:

```js
// export.js | EXPORTING MODULE
export default () => console.log("Hello");
```

Or:

```js
const data = "DATA";
export default data;
```

Syntax 2:

```js
// export-second.js | EXPORTING MODULE
const data = "DATA";
export { data as default };
```

Importing default exports:

```js
import sayHello from "./export.js";
import data from "./export-second.js";
```

Notice that the curly braces are gone from the import statement. This syntax is actually shorthand for:

```js
import { default as sayHello } from "./export.js";
```

- The imported **default** value may be given any name the programmer chooses.
- Note that in `export.js` module we simply export a value produced by a function, besides this the exported function is not named, we simply export the function's value. And then when we import the function as default export we give it a name that we want.
- The preferred style of using modules is to just use one default export per module and then import it.

### Mix named and default imports in one single import statement

```js
// import.js | IMPORTING MODULE
import data, { sayHello as greet } from "./export.js";
```

Where `data` is the default export, and `sayHello` is the named export.

In practice, don't do this, avoid complexity.

<br>

## Imports are a live connection to exports

```
project-directory/
| -- import.js
| -- export.js
```

```js
// export.js | EXPORTING MODULE
export const arr = [];
export const addData = (el = arr.push(el));
```

```js
// import.js | IMPORTING MODULE
import { arr, addData } from "./export.js";

addData(25);
console.log(arr); // (1) [25]
```

We mutate an array using a function, both imported from the exported module.

This example proves that imports are not simply a copy of the value exported, instead it is a live connection, they point to the same place in memory.

<br>
