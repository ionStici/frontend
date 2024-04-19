[&larr; Back](./README.md)

# JavaScript Testing

## Introduction

- **Software testing** is the process of assessing the completeness and quality of computer software.
- **Manual testing** is a form of testing done by a human interacting with a system.
- A **bug** is an error in a software that makes the system behave in unexpected ways.
- **Automated testing** is the use of software to control the execution of tests and the comparison of actual behavior to expected behavior. Compared to manual testing, automated testing is: faster, more reliable, maintainable.
- **Regression** is when a break occurs within a feature developed earlier after some current changes. When functionality previously developed and tested stops working, you may say _the functionality regressed_.
- **Tests as Documentation** provide both human-readable text to describe the application and machine-executable code to confirm the app works as described.
- [Codecademy Docs: Types of Testing](https://www.codecademy.com/resources/docs/general/software-testing)
- A **test suite** is a collection of tests for a web application. Tests are written with code, just like the rest of your web app. You can refer to the code defining your app as _implementation code_, and the code defining your tests as _test code_. Test code is included with and structured similarly to implementation code. Often times changes to test code are associated with changes to implementation code and vice versa. Both are easier to maintain when they are stored in the same place. For example, if implementation code is written in `index.js` then the corresponding test code may be written in `index-test.js`.

<br>

<!-- ## Tests with Mocha

**Test frameworks:** organize and automate tests that provide useful feedback when errors occur.

[**Mocha**](https://mochajs.org/) is a JavaScript test framework running on Node.js and in the browser.

<br>

### Install and Run Mocha

After setting npm for your project directory, run the following command to install mocha:

```
npm install mocha -D
```

To run Mocha, we add a script to `package.json` in the `scripts` field:

```
"scripts": {
    "test": "mocha"
}
```

Now, we can call Mocha using this command:

```
npm test
```

This will run the full test suite automatically.

<br> -->
