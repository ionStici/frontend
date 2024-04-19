[&larr; Back](./README.md)

# Declarative and Functional JavaScript Principles

_Two fundamentally different ways (paradigms) of writing code in programming._

## Table of Content

- [Imperative Programming](#imperative-programming)
- [Declarative Programming](#declarative-programming)
- [Functional Programming](#functional-programming)

<br>

## Imperative Programming

**Imperative Code** explains exactly to the computer _HOW to do things_. We explain with code _every single step the computer needs to follow in order to achieve a certain result_. Step-by-step explanation.

```js
// Imperative Code Example
const arr = [4, 3, 5, 7];
const doubled = [];
for (let i = 0; i < arr.elngth; i++) doubled[i] = arr[i] * 2;
```

_Example:_ we tell the computer to create an empty array -> create a counter that starts at 0 -> increase that counter until we each the length of the original array -> store the new result in each new position of the new array (a lot of steps that we give to the computer in otder to achieve a result).

<br>

## Declarative Programming

**Declarative Code** - the programmer tells the computer only "WHAT to do". We simply _describe_ the way the computer should achieve a certain result. The HOW (step-by-step instructions) gets abstracted away.

```js
// Declarative Code Example
const arr = [4, 3, 5, 7];
const doubled = arr.map((n) => n * 2);
```

_Example:_ here we simply tell JS that it should map the values of an array to a new array. We just "describe" or "tell" WHAT to do, but no HOW to do it. The details about HOW to do have been abstracted away.

Declarative programming is a big and popular programming paradigm, which has given rise to a sub paradigm called **functional programming**.

<br>

## Functional Programming

**Functional Programming** is a _declarative programming paradigm_, based on the idea of writing software by combining multiple **pure functions**, avoiding **side effects** and **mutating** data.

**Side effect** - Modification (mutation) of any data **outside** of the function (mutating external variables, writing to DOM, etc.)

**Pure function** - Function without side effects. Does not depend on external variables. Given the same inputs, always returns the same outputs.

**Immutability** - State (data) is **never** modified. Insteadm state is copied and the copy is mutated and returned.

### Functional Programming Techniques

- We can mix imperative and declarative programming (we don’t have to go 100% declarative)
- Try to avoid data mutations as often as possible
- Use built-in methods that don't produce side effects
- Do data transformations with methods such as **map, filter, reduce**
- Try to avoid side effects in functions (not always possible)

### Declarative Syntax

- Use array and object destructuring
- Use the sprea operator `...`
- Use the ternary (conditional) operator
- Use template literals

These operators are about telling the code what to do, and not about the steps it should take.

<br>
