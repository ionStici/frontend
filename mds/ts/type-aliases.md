# Type Aliases

## Table of Contents

- [What is a Type Alias?](#what-is-a-type-alias)
- [Union Types](#union-types)
- [Function Types](#function-types)
- [Object Types](#object-types)
- [Benefits of Type Aliases](#benefits-of-type-aliases)
- [Combine Type Aliases](#combine-type-aliases)

## What is a Type Alias?

**Type Alias:** create a new name for a type.

Type aliases are especially useful when we need a complex type to be reused in multiple places, or when we want to make our code more readable and maintainable.

We can create type aliases for various types, including unions, functions, objects, and more.

## Union Types

```ts
type StringOrNumber = string | number;
let id: StringOrNumber = "12345";
```

`StringOrNumber` is a type alias for a union type that can be either `string` or `number`.

## Function Types

```ts
type AddFn = (a: number, b: number) => number;
const calculate = (addFn: AddFn) => {};
```

`AddFn` is a type alias for a function type that takes two `number` arguments and returns a `number`.

## Object Types

```ts
type Person = { name: string; age: number; id: string | number };
const mie: Person = { name: "Mike", age: 21, id: 12345 };
```

`Person` is a type alias for an object type with specific properties (`name`, `age`, and `id`), where `id` can be a `string` or `number`.

## Benefits of Type Aliases

Type aliases are particularly useful when:

- **Reusability:** You need to use the same type in multiple places. Instead of repeating the type definition, you can define it once as an alias and use it wherever needed.
- **Readability:** Type aliases can make complex types easier to understand at a glance, improving the readability of your code.
- **Maintainability:** If you need to update a type, you only need to change the alias definition, and all instances where the alias is used will automatically reflect the change.

## Combine Type Aliases

```ts
type User = {
  name: string;
};

type Admin = {
  isAdmin: boolean;
};

type UserAdmin = User & Admin;

type Admins = UserAdmin[];

const admins: Admins = [{ name: "Mike", isAdmin: true }];
```

Type aliases are highly flexible, allowing for reuse and combination. For instance, you can define your type aliases in a separate file, export them, and then use them consistently across your project.
