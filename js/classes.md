[&larr; Back](./README.md)

# Classes

<details>
<summary>Additional Details</summary>

<br>

Classes in JavaScript don't work like traditional classes, they're just syntactic sugar over OOP. Behind the scenes, classes work as contructor functions implementing prototypal inheritance, but using a nicer and more modern syntax.

<div></div>

Just like in functions, we have class declaration and class expression, because in fact classes are just a special type of functions.

<div></div>

```js
// class expression
class PersonCl = {}

// class declaration
class PersonCl {}
```

<div></div>

A class acts like any other regular constructor function, the only difference is in the syntax. Classes hides the true nature of prototypal inheritance in JavaScript.

</details>

<br>

## Table of Content

- [ES6 Classes](#es6-classes)
  - [Defining a Class](#defining-a-class)
  - [Creating a Class Instance](#creating-a-class-instance)
  - [Methods](#methods)

<br>

## ES6 Classes

[MDN Documentation: JavaScript Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

JavaScript is an _object-oriented programming_ (OOP) language.

### Defining a Class

```js
class PersonCl {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
```

- The `class` keyword -> The name of the class -> Curly braces.
- Convention: capitalize and CamelCase class names.
- The `constructor()` method of the class will be called every time we create a new instance of a class.
- We pass in this `constructor()` method arguments for the properties we want the object to have.
- In the context of a class, `this` refers to the instance of the newly created empty class.
- We use `this` within the `constructor()` method and define each property by setting it to the class arguments.

**Particularities:**

1. Classes are NOT hoisted

   Even if they are class declarations

2. Classes are first-class citizens

   We can pass classes into functions and return them from functions

   Because classes are just a special kind of function behind the scenes.

3. Classes are executed in strict mode

   The body of a class is always executed in strict mode.

### Creating a Class Instance

An _instance_ is an object that contains the property names and methods of a Class, but with unique property values.

```js
const john = new PersonCl("John", 25);
const mike = new PersonCl("Mike", 27);
```

- We use the `new` keyword to generate a new instance (object) of the class.
- The `new` keyword: calls the `constructor()`, runs the code inside of it, and then returns the new instance.
- As arguments to the class name, we pass the data that we want the instance to contains.
- Then, we store our newly created instance inside a variable.

### Methods

```js
class PersonCl {
  // ...

  sayHello() {
    console.log(`Hello, I'm ${this.name}.`);
  }
}

const john = new PersonCl("John", 25);
john.sayHello(); // Hello, I'm John
```

We define and call methods for classes just like in regular objects.

The only difference is that in classes we omit the comma between methods.

Node: **Setters** and **Getters** in classes work exactly the same way as in regular objects.

Prototypal inheritance: All methods of a instace, will be on the prototype of that instance, and not on the instances themselves.

```js
john.__proto__ === PersonCl.prototype; // true
```

In practice, the `sayHello` method is in the `__proto__` of `john`.

We can add methods manually to the class prototype:

```js
PersonCl.prototype.sayGoodbye = function () {
  console.log("Goodbye");
};
```

<br>
