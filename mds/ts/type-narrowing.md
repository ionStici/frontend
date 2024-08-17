# Type Narrowing

- [What is Type Narrowing?](#what-is-type-narrowing)
- [Type Guards](#type-guards)
- [Using `in` with Type Guards](#using-in-with-type-guards)
- [Narrowing with `else`](#narrowing-with-else)
- [Narrowing After a Type Guard](#narrowing-after-a-type-guard)
- [Shared Methods and Properties](#shared-methods-and-properties)

## What is Type Narrowing?

**Type Narrowing** is when TypeScript can infer a type based on the variable's surrounding code, allowing you to write type-safe code that handles different types appropriately.

## Type Guards

TypeScript can narrow a type using **type guards**, which are conditionals that check if a variable is a specific type. One common type guard is the `typeof` operator:

```ts
function getWidth(width: string | number) {
  if (typeof margin === "string") {
    // ...
  }
  if (typeof margin === "number") {
    // ...
  }
}
```

- **Type Narrowing:** TypeScript infers that `width` can be either a `string` or a `number` based on the `if` block in which the code will run.

- **TypeScript** recognizes `typeof` as a type guard for `string`, `number`, `boolean`, and `symbol`.

_p.s._ TypeScript is able to infer types in many convenient situations. A great example is a function's return type. TypeScript will look at the contents of a function and infer which types the function can return. If there are multiple possible return types, TypeScript will infer the return type as a union.

## Using `in` with Type Guards

The [`in` operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in) checks if a property exists on an object, which TypeScript recognizes as a type guard:

```ts
type Tennis = {
  serve: () => void;
};

type Soccer = {
  kick: () => void;
};

function play(sport: Tennis | Soccer) {
  if ("serve" in sport) {
    return sport.serve();
  }
  if ("kick" in sport) {
    return sport.kick();
  }
}
```

TypeScript narrows the type of `sport` based on whether the `serve` or `kick` property exists, allowing the appropriate method to be called.

## Narrowing with `else`

TypeScript can also narrow types using the `else` block as the opposite of the `if` condition:

```ts
function formatPadding(padding: string | number) {
  if (typeof padding === "string") {
    return padding.toLowerCase(); // padding is string
  } else {
    return `${padding}px`; // padding is number
  }
}
```

The type guard `typeof padding === 'string'` tells TypeScript that `padding` within the `if` statement’s block must be a string. Going further, TypeScript is also able to infer that, since the `padding` argument is typed as the union `string | number`, then `padding` must be a `number` type within the `else` block.

## Narrowing After a Type Guard

```ts
type Tea = {
  steep: () => string;
};

type Coffee = {
  pourOver: () => string;
};

function brew(beverage: Coffee | Tea) {
  if ("steep" in beverage) {
    return beverage.steep();
  }

  return beverage.pourOver();
}
```

If the conditional is true, we immediately return `beverage.steep()` and the function execution stops. If not, TypeScript infers that the remaining code must be of type `Coffee` because `Tea` has already been handled.

## Shared Methods and Properties

When working with union types, TypeScript allows you to access only the properties or methods that are common to all types in the union unless you use type narrowing to refine the type:

```ts
function printStatus(status: boolean | number) {
  console.log(status.toString()); // Both boolean and number have toString()

  if (typeof status === "number") {
    console.log(status.toFixed(2)); // status is narrowed to number here
  }
}
```

- **Without Narrowing:** Only shared methods like `toString()` can be called directly.

- **With Narrowing:** TypeScript allows access to methods specific to the narrowed type (e.g., `toFixed()` on a `number`).
