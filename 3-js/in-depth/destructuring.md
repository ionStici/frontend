[&larr; Back](./README.md)

# Destructuring

**Destructuring** (ES6) is a JS feature - to extract data from arrays or objects.

## Table of Content

- [Destructuring Arrays](#destructuring-arrays)
- [Destructuring Objects](#destructuring-objects)
- [Destructuring Function Parameters](#destructuring-function-parameters)

<br>

## Destructuring Arrays

Retrieve elements from an array and store them into variables.

Destructuring follows the array order of the elements.

```JS
const secondArr = [6, 7];
const arr = [1, 2, 3, [4, 5], secondArr];

const [a, b] = arr;  // a = 1, b = 2
// destructuring the first 2 elements

const [a, b] = arr.secondArr;  // a = 6, b = 7
// destructuring an array within another array

const [a, , c] = arr;  // a = 1, c = 3
// skipping elements with commas

const [,,, [d, e]] = arr;  // d = 4, e = 5
// nested destructuring

const  [ a=1, b=2] = arr;
// default values
```

<br>

## Destructuring Objects

Using Object Destructuring, we can create new variables directly from object's properties.

We access the values by matching the variable names to the property names, the order doesn't matter in objects.

The destructured key / value pairs become individual variables.

```JS
const { job, age } = user;  // job = programmer, age = 35
// destructuring job and age variables from user objects

const { job: hobby } = user;
// renaming variable names

const { job: hobby = "programmer" } = user;
// default values

const { innerObj: { friends } } = user;
// nested destructuring

let a = 5;  let b = 7;
( {a, b} = user; );
// mutating existing variables with destructuring

```

<br>

## Destructuring Function Parameters

Destructuring - Function returning an array

```JS
const obj = { method() { return [4, 5] } };

const [par1, par2] = obj.method(); // par1 = 4, par2 = 5

// A function returns an array, and then we destruct the result into  variables
```

<br>

Using destructuring for function arguments to capture specific properties as named parameters:

```JS
let myObj = {
    job: 'programmer'
}

const whoAreYou = function ( { job } ) {
    console.log(`I am a ${job}`);
}

whoAreYou(myObj);  // 'I am a programmer'
```
