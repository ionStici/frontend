[&larr; Back](./README.md)

# TypScript Code

## Table of Content

- []()
- [Functions](#functions)
- []()

<br>

##

```ts
const my_name: string = "John";
```

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
