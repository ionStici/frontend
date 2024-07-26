[&larr; Back](./README.md)

# Objects

## Table of Contents

- [Object Literals](#object-literals)
- [Accessing Properties](#accessing-properties)
  - [Dot Notation](#dot-notation)
  - [Bracket Notation](#bracket-notation)
  - [Differences](#differences)
- [Property Assignment](#property-assignment)
  - [delete operator](#delete-operator)
- [Methods](#methods)
- [Nested Objects](#nested-objects)
- [Pass By Reference](#pass-by-reference)
- [Looping Through Objects with for...in](#looping-through-objects-with-forin)

<br>

## Object Literals

We use curly braces `{}` to designate an object literal.

Then, we assign our object to a variable `const obj = {}`

Objects are organized into key-value pairs, called properties.

A key is like a variable name that points to the location in memory that holds a value.

The key's value can be of any data type, even other objects, or any expression, including function.

```js
const myObj = {
  firstName: "John",
  age: 2030 - 1995,
  friends: ["Irina", "You"],
};
```

- First the key's name followed by a colon and then the value.
- We separate properties with a comma.

Keys are strings, but when we have a key that does not have any special characters in it, JavaScript allows us to omit the quotation marks.

Objects contain unordered data, the order of properties does not matter, we reference to properites by its key.

If we log the object we see that the properties are ordered alphabetically.

Arrays for ordered data. Objects for unstructured and named data.

**Note:** the curly braces from an object is not a code block, it does not create its scope. Instead, it's just a way that we define objects (object literals). So all the code from curly braces from the object is in the global scope.

<br>

## Accessing Properties

Two ways to access object properties: Dot notation and Bracket notation.

### Dot Notation

To access an object property using the dot notation:

```js
myObj.age; // 15
```

Object name + dot operator + the property name (key).

If we try to access a property that does not exist, `undefined` will be returned.

### Bracket Notation

```js
myObj["firstName"]; // ohn
```

Inside bracket, we pass in the property name (key) as a string.

### Differences

In bracket notation we can put any expression, for example we can compute the property name based on input user data.

Besides this, we must use bracket notation when accessing keys that have numbers, spaces, or special characters in them.

Another use case, we can use variables inside bracket notation (helpful when working with functions and parameters).

Without bracket notation in these situations, our code would throw an error.

```js
const obj = {
  "key 1": "Hello",
  data: "empty",
};

obj["key 1"];
obj["da" + "ta"];
```

_Recommendation:_ Use dot notation by default, and bracket notation when you need to compute the property name.

<br>

## Property Assignment

Add and change object properties (with both dot and bracket notation):

- If the property name already exists: the value will be replaced with the newly assigned value.
- If there was no property with that name: a new property will be added to the object.

```js
myObj.job = "Software Engineer";
myObj["hobby"] = "Reading";
```

_Note:_ Like arrays, even if we can't completely reassign an object declared with const, we can still add or change properties.

### delete operator

```js
delete myObj.hobby;
```

We can delete a property from an object with the `delete` operator.

<br>

## Methods

Any function attached to an object is called a **method**.

Example: `console` is a global object, and `.log()` is a method on that object.

In objects we can use only function expressions.

```js
const myObj = {
  funcName: function () {
    console.log("I am a method");
  },

  newFunction() {
    console.log("New method syntax");
  },
};

myObj.funcName();
myObj["newFunction"]();
```

When writing methods, the key serves as the method's name, and the value is an anonymous function expression.

With the new method syntax introduced in ES6 we can omit the colon and the `function` keyword.

Object methods are invoked by appending the object’s name with the dot operator followed by the method name and parentheses.

<br>

## Nested Objects

We can nest objects inside objects inside other objects and so on.

To access nested properties, we chain operators.

```js
const myObj = {
  nestedObj: {
    "third-object": { chooseMe: ":P" },
  },
};

myObj.nestedObj["third-object"].chooseMe; // :P
```

The chain is evaluated from left to right.

So, first `myObj.nestedObj` returns the value it contains and only then the next chain is evaluated.

<br>

## Pass By Reference

Objects are _passed by reference_. This means: when we pass an object into a function as an argument, JavaScript interprets the parameter name as pointing to the space in memory holding that object. As a result, functions which change object properties actually mutate the object permanently.

However, reassigning an object inside a function body passed as an argument would not work. Even though the object was declared with let and even though we can reassign the object outside of the function body. The reassignment kind of worked inside the function, because if we log the object right after reassignment, we see the new object, but if we log the object outside the function then the object still contains the previous properties.

So, when we pass the object as argument inside the function, then that variable which received the object, became a reference to the memory location of the object (it is a variable in its own right), but not to the initial object identifier (the body function has now knowledge of the object identifier).

And when we did the reassignment in the body of the function, the variable from the function came to refer to the memory location of the object, while the object identifoer was completely unchanegd from its earlier value.

<br>

## Looping Through Objects with for...in

Iterating through objects using the [`for...in`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) loop.

`for...in` will execute a given block of code for each property in an object.

```js
let friends = {
  iri: {
    name: "Irina",
  },

  andr: {
    name: "andrew",
  },
};

for (let friend in friends) {
  console.log(friend); // iri andr
  console.log(friends[friend].name); // irina andrew
}
```

In each iteration, the variable `friend` is set to one of the keys of the `friends` object.

<br>
