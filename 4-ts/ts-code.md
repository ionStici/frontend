[&larr; Back](./README.md)

# TypScript Code

## Table of Content

- [Introduction](#introduction)
- [Functions](#functions)
- [Arrays](#arrays)
- [Enums](#enums)

<br>

## Introduction

- TypeScript files extension: `main.ts`

- `tsc` command - transpile TypeScript code to JavaScript code.

- `tsconfig.json` file specifies the transpier options required to compile TypeScript.

- **Type Inferences:** when the type is not explicitly declared by the user, TypeScript will infer the type on its own.

- **Type Shapes:** an object's shape describes what properties and methods it does or doesn't contain.

- **Any:** When TS isn't able to infer a type, it will consider the variable of type `any`

  Variables of type `any` can be reassigned to any value later on.

```ts
const my_name: string = "John";
```

- **Variable Type Annotations (declaration):** explicitly tell TS what type a variable is.

<br>

## Functions

```ts
const my_name: string = "John";

const greet = (name: string = "Mike", age?: number): string => {
  return `Hello, ${name}!`;
};

greet(my_name); // Hello, John!
```

- **Function parameter type annotation:** `(name: string)`

  Parameters without a type annotation are assumed to be of type `any`

- **Optional Parameters:** `(age?: number)` -

  Indicate that a parameter is intentionally optional, otherwise TS throws an error if an argument is omitted.

- **Default Parameters:** `(name = "John")`

  If a parameter is assigned a default value, TS will infer the variable type of the default value's type.

- **Inferring Return Types:** based on the value after the return statement, TS infers the type for the return value.

- **Explicit Return Types:** `() : string => {}`

  TS will produce an error for any return statement that doesn't return the right type of value.

- **Void Return Type:** `() : void => {}`

  Recommended practice: when no returned value, use `void`

<br>

## Arrays

```js
// the numb array can only contain numbers
const numb: number[] = [1, 7];
```

```js
// Multi-dimensional Arrays
const letters: string[][] = [["a", "b"], []];
const numbers: number[][][] = [[[13]], [[27]]];
```

```js
// Tuples: array typed with elements of specific types
// Each value must match its type and index
const tuple: [string, number, boolean] = ["Hello", 25, true];
```

```js
// Rest Parameters & Spread Syntax
const friends: [string, string] = ["Robert", "John"];
const log = (...friends: string[]) => console.log(...friends);
log(...friends);
```

<br>

## Enums

**Enums:** enumerate and limit all the possible values that a variable can take.

```ts
enum Color {
  Red = 1,
  Green = 7,
  Blue = "BLUE",
}
```

Each member is assigned a numeric value by default, starting from 0. We can explicitly set the values of enum members to numeric or string values, like above. String Enums Convention: the string value should be just the capitalized form of the enum member.

```ts
const myColor: Color = Color.Green;
const blue: Color = Color.Blue;
const reverse: string = Color[myColor];
console.log(myColor, reverse, blue); // 2 'Green' 'BLUE'
```

Enums can be used in reverse, where you convert a numeric value to its corresponding enum member.

<br>
