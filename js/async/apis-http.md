[&larr; Back](./README.md)

# APIs and HTTP Requests

## Table of Content

- [HTTP Requests](#http-requests)
- [Web APIs](#web-apis)

<br>

## HTTP Requests

**URL (Uniform Resource Locator)** is like a home address or a phone number, it describes how to reach you.

**HTTP (HyperText Transfer Protocol)** is used to structure requests and response over the internet. It is a protocol for sending data from one point to another over the network.

This transfer of resources (HTML files, stylesheets, scripts, images, videos) happens using _TCP (Transmission Control Protocol)._

**HTTP & TCP**

When we type an address URL into the browser, it will open a TCP channel to the server that responds to that URL.

- The computer which is making the request, is called _the client_.
- The URL that we request is the address that belongs to the server.

Once the TCP connection is established, the client sends a HTTP GET request to the server to retrieve the webpage. After the server has sent the response, it closes the TCP connection. For other requests, the same process applies.

[Different HTTP methods a client can call](https://www.codecademy.com/article/what-is-rest)

<div></div>

**How the GET request works in relation the client to access resources on the web:**

After you type the URL into the browser, it will extract the `http` part and recognize as the network protocol to use. Then, it takes the domain name from the URL and asks the internet Domain Name Server to return an Internet Protocol (IP) address.

Now the client knows the destination's IP address. It opens a connection to the server at that address using the `http` protocol as specified. It will initiate a GET request to the server which contains the IP address of the host and optionally the data payload.

The GET request contains the following text:

```
GET / HTTP/1.1
Host: www.wikipedia.com
```

_First line:_ identifies the type of request, and the protocol `HTTP/1.1`.

_Second line:_ the address of the server. There may be additional details.

<details>
<summary>HTTP/1.1 is a revision of HTTP/1.0</summary>

<br>

`HTTP/1.0` - every resource request requires a separate connection to the server.

<div></div>

`HTTP/1.1` - uses one connection for additional resource requests (images, stylesheets, etc.) even after the page has been retrieved.

<div></div>

Using `HTTP/1.1` protocol results in less delay.

<div></div>

</details>

If the server is able to locate the path requested, the server might respond with the header:

```
HTTP/1.1 200 OK
Content-Type: text/html
```

This header is followed by the website or content requested.

_First line:_ `HTTP/1.1` refers to as aconfirmation that the server understands the protocol that the client wants to communicate with. + An HTTP status code `200` signifying that the resource was found on the server.

_Second line:_ shows the type of content that it will be sending to the client.

If the server is not able to locate the path requested by the client, it will respond with the header:

```
HTTP/1.1 404 NOT FOUND
```

Here, the server identifies that it understands the HTTP protocol, then `404 NOT FOUND` status code signifies that the specific peece of content requested was not found.

About the [404 error](https://www.codecademy.com/article/http-errors-404).

**HTTPS**

- HTTPS (HTTP Secure) allows you to encrypt data that you send and receive.
- HTTPS is important to use when passing sensitive information to and from websites.

<br>

## Web APIs

An **Application Programming Interface (API)** is a software tool that makes it easier for developers to interact with another application to use some of that application's functionality.

### Types of APIs

_Two main categories of web APIs: (1) browser APIs and (2) 3rd party APIs._

**Browser APIs** are specific to writing code related to browsers and give developers access to information that the browser can also access. [MDN's documentation of web APIs](https://developer.mozilla.org/en-US/docs/Web/API)

**Third-party APIs** are apps that provide functionality or information from a third-party.

### Third-party APIs

Each API has a specific structure and protocol that we have to follow in order to gain access to its functionality.

Organizations that maintain third-party APIs often set rules and requirements for how develoeprs can interact with their APIs.

For OpenWeather, we need to sign up for an account and generate a special token called an _API key_ that grants our account the ability to make API requests. API keys are unique to individual accounts and should be kept secret.

There are free and paid APIs. Check out the API documentation for additional information.

Most of the times we use 3rd-party APIs for making requests for data.

After we make a successful API request, the API sends back data. Usually, APIs data comes in a [JSON](https://www.codecademy.com/article/what-is-json) format (JavaScript Object Notation) which looks like a JavaScript object but converted into a string.

Then, it's up to us how we use this data.

<br>
