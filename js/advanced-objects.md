[&larr; Back](./README.md)

# Advanced Objects

## Table of Content

- [The `this` keyword](#the-this-keyword)
- [Privacy](#privacy)
- [Getters and Setters](#getters-and-setters)
- [Factory Functions](#factory-functions)
- [Built-in Object Methods](#built-in-object-methods)
- [Enhanced Object Literals](#enhanced-object-literals)
- [Looping Objects: Keys, Values, Entries](#looping-objects-keys-values-entries)

<br>

## The `this` keyword

Objects are collections of related data and functionality. We store that functionality in methods on our objects.

```js
const obj = {
  name: "Mike",

  sayHello() {
    console.log(`Hello ${this.name}`); // Hello Mike
  },
};
```

By using `this` inside a method, we ca access the object itself and its properties.

The `this` keyword is equal (references) to the object from which the method is called.

We can use the `this` keyword to declare new key - value pairs.

**Note:** Arrow functions (methods) does not have a `this` keyword, it will point to the global object.

<br>

## Privacy

The concept of privacy in objects refers to the idea that ONLY certain properties should be allowed to change.

Certain languages have privacy built-in for objects, but JavaScript don't.

JavaScript developers follow naming conventions that signal to other developers how to interact with a property.

One common convention is to place an underscore `_` before the name of a property to mean that the property should not be directly manipulated.

```js
{
  _birthYear: 2010;
}
```

<br>

## Getters and Setters

Objects can have [getter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get) and [setter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set) properties.

- Getters are methods that return properties of an object.
- Setters are methods that reassign values of existing properties within an object.

<div></div>

- We call these special properties: _assessor properties_.
- While the more normal properties are called: _data properties_.

```js
const obj = {
  _fullName: "Mike",
  _birthYear: 1995,
  currentYear: 2025,

  get age() {
    return 2025 - this._birthYear;
  },

  set fullName(name) {
    this._fullName = name;
  },
};

obj.age; // 30
obj.fullName = "Mike Raven";
```

To add a getter or setter to an object, we prepend the keyword `get` or `set` to a method.

- Getter methods do not need to be called with parentheses. Syntactically, it looks like we're accessing a property. Useful when we want to read something as a property, but still need to do some calculations before.

- Setter methods do not need to be called with parentheses. It looks like we're reassigning a value of a property. Any setter method needs to have exactly one parameter, which we need to pass in.

Don't name the getters / setters methods with the same name as properties. If we do so, then calling the method will result in an infinite call stack error. Workaround convention: use an underscore when calling properties.

<br>

## Factory Functions

A factory function is a function that:

- Can return a new object.
- Can be reused to make multiple object instances.

```js
const person = (name, birthYear, job) => {
  return {
    name: name,
    birthYear: birthYear,
    job: job,

    set age(currentYear) {
      this._age = currentYear - this.birthYear;
    },
  };
};

const mike = person("Mike", 1995, "Dev");
mike.age = 2025;
```

We call the factory faction with the necessary arguments and assign the return value of the function to a variable that will become the new object.

<br>

## Built-in Object Methods

Check out the documentation: [Object MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

<br>

## Enhanced Object Literals

ES6 introduced three new ways which makes easier to write object literals.

### Passing an object into another object

```js
const obj = {
  // ...
};

const complexObj = {
  // before ES6
  obj: obj,

  // ES6 enhanced object literals
  obj,
};
```

Enhanced object literals creates a property name with exactly the variable name we pass in.

### We can compute property names

```js
const obj = {
  [player[0]]: "",
  [`player-${2 + 3}`]: "",
};
```

In square brackets we can put any expression.

### Simpler methods syntax

```js
const obj = {
  // before ES6
  oldSyntax: function () {
    // ...
  },

  // ES6
  newSyntax() {
    // ...
  },
};
```

With the new method syntax introduced in ES6 we can omit the colon and the `function` keyword.

<br>

## Looping Objects: Keys, Values, Entries

Objects are not iterables, but we can loop over them in an indirect way.

Depending on what exactly we want to loop over, we have different options:

1. Property names: `Object.keys()`
2. Property values: `Object.values()`
3. The entire object: `Object.entries()`

### Object.keys()

```js
const obj = {};
const properties = Object.keys(obj);
```

Due to `Object.keys()` method, `properties` variable is now an array which contains only the property names of the `obj` object. Now we can loop over `properties` like a simple array.

### Object.values()

```js
const values = Object.values(obj);
for (const item of values)
```

It works exactly the same, but now with `Object.values()` we have an array with only the object values.

### Object.entries()

```js
const entries = Object.entries(obj);
console.log(entries); // 0: (2) ['key', 'value'] for each key / value pair
```

With `Object.entries()` we get an array with arrays for each key / value pair.

```js
for (const [key, value] of entries)
```
