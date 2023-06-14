[&larr; Back](./README.md)

# Custom Types

## Table of Content

- [Enums](#enums)
  - [Enums under the hood](#enums-under-the-hood)

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

### Enums under the hood

Under the hood, enum values are assigned a numerical value according to their listed order, starting with `0`.

```ts
petOnSale = Pet.Chinchilla;
petOnSale === 2; // true
```

Furthermore, we can reassign `petOnSale` to a number value, like `petOnSale = 0`, and it does not raise a type error.

We can change the starting number of the first enum value so the next enums will continue from that number, or even specify all numbers separately.

```ts
enum Pet {
  Hamster = 4,
  Rat = 7,
  Chinchilla = 3,
  Tarantula = 1,
}
```

<br>
