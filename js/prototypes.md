[&larr; Back](./README.md)

# OOP in JavaScript: Prototypes

## Table of Content

- [Constructor Functions and the `new` operator](#constructor-functions-and-the-new-operator)
- [Prototypes and Methods](#prototypes-and-methods)

<br>

## Constructor Functions and the `new` operator

**Constructor Functions:** build object instances using a function.

A constructor function is a normal function, but called with the `new` operator.

OOP convention: the name of constructor functions start with a capital letter.

For constructor functions we use function declaration or expression.

But not arrow functions because they doesn't have their own `this` keyword.

```js
const Person = function (name, age) {
  this.name = name;
  this.age = age;
};

const john = new Person("John", 25);
```

- A constructor function is gonna produce an object.
- The arguments we pass in will be the object properties.
- We call the constructor function with the `new` operator.

What happenes when we call a function with the `new` operator behind the scenes:

1. A new empty object `{}` is created.
2. The function is called, the `this` keyword is set to the newly created object.
3. The newly created object is linked to a prototype.
4. The object is automatically returned from the constructor function.

Because in step 4 the object is returned, we store it in a variable which in turn will be the object itself.

When we call the function, the `this` keyword inside the function will be the newly created object, so we define properties on the `this` (keyword which essentially is the object) from the values we receive as parameters. Convention: give the properties exactly the same names as the parameters.

We can create as many different objects as we want from constructor functions.

In classical OOP we created object instances from a class. JavaScript doesn't have classes in the sense of traditional OOP, so technically we didn't created a class here, instead we created an object from a constructor function.

Constructor function simulate classes. Anyway, we can say that `john` is an instance of `Person`.

**Instance Properties:** the constructor function properties.

<br>
