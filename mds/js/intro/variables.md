# Variables

## Table of Content

- [Values and Variables](#values-and-variables)
- [Type Conversion and Type Coercion](#type-conversion-and-type-coercion)
- [let, const, var](#let-const-var)
- [Mathematical Assignment Operators](#mathematical-assignment-operators)
- [The Increment and Decrement Assignment Operator](#the-increment-and-decrement-assignment-operators)

<br>

## Values and Variables

In programming, a value is the fundamental unit of data, like `23`, `true`, or `'Hello'`.

Variables are used to label and store data (values) in the computer's memory.

After creating a variable, we can: store or update data, reference for data.

```js
let firstName = 'John'; // declaring a variable
```

1. To create or declare a new variable, we use one of the keywords: `let` `const` `var`
2. `firstName` is the variable's name that we gave.
3. `=` is the _assignment operator_. In this case, it assigns a value to a variable.
4. `"John"` is the value assigned to the variable `firstName`.

<details>
<summary>Rules for naming variables</summary>

<br>

- Cannot start with a number.

<div></div>

- Can only contain: letters, numbers, dollar sign, underscore.

<div></div>

- Variable names are case sensitive.

<div></div>

- Don't use reserved JS keywords.

</details>

<br>

**Naming Convention:** Use the _camelCase_ technique and descriptive names for naming variables.

_Other conventions:_ First letter in uppercase: OOP. All letters in uppercase: for constants.

**Note:** Variables are not the same as values. Variables contain values and represent them with a name.

<br>

## Type Conversion and Type Coercion

_Converting between types_

### Type Conversion

**Type Conversion** is when we manually convert from one type to another. Functions:

```js
Number('1922'); // 1922 | converting strings to numbers
String(1922); // "1922" | converting numbers to strings
Boolean('Hi'); // true |
```

Usually when we receive input from the user, it get it as a string, to process it, we can use type conversion in case we need.

If we're trying to convert something to a number that is impossible to convert, an actual string for example, we will get the value of `NaN` which stands for _Not a Number_. JavaScript returns `NaN` whenever an operation that involves numbers fails to produce a new number, referring to _invalid number_. In case we check, we see that `typeof NaN` is `number`, a number but an invalid one.

_Note:_ `-1` is a standard in programming, a number that shows us clearly that this has no meaning.

JavaScript only converts to 3 types: number, string, boolean. However, in practice we rarely have to do it manually, because JavaScript does type coercion automatically for us in many situations.

### Type Coercion

**Type Coercion** is when JS automatically converts types behind the scenes for us.

Type coercion happens whenever an operator is dealing with two values that have different types. In this case, JS will convert one of the values to match the other value, so in the end the operation can be executed.

_Type Coercion:_

- **`+`** converts to _Strings_
- **`-`** converts to _Numbers_
- **`*`** converts to _Numbers_
- **`/`** converts to _Numbers_
- **`>`** converts to _Numbers_

```js
'23' > '18'; // true | strings were converted to numbers then the comparison was made
'23' + 47; // 2347 | string concatenation, 47 was converted into string
'5' * 3; // 15 | "5" string was converted into number
```

If JS would not have automatic type coercion, like many other languages don't, then we would have to manually do this.

## Dynamic Typing

When we create a new variable, we do not have to manually define the data type that it contains, JavaScript automatically determines the data type of the value from that variable. Later in our code, we can reassign a new value with a different data type to the same variable, which also happens automatically by JS.

<br>

## let, const, var

Use `const` by default, and `let` only when you need to update the variable.

### let

`let` keyword is used to declare variables that can be reassigned later.

```js
let myName = 'John';

let age;
age = '25';
let x, y, z;
```

We can declare a empty variable, so without assigning a value. In this case, the variable will be automatically initialized with `undefined` as value. But later we can reassign a value to that empty variable. Besides this, we can declare multiple empty variables at once.

### const

`const` is used to declare immutable variables.

We cannot reassgin a const variable, it is a constant.

```js
const myName = "John";

const age; // SyntaxError
const myName = 'Superman';  // TypeError
```

- If we try to reassign a `const` variable, we will get a `TypeError`.
- And if we try to declare a empty `const` variable, we will get a `SyntaxError`.

### var

`var` is the old way of declaring variables, it works similar to `let` with some differences.

In modern JavaScript, `var` should be completely avoided.

<br>

## Mathematical Assignment Operators

The most straightforward assignment operator is just the equal sign `=`

Additionally, JavaScript has _built-in mathematical assignment operators_

```js
let x = 5;
x = x + 2; // 7

x += 1; // 8
x -= 2; // 6
x *= 2; // 12
2 /= 3; // 4
```

The mathematical assignment operator: performs the mathematical operation of the first operator using the number to the right, then reassigning `x` variable to the computed value.

<br>

## The Increment and Decrement Assignment Operators

- _The increment operator_ `++`
- _The decrement operator_ `--`

These operators, will increase or decrease the value of the variable by `1`.

```js
let x = 10;

x++; // 11 | x = x + 1;
x--; // 10 | x = x - 1;
```

Prefixed increment and decrement operators:

```js
let a = 10; // 10
++a; // 11
a++; // 11
a; // 12
```

The prefixed operator will assign the value to the variable immediatly on exactly that line of code.

<br>
