[&larr; Back](./README.md)

# Arrays

<br>

## Array Type Annotations

```ts
const nums: number[] = [1, 2, 3];
const onOff: boolean[] = [true, true, false];
const friends: Array<string> = ["Robert", "Andrew"];
```

The `nums` array can only contain numbers, `onOff` only booleans, and `friends` only strings.

<br>

## Multi-dimensional Arrays

We can declare multidimensional arrays: arrays of arrays of arrays (of some type).

```ts
const numbers: number[] = [1, 2, 3];
const multiNumbers: number[][] = [nums, 4, 5];
const letters: string[][][] = ["a", ["b"], [["c"]]];
```

<br>

## Tuples

Arrays with elements of different types.

```ts
let ourTuple: [string, number, string, boolean] = ["Hello", 7, "World", false];
```

In TypeScript, when an array is typed with elements of specific types, it’s called a **tuple**.

Tuple types specify both the lengths and the orders of compatible tuples, and will cause an error if either of these conditions are not met, so each value must match its type and index.

When we want tuples, we need to use explicit type annotations. Tuples have fixed lengths.

<br>

## Array Type Inference

<br>
