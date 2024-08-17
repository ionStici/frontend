# Object Type Annotation

You can define the shape of an object by specifying the types of its properties:

```ts
let person: {
  name: string;
  age: number;
  isAdmin: Boolean;
  id: string | number;
};

person = {
  name: "John",
  age: 25,
  isAdmin: true,
  id: "12345",
};
```

- The `person` object must have `name`, `age`, `isAdmin`, and `id` properties with the specified types.
- TypeScript enforces the shape and types, leading to a type error if they don’t match.

TypeScript allows object properties to be of any type, including enums, arrays, and other objects.
