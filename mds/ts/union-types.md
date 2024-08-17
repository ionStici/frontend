# Union Types

## Introduction

**Union Types** allow you to combine different types into a single union.

```ts
let id: string | number;
id = 1; // Valid
id = "001"; // Valid
```

- The `string | number` union allows `id` to be either a `string` or a `number`, providing more flexibility than a single type, but more specificity than `any`.
- Unions can be written anywhere a type is expected, including function parameters.

## Unions and Arrays

To define an array that can hold multiple types, wrap the union in parentheses, and then use array notation, for example: `(string | number)[]`.

```ts
const timesList: (string | number)[] = [
  new Date().getTime(), // number
  new Date().toString(), // string
];
```

## Unions with Literal Types

Literal types allow you to specify that a variable can only take one of a specific set of values:

```ts
type Color = "green" | "yellow" | "red";

function changeLight(color: Color) {
  // ...
}
```

`color` can only be `"green"`, `"yellow"`, or `"red"`. Any other value will result in a TypeScript error.
