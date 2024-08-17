# TypeScript and JavaScript

## Table of Contents

- [Differences between JavaScript and TypeScript](#differences-between-javascript-and-typescript)
- [Advantages of using TS over JS](#advantages-of-using-ts-over-js)
- [Statically Typed vs. Strongly Typed](#statically-typed-vs-strongly-typed)
- [How TypeScript Works](#how-typescript-works)
- [Transpilation vs. Compilation vs. Interpretation](#transpilation-vs-compilation-vs-interpretation)

## Differences between JavaScript and TypeScript

**TypeScript** is a superset of JavaScript. This means that javaScript code is valid TypeScript code, but TypeScript provides additional features that make it more reliable.

JavaScript has a vast and mature ecosystem with numerous libraries and frameworks. TypeScript extends JS's ecosystem, having good compatibility with existing JS code, making TS powerful.

TypeScript needs to be transpiled to JavaScript before runtime execution.

TS supports JS libraries, it is not environment specific, you can use TS with node.js for example.

**JavaScript:** Dynamically-typed, variable types are determined at runtime.

**TypeScript:** Statically-typed, variable types are determined at transpilation.

| Criteria          |    JavaScript     |    TypeScript    |
| ----------------- | :---------------: | :--------------: |
| **First release** |       1995        |       2012       |
| **Created by**    |     Netscape      |    Microsoft     |
| **Typing**        | Dynamically-typed | Statically typed |
| **OOP**           |  Prototype-based  |   Follows OOP    |

## Advantages of using TS over JS

- In TS, errors are caught at transpile time, resulting in less runtime errors.

- The TS compiler can transpile backwards up to ES3. TS is excellent for large-scale projects.

- Provides additional programming features, enhancing code organization and maintainability.

- Due to static typing and additional features, TS code becomes more self-documenting.

## Statically Typed vs. Strongly Typed

- **Statically Typed:** Type checking is done at transpile time.

- **Strongly Typed:** Strict type rules are enforced, and implicit type coercion is limited.

**TypeScript:** Statically typed and strongly typed, providing type checking at transpile time and enforcing strict type rules.

## How TypeScript Works

**TypeScript** code is a superset of JavaScript code - it has all the features of traditional JavaScript but adds some new features (e.g. types).

TypeScript allows us to write JavaScript with a set of tools called a type system that can spot potential bugs in, clarify the structure of, and help refactor our code.

- TypeScript files extension: `main.ts`
- We run TypeScript code through the TS compiler, and if the code adheres to TypeScript's standards, it will output a JavaScript version of the file

The `tsconfig.json` file that is placed in the root of the project, contains the enforced rules for the TypeScript compiler.

When the compiler notices an error, it will throw an error.

## Transpilation vs. Compilation vs. Interpretation

**Compilation:** Entire source code is translated before execution, it produces a standalone executable file. Faster execution. Platform specific.

_Example:_ C is a compiled language. The C source code is compiled by a C compiler before execution. Compilation produces a standalone executable file that can be run on a specific machine architecture.

**Interpretation:** Code is translated and executed line by line at runtime. No separate executable file. Potentially slower execution. Platform-independent.

_Example:_ JavaScript is primarily an interpreted language. The JavaScript engine reads and executes the source code line by line at runtime. No separate compilation step. JavaScript code is executed directly by the browser or another runtime environment.

**Transpilation:** High-level source code is translated to equivalent code in another language. May involve an additional processing step. Enable features, address compatibility.

_Example:_ TypeScript is a superset of JavaScript. TypeScript code is transpiled into JavaScript before execution. The TypeScript compiler `tsc` translates TypeScript code into equivalent JavaScript code.

TypeScript code is transpiled into JavaScript code, and the resulting JavaScript code is executed in a JavaScript runtime environment. The TypeScript compiler removes type annotations and other TypeScript-specific features, producing JavaScript code that is compatible with browsers or other JS runtime environments.
