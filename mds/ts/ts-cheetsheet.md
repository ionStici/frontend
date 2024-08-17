# TypScript Refresher

## Table of Contents

- [Introduction](#introduction)
- [TypeScript Built-in Types](#typescript-built-in-types)
- [Functions](#functions)
- [Arrays](#arrays)
- [Object Type Annotation](#object-type-annotation)
- [Type Aliases](#type-aliases)
- [Function Types](#function-types)
- [Generic Types](#generic-types)
- [Generic Functions](#generic-functions)
- [Union Types](#union-types)

## Introduction

- TypeScript files extension: `main.ts`

- `tsc` command transpile TypeScript code to JavaScript code.

- `tsconfig.json` file specifies the compiler options required to transpile TypeScript.

- **Type Inferences:** when the type is not explicitly declared by the user, TypeScript will infer the type on its own.

- **Type Shapes:** an object's shape describes what properties and methods it does or doesn't contain.

- **Type `any`** : When TS isn't able to infer a type, it will consider the variable of type `any`

  Variables of type `any` can be reassigned to any value later on.

```ts
const my_name: string = "John";
```

- **Variable Type Annotation (declaration):** explicitly tell TS what type a variable is.

## TypeScript Built-in Types

### Primitive Types

_Basic JavaScript Data Types._

1. `number`: for numeric values
2. `string`: sequence of characters
3. `boolean`: true or false
4. `symbol`: represents a unique value
5. `BigInt`: for large integer values.

### Composite Types

_Types made up of other types._

1. **Object**: collection of key/value pairs
2. **Array**: collection of values of the same type
3. **Tuple**: collection of values of different types
4. **Enum**: represents a set of named constant values
5. **Union**: a value that can be of one of several types
6. **Intersection**: a type that combines two or more types
7. **Type Alias**: a custom type name
8. **Generic Type**: parameterized collections of types
9. Other: Function and Class

### Special Types

_Types with special meanings for TypeScript._

1. `any` - represents any type, for dynamic typing
2. `void` - represents a value that has no type
3. `never` - represents a value that never occurs
4. `unknown` - similar to `any`, but more restrictive
5. `null` - represents the absence of a value
6. `undefined` - represents a value that has not been assigned

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

- **Optional Parameters:** `(age?: number)`

  Indicate that a parameter is intentionally optional, otherwise TS throws an error if an argument is omitted.

- **Default Parameters:** `(name = "John")`

  If a parameter is assigned a default value, TS will infer the variable type of the default value's type.

- **Inferring Return Types:** based on the value after the return statement, TS infers the type for the return value.

- **Explicit Return Types:** `() : string => {}`

  TS will produce an error for any return statement that doesn't return the right type of value.

- **Void Return Type:** `() : void => {}`

  Recommended practice: when no returned value, use `void`

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

## Object Type Annotation

```ts
const person: { name: string; age: number } = { name: "John", age: 25 };
```

## Type Aliases

**Type Aliases** - define a custom name for a more complex type.

```ts
// simple string type
type str = string;
const sayHello: str = "Hello";
```

```ts
// object alias
type Point = { x: number; y: number };
let point: Point = { x: 10, y: 20 };
```

```ts
// Intersection Types with Type Aliases
type Person = { name: string };
type Employee = { employeeID: number };
type EmployeeData = Person & Employee;
let mike: EmployeeData;
```

## Function Types

Precisely control the argument and return types of a function.

```ts
type funcType = (arg0: string, arg1: string) => number;
let myFunc: funcType = (ar1, ar2) => ar1.length + ar2.length;
```

## Generic Types

**Generics** - create parameterized collections of types.

```ts
type Person<T, N> = {
  name: [T];
  age: [N];
};

const John: Person<string, number> = {
  name: ["John"],
  age: [25],
};
```

## Generic Functions

```ts
function multiply<T>(value: T, n: number): T[] {
  return Array(n).fill(value);
}
multiply("cheese", 3); // (3) ['cheese', 'cheese', 'cheese']
```

The `value` argument and the returned array will have the same type `T`

## Union Types

**Union** - define multiple types that a value can take.

```ts
let id: string | number = 1;
id = "001";
```

`string | number` is a union that allows `id` to be a `string` or a `number`.

Unions make the code more flexible, but at the same time more specific than the `any` type.

Unions can be used anywhere a type value is defined, including function parameters:

```ts
function getMargin(margin: string | number) {}
```

### Unions for Arrays

```ts
const seven: (string | number)[] = [7, "7"];
```

### Unions with Literal Types

**Literal Type Unions** - specific (literal) values that a variable or parameter can take.

Literal type unions provide precise type definition, make our intentions explicit, less errors.

```ts
type Color = "Green" | "Yellow" | "Red";
function changeLight(color: Color) {}
```

Here, the `color` parameter can only take one of the 3 specified string literals.
