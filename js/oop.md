[&larr; Back](./README.md)

# Object-Oriented Programming (OOP)

In modern JavaScript, there are two major paradigms: **Object-oriented Programming** and **Functional Programming**.

## Table of Content

- [What is Object-Oriented Programming](#what-is-object-oriented-programming)
- [The 4 fundamental OOP principles](#the-4-fundamental-oop-principles)
- [OOP in JavaScript](#oop-in-javascript)
- [Three ways of implementing prototypal inheritance in JavaScript](#three-ways-of-implementing-prototypal-inheritance-in-javascript)

<br>

## What is Object-Oriented Programming

- Object-Oriented Programming (OOP) is a programming paradigm that is based on the concept of objects. By _paradigm_ we mean code style, the way we write and organize code.

- We use objects to model (describe) aspects of the real world, like a user or a to-do list item.

- Objects can contain data in the form of properties and code functionality in the form of methods. We can pack all the data and the corresponding behavior into one big object.

- In OOP, objects are self-contained pieces of code, like small applications on their own.

- We use objects as building-blocks of our application, and make them interact with one another.

- These interactions happen through a **public interface** (API). This interface refers to a bunch of methods that the code outside of the object can access and use to communicate with the object.

- OOP was developed with the goal of organizing code, to make it more flexible and easier to maintain and avoid _spaghetti code_ (unorganized code).

- OOP is the most popular and widely used programming paradigm in large scale software engineering. Other popular programming paradigm: **functional programming**.

- In OOP we create objects programmatically, traditionally using classes. So we create classes to generate objects from them.

- For example: from a `User` class, we can create objects for each user based on the `User` class data. We call all objects created through a class: **instances**. The class itself is not an object.

<br>

## The 4 fundamental OOP principles

1. **Abstraction:** Ignoring or hiding details that don't matter, allowing us to get an overview perspective of the thing we're implementing, instead of messing with details that don't matter to our implementation. Abstraction is important in programming in general, not just in OOP.

2. **Encapsulation:** Keeping properties and methods _private_ inside the class, so they are _not accessible from outside the class_. Then some methods are _exposed_ as a public interface (API).

   Interaction between objects happen through a public inteface. Inside the class these properties are accessible, outside code can't access them. Encapsulation prevents external code from accidentally manipulating internal state and avoids errors. The public interface is essentially all methods that are not private and are supposed to be used on purpose.

3. **Inheritance:** Making all properties and methods of a certain class available to a child class, forming a hierarchical relationship between classes. This allows us to reuse common logic and to model real-world relationships.

   Example: Two classes, User and Admin. They have a lot in common, Admin has all the properties and methods that the User has. We can avoid duplicate code by implementing _inheritance_: a child class inherit (extends) all properties and methods from its parent class. This forms a hierarchy between these 2 classes. The goal of this practice is to reuse logic that is common to both of the classes.

4. **Polymorphism:** A child class can override a method it inherited from a parent class.

   The Admin class, which inherited the state from the User class, needs a special login method. So we write a new method for the Admin class, also called login, and then according to polymorphism that new login method will overwrite the login method that has been inherited from the User class.

<br>

## OOP in JavaScript

OOP specifically in JavaScript works a bit differently.

In JavaScript we have **prototypes**.

All objects in JavaScript are linked to a certain prototype object.

The prototype object contains methods and properties that all the objects that are linked to that prototype can access and use. This behavior is called **prototypal inheritance**.

_Prototypal Inheritance_: all objects that are linked to a certain prototype object can used the methods and properties that are defined on that prototype. Objects inherit methods and properties from the prototype.

Prototypal inheritance: **delegation**.

Objects delegate behavior (properties and methods) to the linked prototypal object.

On the other hand, in classic OOP with classes, the methods are copied from the class to the objects, which is completely different.

For example: we are able to use the `map()` method on all arrays due to prototypal inheritance. On MDN, we can see that `map` is entitled as `Array.prototype.map()`. So `Array.prototype` is the prototype object of all the arrays that we create.

This is where all the methods for arrays are defined, on their prototype object `Array.prototype`. When we create an array, this array is linked to this prototype. Therefore, it has access to all the methods that are defined on the `Array.prototype` object. In essence, our array inherit the `map` method from `Array.prototype`.

<br>

## Three ways of implementing prototypal inheritance in JavaScript

1. **Using a constructor function:** Creating objects programmatically and setting the object's prototype using a function.

   This is how built-in objects like arrays and maps or sets are implemented.

   This is how OOP has been done in JavaScript since the beginning.

2. **ES6 Classes:** Modern OOP alternative to constructor function syntax.

   These are not the kind of traditional classes, they are instead just _syntactic sugar_ over constructor functions with a nicer syntax.

   But behind the scenes ES6 classes are implemented with constructor functions.

   In practice, ES6 Classes also use prototypal inheritance.

3. **Object.create() function:** The easiest way and most straightforward way of linking an object to a prototype object.

The 4 principles of OOP are still valid and important with prototypal inheritance.
