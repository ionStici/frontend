[&larr; Back](./README.md)

# Scope

**Scope** defines where variables can be accessed.

<br>

## Table of Content

- []()
- []()
- []()

<br>

## Blocks and Scope

A block is the code found inside a set of curly braces `{}`

Like the function body or an `if` statement.

<br>

## Global Scope

**Scope** is the contect in which our variables are declared.

We think about scope in relation to blocks because variables can exist either outside of or within these blocks.

In global scope, variables are declared outside of blocks.

These variables are called global variables.

Because global variables are not bound inside a block, they can be accessed by any code in the program, including code in blocks.

<br>

## Block Scope

When a variable is defined inside a block , it is only accessible to the code within the curly braces `{}`.

Variables that are declared with block scope are known as local variables because they are only available to the code that is part of the same block.

<br>

## Scope Pollution

When you declare global variables, they go to the global namespace.

The global namespace allows the variables to be accessible from anywhere in the program.

Scope pollution is when we have too many global variables that exist in the global namespace, or when we reuse variables across different scopes. Scope pollution makes it difficult to keep track of our different variables and sets us up for potential accidents. For example, globally scoped variables can collide with other variables that are more locally scoped, causing unexpected behavior in our code.

It’s best practice to not define variables in the global scope.

<br>

## Practice Good Scoping

Given the challenges with global variables and scope pollution, we should follow best practices for scoping our variables as tightly as possible using block scope.

Tightly scoping your variables will greatly improve your code in several ways:

- It will make your code more legible since the blocks will organize your code into discrete sections.
- It makes your code more understandable since it clarifies which variables are associated with different parts of the program rather than having to keep track of them line after line!
- It’s easier to maintain your code, since your code will be modular.
- It will save memory in your code because it will cease to exist after the block finishes running.

If a variable does not need to exist outside a block— it shouldn’t!

<br>

## Review

- Scope refers to where variables can be accessed throughout the program, and is determined by where and how they are declared.
- Blocks are statements that exist within curly braces {}.
- Global scope refers to the context within which variables are accessible to every part of the program.
- Global variables are variables that exist within global scope.
- Block scope refers to the context within which variables are accessible only within the block they are defined.
- Local variables are variables that exist within block scope.
- Global namespace is the space in our code that contains globally scoped information.
- Scope pollution is when too many variables exist in a namespace or variable names are reused.
