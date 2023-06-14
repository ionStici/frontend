[&larr; Back](./README.md)

# Custom Types

## Table of Content

- [Enums](#enums)

<br>

## Enums

We use **enums** when we’d like to enumerate all the possible values that a variable could have, or in other words, to limit the possible values of a variable.

For example, a variable of the `string` type can have any string as a value, there are infinitely many possible strings, and it would be impossible to list them all.

```ts
enum Pet {
  Hamster,
  Rat,
  Chinchilla,
  Tarantula,
}

const petOnSale: Pet;
petOnSale = Pet.Chinchilla;
petOnSale = Pet.Snake; // error
```

Above, we define the enum `Pet`, representing four animals. Any other values, are not allowed.

Then, our enum type is used in type annotation like any other type.

```ts
const orders: [Pet, number][] = [
  [Pet.Rat, 2],
  [Pet.Chinchilla, 1],
  [Pet.Hamster, 2],
  [Pet.Chinchilla, 50],
];
```

<br>

<!-- ### Enums under the hood -->
