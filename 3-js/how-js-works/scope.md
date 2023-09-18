[&larr; Back](./README.md)

# Scope

## Table of Content

- [Scope Concepts](#scope-concepts)
- [Blocks and Scope](#blocks-and-scope)
- [Three types of scope in JS](#three-types-of-scope-in-js)
- [Global Scope](#global-scope)
- [Block Scope](#block-scope)
- [Scope Pollution and Best practices](#scope-pollution-and-best-practices)
- [The Scope Chain](#the-scope-chain)
- [Scoping in practice](#scoping-in-practice)
- [Summary](#summary)

<br>

## Scope Concepts

- **Scoping** controls how our program's variables are organized and accessed;
- **Lexical Scoping:** (for JS) Scoping is controlled by the placement of functions and blocks in the code;
- **Scope:** Space or environment in which a certain variable is declared. We have: _global scope_, _function scope_ and _block scope_.
- **Scope of a variable:** Region of our code where a certain variable can be accessed.

<br>

## Blocks and Scope

A block is the code found inside a set of curly braces `{}`

Like the function body or an `if` statement.

<br>

## Three types of scope in JS

1. **The Global Scope** is for top-level code. For variables that are declared outside of any function or block. These variables will be accessible everywhere in our program, in all functions and all blocks.

2. **Function Scope:** Every function creates a scope, also called _local scope_. Variables declared inside a function scope, are only accessible inside that function and from other inner functions, but not outside of it.

3. **Block Scope:** _(starting with ES6)_ With block we mean everything that is between curly braces. This works just like function scopes. The difference is that block scopes only apply to variables declared with `let` or `const`. `var` variables are scoped to the parent scope in case of block scopes. All functions are also block scoped, but only in strict mode.

<br>

## Global Scope

**Scope** is the context in which our variables are declared.

We think about scope in relation to blocks because variables can exist either outside of or within these blocks.

In global scope, variables are declared outside of blocks.

These variables are called global variables.

Because global variables are not bound inside a block, they can be accessed by any code in the program, including code in blocks.

<br>

## Block Scope

When a variable is defined inside a block, it is only accessible to the code within the curly braces `{}`.

Variables that are declared with block scope are known as local variables because they are only available to the code that is part of the same block.

<br>

## Scope Pollution and Best practices

Global variables go to the global namespace. The global namespace allow the variables to be accessible from anywhere in the program.

Scope pollution is when we have too many global variables that exist in the global namespace. This makes it difficult to keep track of our different variables and can lead to potential errors. It is a best practice not to define variables in the global scope.

We should follow best practices for scoping our variables as tightly as possible using block scopes. Benefits:

- More modular, maintainable and understandable code.
- It will save memory in your code because it will cease to exist after the block finishes running.

If a variable does not need to exist outside a block — it shouldn’t!

<br>

## The Scope Chain

**Variable Lookup:** Every scope always has access to all the variables from all its outer scopes (from parent scopes). This also includes arguments. But, this does not work the other way around or sideways. A certain scope can't access variables from inner scopes.

- The scope chain is all about the order in which functions are written in the code. The order of function calls is not relevant to the scope chain at all.
- A function scope is equal to its variable environment. We can say that the scope chain in a certain scope is equal to adding together all the variable environments of all the parent scopes.

_Note:_ declared functions also count as variables present in a certain scope.

<br>

## Scoping in practice

- If JS is looking for a variable that is not in the current scope, it will look in its outer scopes, and if the variables is in one of its outer scopes, then it will stop there and will use the variable from the nearest scope.

- Two variables with the same name, in two different scopes, are completely different variables, because they are defined in different scopes. So we can have repeated variable names in different scopes. And this is the reason why we can have different functions with the same parameter names, because each parameter is defined in that scope of that function. It is not a problem at all to have many functions with the exact same parameter names, in the same way it's not a problem to have different functions with the same variable names inside of them.

- We can manipulate variables located inside a child scope from a parent scope.

<br>

## Summary

- Scope refers to where variables can be accessed throughout the program, and is determined by where and how they are declared.
- Blocks are statements that exist within curly braces {}.
- Global scope refers to the context within which variables are accessible to every part of the program.
- Global variables are variables that exist within global scope.
- Block scope refers to the context within which variables are accessible only within the block they are defined.
- Local variables are variables that exist within block scope.
- Global namespace is the space in our code that contains globally scoped information.
- Scope pollution is when too many variables exist in a namespace or variable names are reused.

<div></div>

- Scoping asks the question: _"Where do variables live?"_ or _"Where can we access a certain variable, and where not?"_;
- There are 3 types of scope in JavaScript: the global scope, scopes defined by functions, and scopes defined by blocks;
- Only `let` and `const` variables are block-scoped. Variables declared with `var` end up in the closest function scope;
- In JavaScript, we have lexical scoping, so the rules of where we can access variables are based on exactly where in the code functions and blocks are written;
- Every scope always has access to all the variables from all its outer scopes. This si the scope chain;
- When a variable is not in the current scope, the engine looks up in the scope chain until it finds the variable it's looking for. This is called variable lookup;
- The scope chain is a one-way street: a scope will never have access to the variables of an inner scope;
- The scope chain in a certain scope is equal to adding together all the variable environments of all parent scopes;
- The scope chain has nothing to do with the order in which functions were called. It does not affect the scope chain at all.

<br>
