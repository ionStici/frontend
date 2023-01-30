[&larr; Back](./README.md)

# OOP in JavaScript: Prototypes

Learn how JavaScript prototypes work before learning [ES6 Classes](./classes.md).

<br>

## Table of Content

- [Constructor Functions and the `new` operator](#constructor-functions-and-the-new-operator)
- [Prototypes](#prototypes)

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

### Methods (Wrong 🚫)

Just like we added properties to the constructor function, we can add methods:

```js
// this.sayHello = function() { console.log(`Hello, I'm ${this.name}`) }
// john.sayHello(); // Hello, I'm John
```

However, we should not created methods inside a constructor function. Because in this way each object created through this constructor function would carry around the same method copy. This is terrible for performance of our code.

Instead, we are gonna use _prototypes and prototypes inheritance_.

<br>

## Prototypes

Every function in JavaScript has a property called `prototype`

`Person.prototype;`

Every object that is created by a constructor function will inherit, will get access to all the methods and proeprties that we define on the `prototype` of the constructor function.

Adding a method on the prototype property of the Person constructor function:

```js
Person.prototype.sayHello = function () {
  console.log(`Hello, I'm ${this.name}`);
};

console.log(Person.prototype); // the sayHello method will be here
john.sayHello(); // Hello, I'm John
```

All objects created by Person constructor function will get access to all the methods of its `prototype` property. We can now use the `sayHello` method on `john` instance object even though it is not really on `john` itself, but we have access to it due to prototypal inheritance.

Now like this, exists only one copy of the `sayHello` method which is on the `prototype` property of the `Person` constructor function, then all of the objects created by this constructor function can reuse it on themselves.

In other words, `john` instance is connected to the `prototype` of Person constructor function.

Every object has access to the methods and properties from its `prototype`. And the `prototype` of `john` is `Person.prototype`. We can confirm this with:

```js
john.__proto__; // Person.prototype, sayHello lives here
john.__proto__ === Person.prototype; // true
Person.prototype.isPrototypeOf(john); // true
```

`john.__proto__` is the prototype of `john`, which in `Person.prototype`.

`__proto__` is the linked prototype of the object on which it is called on.

`Person.prototype` is the `prototype` of all the objects created by the `Person` constructor function.

`__proto__` property of created in step number 3 of the `new` operator, and its value is set to the `prototype` property of the function that is being called.

The `__proto__` property of the object is set to the prototype of the constructor function.

If we log an instance object, we see there its `prototype` which is exactly `Person.prototype`, containing `sayHello` method.

Example:

```js
Person.prototype.hobby = "Reading";
```

Now, all instances will have access to this `hobby` property from the prototype. Not directly, but it will be in the `__proto__` property of the object - because of this, the `hobby` property is considered: not own property. Own properties are only the ones that are declared directly on the object itself, not including inherited properties.

```js
john.hasOwnProperty("name"); // true
john.hasOwnProperty("hobby"); // false
```

<br>
