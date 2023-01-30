[&larr; Back](./README.md)

# OOP in JavaScript: Prototypes

Learn how JavaScript prototypes work before learning [ES6 Classes](./classes.md).

<br>

## Table of Content

- [Constructor Functions and the `new` operator](#constructor-functions-and-the-new-operator)
- [Prototypes](#prototypes)
- [Prototypal Inheritance and The Prototype Chain](#prototypal-inheritance-and-the-prototype-chain)
- [Prototypal Inheritance on Built-In Objects](#prototypal-inheritance-on-built-in-objects)

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

## Prototypal Inheritance and The Prototype Chain

Constructor functions have a `prototype` object.

This `prototype` object is the prototype of all object instances created through this constructor function.

How an object is created through a constructor function using the `new` operator:

1. A new empty object is created.
2. The `this` keyword in the function call is set to the newly created object.
3. The new object is linked to the `prototype` property of the constructor function. This happens internally by adding the `__proto__` property to the new object. `__proto__` always points to the `prototype` of an object, this is true for all objects in JavaScript.
4. The new object is automatically returned from the function (unless we explicitly return something else, but in constructor functions we never do that). With this, the result of the `new` operator and the `Person` constructor function is a new object created programmatically, which we then store it in a variable.

This process is valid for constructor functions and ES6 classes, but not for `Object.create`.

When we attempt to call the `sayHello` method on the `john` object, JavaScript can't find it directly on the object, it is not there. If a property or a method can't be found in a certain object, JS will look into its prototype, and if it's there then JS will use it. That's how the `sayHello` method can run correctly and return a result. **This behavior is called prototypal inheritance and delegation**. The `john` object inherited (delegated) the `sayHello` method from its `prototype`. We can use this ONE COPY `sayHello` method on all the objects created through `Person` constructor function. All of them will inherit the `sayHello` method, without the method being directly attached to all the objects themselves, this is essential for JS code performance.

The fact that `john` object is connected to a prototype, and the ability of looking up methods and properties in a prototype, is what we call the: **prototype chain**.

All objects in JS have a prototype, the prototype of `john` is `Person.prototype`, and because `Person.prototype` is an object, it also has a prototype which is `Object.prototype`.

`Person.prototype` is a regular object, which means that it has been built by the built-in `Object` constructor function. This is the function that is called behind the scenes whenever we create an object literal. Essentially, the curly braces `{}` are like a shortcut or writing `new Object`. Since `Person.prototype` has been created by the `Object` constructor function, its `prototype` is gonna be `Object.prototype`. It's the same logic as with the `john` object and its `Person` constructor.

This entire series of links between objects, is called the: **prototype chain**.

`Object.prototype` is the top of the prototype chain, this means that its prototype is `null`, marking the end of the prototype chain.

As the Scope Chain, in the prototype chain whenever JavaScript can't find a property or a method in a certain object, it's gonna loop up into the next prototype in the prototype chain, and see if it can find it there, and if the property is not found then it continues to look up until the last prototype.

Example: simulate `john` calling `hasOwnProperty('name')` method - first JS starts trying to find the called method on the object itself where it was called, and because it was not found there, it is gonna look in its prototype which is `Person.prototype`. The required method isn't here too, therefore it will move up even further in the prototype chain, now looking into `Object.prototype`. `Object.prototype` does contain a bunch of built-in methods, including `hasOwnProperty()`. JavaScript then takes this one and run it on the `john` object as this method was defined directly on `john`. Important: the method was not copied into the `john` object, instead it was inherited from `Object.prototype` through the prototype chain.

<br>

## Prototypal Inheritance on Built-In Objects

We can use the `__proto__` property to look in the prototype chain even further.

```js
john.__proto__.__proto__.__proto__; // null
// Person.prototype -> Object.prototype -> null
```

**The prototype of a function:** any function is also an object, therefore it also has a prototype, which contains methods on functions like: `apply`, `bind`, `call`. This is the reason why we can call methods on functions, because they are objects and objects have prototypes.

**The prototype of arrays:**

```js
const arr = [1, 2, 3, 2];
Array.prototype === arr.__proto__; // true
```

The prototype of `arr` or of any other regular array is `Array.prototype`. In this prototype we have all the methods that arrays have. This is the reason why all the arrays get access to all of these methods, the inherit them from tis prototype `Array.prototype`.

`Array` is the constructor function, so the prototype property of the constructor is gonna be the prototype of all the objects created by that constructor. Just like in objects, this `[1, 2, 3]` is the shortcut of `new Array(1, 2, 3)`.

The prototype of `Array` is `Object.prototype`.

```js
arr.__proto__.__proto__ === Array.prototype.__proto__; // true
```

If we search for a method on MDN, we see its name like `Array.prototype.filter()`. The `filter` method lives in the prototype property of the `Array` constructor.

The prototypal inheritance is a mechanism for reusing code. All these built-in methods have to exists only once somewhere in the JavaScript engine, and then all the arrays in our code get access to them through prototype chain and prototypal inheritance.

We even can created methods on the `Array.prototype`, then all arrays inherit them:

```js
Array.prototype.unique = function () {
  return [...new set(this)];
}; // return all the unique elements of an array
arr.unique(); // (3) [1, 2, 3]
```

The `this` keyword is going to be the array on which the method will be called.

However this is not a good idea. The next version of JavaScript might add a method with the same name that we are adding. And if you work on a team of developers, this might create bugs, because developers implement the same method with a different name. If you're working on a small project on your own then i guess you could do it.

**All the DOM elements are behind the scenes objects:** in these DOM element objects we have a lot of different properties and methods, and a huge prototype chain.

```js
h1.__proto__.__proto__.__proto__.__proto__.__proto__.__proto__.__proto__; // null
```

<br>
