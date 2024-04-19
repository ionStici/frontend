[&larr; Back](./README.md)

# Variable Environment

**Hoisting** (JavaScript mechanism) - makes certain variables accessible in the code before they are declared.

During the creating phase of the execution context, the code is scanned for variable declarations before it is executed, then for each found variable, a new property is created in the variable environment object.

Hoisting does not work the same for all variable types:

|                         | Hoisted? | Initial Value         | Scope                            |
| ----------------------- | -------- | --------------------- | -------------------------------- |
| function declarations   | Yes      | The actual function   | strict: Block / sloppy: Function |
| `var` variables         | Yes      | `undefined`           | Function                         |
| `let` `const` variables | No       | `<uninitialized>` TDZ | Block                            |
| func. express. & arrow  |          |                       |                                  |

- We can use **Function declarations** before they are declared in the code, this is because they are stored in the variable environment object even before the code starts executing.

- **`var` variables** - hoisted

- **`let` `const` variables** - technically they are hoisted but their value is set to `Uninitialized`, which results in like hoisting was not happening at all. We say that these variables are placed in **Temporal Dead Zone (TDZ)**.

  TDZ makes it so that we can't access these variables between the beginning of the scope and the place where the variables are declared. As a consequence, if we attempt to use a let or const variable before it's declared, we get ane error.

- Function **expressions** and **arrows** - it depends if they were declared using `var` or `const let`, because this functions are simply variables, they behave the exact same way as variables in regard to hoisting.

<br>

## Temporal Dead Zone - TDZ

Every `let` and `const` variable gets their own TDZ that starts at the beginning of the scope, until the line where it is defined, and the variable is only safe to use after the TDZ.

If we try to access a variable while in the TDZ, then we get a reference error telling us that we can't access the variable before initialisation. This error is not the same as if we would try to access a variable that is not yet defined.

So the engine knows that the variable from the TDZ will eventually be initialised, because it already read the code before, and it set the variable in the variable environment to _uninitialised_. Then, when the execution reaches the line where the variable is declared, it is removed from the TDZ and it's then safe to be used.

The main reason for the need of TDZ is to avoid errors. A second reason is to make `const` variables work the way they are supposed to, which means to be assigned only when the execution reaches the declaration, so it will avoid the need of reassigning because of `undefined` as the frist value (as `var` variables do).

If hoisting is bad, why does it exist in the first place? The creator of JS implemented hoisting so that we can use function declarations before they are written, because this is essential for some programming techniques, such as mutual recursion. The fact that it also works for `var` declarations is because that was the only way hoisting could be implemented at the time. So hoisting of `var` variables is just a byproduct of hoisting functions, and it probably seemed a good idea to simply set variables to `undefined`. We need to consider that JS was never intended to become the huge programming language that it is today. To work this around we should use only `let` and `const`.

<br>

## Hoisting and TDZ in Practice

- The only function that can be used before declaring, is the function declaration.

- Function expression and arrow function declared with `let` and `const` can't. If we would use `var` we would still get an error: _respective function is not a function._ This is because just like `var` variables, we get `undefined` as value, but because we used parenthesis to call the function it resulted in `undefined()` which obviously is not a function as JS tells us.

- **Advice:** In order to write clean code, you should declare your variables at the top of each scope.

  This applies for function as well, call functions only after declaration, even for function declaration.

**Note:** Variables declared with `var` will create a property on the global `window` object, but `let` and `const` don't.

<br>
