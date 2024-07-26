[&larr; Back](./README.md)

# The MVC Architecture

## Table of Contents

- [Why Software Architecture?](#why-software-architecture)
- [Components of any Architecture](#components-of-any-architecture)
- [The Model-View-Controller (MVC) Architecture](#the-model-view-controller-mvc-architecture)

<br>

## Why Software Architecture?

- Architecture gives the project **Structure** on which we can then write code. In software, structure refers to how we organize and divide the code different modules, classes and functions.

- **Maintainability:** when the code base is well structured.

- **Expandability:** the ability to easily add new features in the future, which is only possible with a good structure, and a good overall architecture.

A good architecture is one that considers the above aspects: structure, maintainability, expandability.

<br>

## Components of any Architecture

- **Business Logic:** Code that **solve the actual business problem.**

  Code directly related to what business does and what it needs.

  Examples: sending messages, storing transactions, calculating taxes.

- **State:** stores all the data about the application running in the browser (frontend).

  The state should store any data you might fetch from an API or data that the user inputs.

  State should be the "single source of truth". The UI should be kept in sync with the state.

- **HTTP Library:** responsible for making and receiving AJAX requests.

- **Application Logic (Router):** code that is only concerned about the **implementation** of the application itself.

  Handles navigation and UI events.

- **Presentation Logic (UI Layer):** code that is concerned about the **visible part** of the application.

  The presentation logic is responsible for displaying the application state on the user interface.

<br>

## The Model-View-Controller (MVC) Architecture

MVC Architecture contains 3 big parts: Moden, View, Controller.

- **View** is for the presentation logic, the part of the app interacting with the user.

- **Model** is all about the app data: includes state, business logic, HTTP library.

- **Controller** - the application logic, it creates a bridge between the model and view.

The View and the Model are completely independent from one another.

_A typical flow of actions as soon as some event happens on the user interface:_

1. The controller handles the event (app logic).

2. In case this event updates the UI or asks the model for data, we say that the **controller** dispatches tasks to the **model / view**. In other words, the controller controls and orchestrates the entire action, in fact the whole application itself.

3. Asking the Model for data might involve doing an Ajax request, and that's what the Model does. When the data arrives, the Controller takes the data and sends it to the View, which will render that data to the user interface, and the cycle finished.

It's only the Controller who imports and calls functions from the model and from the view, but never the other way around.

The model and the view are in fact completely standalone and isolated, they don't import each other, and they don't even import the controller. All they do is to wait for instractions from the controller.

```
src/js/
    controller.js
    model.js
    views/
        todosView.js
        searchView.js
```

- `model.js` module contains the entire Model.
- `controller.js` module for all the controllers.
- `views/searchView.js` folder with multiple views, one for each feature.

<br>
