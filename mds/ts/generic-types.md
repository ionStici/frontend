# Generic Types in TypeScript

## Table of Contents

- [What are Generics?](#what-are-generics)
- [Example: Generic Types](#example-generic-types)
- [Creating Your Own Generic Types](#creating-your-own-generic-types)
- [Generic Functions](#generic-functions)

## What are Generics?

Generics in TypeScript allow you to create reusable, flexible types and functions that work with any data type. They are parameterized by one or more type variables, which can be replaced with specific types when the generic type or function is used.

## Example: Generic Types

A common example of a generic type is `Array<T>`, where `T` is a placeholder for any type:

```ts
let numbers: Array<number> = [1, 2, 3];
```

## Creating Your Own Generic Types

You can define your own generic types to create flexible collections of object types:

```ts
type User<T, U> = {
  name: T;
  id: T | U;
  hobbies: T[];
};

const mike: User<string, number> = {
  name: "Mike",
  id: 123,
  hobbies: ["Coding", "Robotics"],
};
```

- `User` in a generic type where `T` and `U` are placeholders for any type.

- When creating a `User<string, number>`, the `T` and `U` are replaced with `string` and `number`, ensuring type safety across the object.

### How It Works

- Writing generic types using t`ype TypeName<T>` allows `T` to be used as a type placeholder within the type definition.
- When you use the generic type, `T` is substituted with the specific type you provide.

## Generic Functions

Generic functions allow you to write functions that can operate on any type while still preserving type safety.

Here's a function that returns an array filled with a certain value:

```ts
function getFilledArray<T>(value: T, n: number): T[] {
  return Array(n).fill(value);
}

getFilledArray<string>("cheese", 3); // ["cheese", "cheese", "cheese"]
```

- `getFilledArray<T>` is a generic function where `T` is a placeholder for any type.
- The function ensures that the type of `value` and the elements of the returned array are consistent.

### How It Works

- Writing generic functions with `function functionName<T>()` allows `T` to be used as a type placeholder within the function's type annotations.
- When the function is invoked, `T` is replaced with the specific type provided by the caller.
