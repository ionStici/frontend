[&larr; Back](./README.md)

# Forms Introduction

The `<form>` HTML element represents a document section containing interactive controls for submitting information.

## Table of Content

- [Where is the data processed?](#where-is-the-data-processed)
- [How is the data transferred?](#how-is-the-data-transferred)
- [What method should you use?](#what-method-should-you-use)

<br>

## Where is the data processed?

When a form is submitted, the browser makes a request. A script can respond to that request and process the data. By default, the request is made to the page where the form is shown.

A script running on the server or on the client is needed to process the form. It may validate the data, save it into a database, or do other operations based on the form data. The `action` attribute requires the backend location of the script waiting for the form to be submitted.

## How is the data transferred?

By default, the form is sent as a `GET` request, with the submitted data appended to the URL. In this case, we can access the data on the frontend or the backend by getting the data from the URL.

We can instruct the form to use a `POST` request by changing the method attribute: `method="post"`. By using `POST`, the data is included in the body of the request. The data will not be visible in the URL and can only be accessed from a frontend or backend script.

## What method should you use?

For forms that process sensitive data use the `POST` method. The data is encrypted (if you use HTTPS) and only accessible by the backend script that processes the request. The data is not visible in the URL. A common example is a sign-in form.

If the data is shareable, you can use the `GET` method. This way the data will be added to your browser history as it is included in the URL. Search forms often use this. This way you can bookmark a search result page.

<br>
