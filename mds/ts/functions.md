# Functions in TypeScript

## Table of Contents

- [Parameter Type Annotations](#parameter-type-annotations)
- [Optional Parameters](#optional-parameters)
- [Default Parameters](#default-parameters)
- [Inferring Return Types](#inferring-return-types)
- [Explicit Return Types](#explicit-return-types)
- [`void` Return Type](#void-return-type)
- [Functions as Parameters](#functions-as-parameters)

## Parameter Type Annotations

Specify the types of function parameters by placing a type annotation after the parameter name:

```ts
const sayHello = (name: string) => console.log(`Hello ${name}`);
```

If a parameters does not have a type annotation, TypeScript assumes it to be of type `any`, similar to how it handles variables.

## Optional Parameters

TypeScript returns an error if we don't provide a value for all the arguments the function expects. To indicate that a parameter is intentionally optional, append a `?` after the parameter name:

```ts
const sayHello = (name?: string) => console.log(`Hello ${name}`);
```

This tells TypeScript that the parameter may be `undefined` and doesn’t always need to be provided.

## Default Parameters

When a parameter has a default value, TypeScript infers its type from that default value:

```ts
const sayHello = (name = "John") => console.log(`Hello ${name}`);
```

- The `name` parameter is inferred to be of type `string | undefined`.
- Default parameters are considered optional, so there's no need to use `?` after their name.

## Inferring Return Types

TypeScript automatically infers the return type of a function based on the value returned:

```ts
const sayHello = () => "Hello";
const myVar = sayHello(); // TypeScript infers myVar as 'string'
```

The return type is inferred from the expression following the `return` keyword.

## Explicit Return Types

You can explicitly specify the return type of a function by adding a type annotation after the closing parenthesis:

```ts
const sayHello = (name: string): string => `Hello ${name}`;
```

If a function returns a value of a different type than the one specified, TypeScript will produce an error.

## `void` Return Type

Even when a function doesn’t return a value, it’s a good practice to annotate the return type as `void`:

```ts
const sayHello = (name: string): void => console.log(`Hello ${name}`);
```

The `void` type indicates that the function does not return any value.

## Functions as Parameters

You can pass functions as parameters to other functions and annotate them with the expected parameter and return types:

```ts
const chitChat = (name: string, sayHello: (name: string) => string): string => {
  return `${sayHello(name)}. How are you?`;
};
```

**Syntax:** Use arrow notation to define the argument types and return type.
