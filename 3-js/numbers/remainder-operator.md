[&larr; Back](./README.md)

# Remainder Operator

The remainder operator `%` returns the remainder left over when one operand is divided by a second operand.

```js
15 % 4; //3
5 % 2; // 1
8 % 3; // 2
6 % 2; // 0
7 % 2; // 1
```

### Even or Odd

_Check if a certain number is even or odd:_

```js
let n = 101;
n % 2 === 0 ? "Even" : "Odd"; // "Odd"
```

### Check for equal division

Whenever the result of the remainder operator is zero, then that means that the first number is completely divisble by the second one. Important to know in programming.

### Checking each third element

```js
if (n % 3 === 0) console.log("Third");
```

When you need to do something every Nth time.

<br>
