[&larr; Back](./README.md)

# Advanced Objects

## Table of Content

- [The `this` keyword](#the-this-keyword)
- [Privacy](#privacy)
- [Getters and Setters](#getters-and-setters)
- [Factory Functions](#factory-functions)

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

<!-- ## Enhanced Object Literals

We can use a destructuring technique, called _property value shorthand_ (ES6), so all we have to do

How we write functions

<br>

## Built-in Object Methods

Check out the documentation: [Object MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) -->
