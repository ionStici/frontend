# Arrays in TypeScript

## Table of Contents

- [Rest and Spread Operators](#rest-and-spread-operators)
- [Array Type Inference](#array-type-annotations)
- [Tuples](#tuples)
- [Multi-dimensional arrays](#multi-dimensional-arrays)
- [Array Type Annotations](#array-type-annotations)

## Array Type Annotations

In TypeScript, you can define the type of elements that an array can contain:

```ts
const grades: number[] = [1, 2, 3];
const friends: Array<string> = ["Robert", "Andrew"];
```

- The `grades` array can only contain numbers.
- The `friends` array can only contain strings.

## Multi-dimensional arrays

Multi-dimensional arrays: arrays of arrays of arrays.

```ts
const numbers: number[] = [1, 2, 3];
const moreNumbers: number[][] = [numbers, 4, 5];
const letters: string[][][] = ["a", ["b"], [["c"]]];
```

## Tuples

Tuples are arrays with a fixed number of elements, where each element can have a different type:

```ts
let myTuple: [string, number, boolean, any] = ["Hello", 7, true, null];
```

- Tuples require explicit type annotations.
- Each value in a tuple must match its specified type and position (index).
- Tuples have a fixed length, and TypeScript will enforce this.

## Array Type Inference

If you don't provide an explicit type annotation, TypeScript will infer the array's type based on the initial values:

```ts
let arr = [true, true, false];
arr[3] = true; // expanding
```

- In this example, `arr` is inferred to be of type `boolean[]`.

## Rest and Spread Operators

Rest parameters in functions can be typed similarly to arrays:

```ts
let words: string[] = ["Hello", "World"];
const merge = (...words: string[]): void => console.log(...words);
merge(...words);
```

The `words` parameter is treated as an array of strings.
