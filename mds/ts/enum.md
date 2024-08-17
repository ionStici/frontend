# Enums in TypeScript

## What are Enums?

Enums allow us to define a set of named constants that limit the possible values a variable can have.

```ts
enum Pet {
  Hamster,
  Rat,
  Chinchilla,
  Tarantula,
}

let petOnSale: Pet;

petOnSale = Pet.Chinchilla; // Valid
petOnSale = Pet.Snake; // Error: 'Snake' is not a member of 'Pet'
```

- The `Pet` enum defines four possible values.
- Variables of type `Pet` can only be assigned these values.

Enums can be used in type annotations like any other type:

```ts
const orders: [Pet, number][] = [
  [Pet.Rat, 2],
  [Pet.Chinchilla, 1],
  [Pet.Hamster, 2],
  [Pet.Chinchilla, 50],
];
```

## Enums Under the Hood

By default, enum values are assigned numeric values based on their order, starting at `0`.

```ts
petOnSale = Pet.Chinchilla;
petOnSale === 2; // true
```

Enum members can be reassigned to their corresponding numeric values, like `petOnSale = 0`.

You can customize the numeric values:

```ts
enum Pet {
  Hamster = 4,
  Rat = 7,
  Chinchilla = 3,
  Tarantula = 1,
}
```

This type of enum is called a **numeric enum**.

## String Enums vs. Numeric Enums

TypeScript also supports string enums, where each enum value is explicitly assigned a string:

```ts
enum DirectionNumber {
  North,
  South,
  East,
  West,
}

enum DirectionString {
  North = "NORTH",
  South = "SOUTH",
  East = "EAST",
  West = "WEST",
}
```

- **Numeric Enums:** Numbers can be assigned automatically, but arbitrary numbers can be assigned directly.
- **String Enums:** Strings must be explicitly assigned, which provides more strict type checking.

**Best Practice:** Prefer string enums for stricter type safety.
