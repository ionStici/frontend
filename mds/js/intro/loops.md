[&larr; Back](./README.md)

# Loops

A **loop** is a programming tool and a fundamental aspect of every programming language.

Loops iterate or repeat an action (a set of instructions) until a specific condition if met. When the condition is met, the loop stops and the computer moves on to the next part of the program. _Iterate_ means to repeat.

Loops allow us to create efficient code that automates repetitive tasks, to make scalable, manageable programs.

<br>

## Table of Content

- [The For Loop](#the-for-loop)
- [Looping through Arrays](#looping-through-arrays)
- [Nested Loops](#nested-loops)
- [The While Loop](#the-while-loop)
- [do..while statement](#dowhile-statement)
- [break and continue statements](#break-and-continue-statements)
- [The for..of Loop](#the-forof-loop)

<br>

## The For Loop

```js
for (let i = 0; i < 5; i++) {
  console.log(i + 1); // 1 2 3 4 5 | 5 lines of code
}
```

The `for` loop contains 3 expressions separated by semicolons `;` inside the parentheses:

1. Declaring the iterator variable as a counter and assigning its initial value.

2. A _stopping condition_, evaluated before each iteration of the loop.

   If the condition is `true`, then the next iteration will run. If it evaluates to `false`, the loop stops.

3. An _iteration statement_ is used to update the iterator variable on each loop.

   Usually, increasing or decreasing the counter after each iteration.

After parentheses, we open curly braces, where we write the code that we want to be repeated.

We can use the iterator variable inside the loop. The first time, it is printed by its original value, then it is updated depending on the iteration.

If the stopping condition isn't met, then this will create an _infinite loop_.

<br>

## Looping through Arrays

```js
const arr = ["a", "b", "c"];

for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]); // a b c
}
```

- Convention: name the iterator variable `i`
- Think of `i` as the index of array elements
- Use the array's `length` to set the condition

### Looping Arrays Backwards

```js
const arr = ["a", "b", "c"];

for (let i = arr.length - 1; i >= 0; i--) {
  console.log(arr[i]); // c b a
}
```

<br>

## Nested Loops

A loop running inside another loop. Useful for comparing elements in two arrays.

For each round of the outer `for` loop, the inner `for` loop will run completely.

```js
const outerArr = [5, 10, 15];
const innerArr = [3, 5, 7];

for (let i = 0; i < outerArr.length; i++) {
  for (let i = 0; i < innerArr.length; i++) {
    if (outerArr[i] === innerArr[i]) {
      console.log(i); // 5
    }
  }
}
```

<br>

## The While Loop

Another type of loop.

```js
let i = 1;
while (i < 4) {
  console.log(i); // 1 2 3
  i++;
}
```

We still need the same components: the counter, a condition, increase or decrease the counter.

- The counter is declared in the global scope.
- Inside parentheses we specify only the stopping condition which evaluates before each iteration.
- Then, we have the loop's code block, which also makes sure to update the iterator varaible.

If we don't set the condition correctly, it could create an infinite loop.

Infinite loops can take up all of your computer's processing power potentially freezing the computer.

<br>

## do..while statement

The **do...while** will run at least once whether or not the condition evaluates to `true.`

```js
let str = "Hello";
let i = 0;

do {
  console.log(str);
  i++;
} while (i < 2);
```

1. First, the code block after the `do` keyword is executed once.
2. Then the condition is evaluated, and if the condition is `true` then the code block will execute again.
3. The looping stops when the condition evaluates to `false`.

<br>

## break and continue statements

- `continue` keyword is used to exit the current iteration, and continue to the next one.
- `break` keyword is used to completely terminate the whole loop.

```js
for (let i = 0; i < 5; i++) {
  if (i === 0) continue;
  if (i === 4) break;
}
```

<br>

## The for..of Loop

The **for..of** loop (ES6). Primary use case: iterating through the items of an array.

```js
const letters = ["a", "b", "c"];
for (const letter of letters) console.log(letter); // a b c
```

- `for..of` loop will iterate through the array and will give us access to the array items in each iteration.
- Inside parentheses we specify that we will iterate through the array `letters` and for each item `letter`.
- The variable `letter` is assigned a different value on each iteration of the loop.
- We can use the `for..of` loop on other iterables too, like strings or sets.
- We can use `break` and `continue` statements in `for..of` loops.

To get access to the current index and current item, call the `entries()` method on the array:

```js
for (const item of arr.entries()) console.log(item);
for (const [i, item] of arr.entries()) console.log(i, item);
console.log(...arr.entries()); // (2) [0, 'i'], (2) [1, 'love'], (2) [2, 'you']
```

<br>
