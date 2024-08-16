# Types in TypeScript

## Table of Contents

- [Type Inferences](#type-inferences)
- [Type Shapes](#type-shapes)
- [`any` type](#any-type)
- [Variable Type Annotations](#variable-type-annotations)

## Type Inferences

Type inference in TypeScript means that the language automatically determines the type of a variable based on the initial value assigned to it:

```ts
let score = 100; // TypeScript infers that score is of type 'number'
```

If you try to reassign a variable to a value of a different type, TypeScript will generate an error:

```ts
score = "A+";
// Error: Type 'string' is not assignable to type 'number'
```

## Type Shapes

The shape of an object in TypeScript refers to the set of properties and methods that the object has:

- TypeScript understands the shape of an object based on its type and will enforce this shape throughout your code.
- For example, since all strings have a `.length` property and a `.toLowerCase()` method, TypeScript will allow you to use these on any string:

```ts
let greeting: string = "Hello";
console.log(greeting.length); // 5
console.log(greeting.toLowerCase()); // "hello"
```

- If you try to access a property or method that doesn't exist on the object's type, TypeScript will log an error:

```ts
greeting.nonExistentMethod();
// Error: Property 'nonExistentMethod' does not exist on type 'string'.
```

## `any` type

When TypeScript cannot infer a type, it assigns the type `any` to the variable:

```ts
let something: any;
something = "Hello";
something = 42;
```

- The `any` type allows a variable to hold any type of value and disables type checking for that variable.
- However, using `any` should be done sparingly, as it removes the benefits of TypeScript's type safety.

## Variable Type Annotations

**Type Annotations** allow you to explicitly declare the type of a variable in TypeScript:

```ts
let age: number = 27;
```

- To annotate a variable, use a colon `:` followed by the type (`string`, `number`, `boolean`, `any`, etc.).
- Type annotations make your code more predictable and help TypeScript catch potential errors at compile time.
