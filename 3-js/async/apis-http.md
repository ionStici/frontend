[&larr; Back](./README.md)

# APIs and HTTP Requests

## Table of Content

- [HTTP Requests](#http-requests)
- [Web APIs](#web-apis)
- [**How the Web Works**](#how-the-web-works)

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

Here, the server identifies that it understands the HTTP protocol, then `404 NOT FOUND` status code signifies that the specific piece of content requested was not found.

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
<br>

<hr>

<br>
<br>

# How the Web Works

When we try to access a web server, the browser (client) sends a request to the server and then the server will then send back a response. That response contains the data or the web page that we requested. This process works exactly the same whether we're accessing an entire web page or just some data from a web API.

This process is called: **Request-Response Model** or **Client-Server Architecture**.

<br>

## Table of Content

- [Accessing an URL for data](#accessing-an-url-for-data)
- [HTTP Request](#http-request)
- [HTTP Response](#http-response)
- [TCP / IP](#tcp--ip)
- [Accessing a Web Page](#accessing-a-web-page)

<br>

## Accessing an URL for data

**URL Structure:**

- HTTP or HTTPS (the protocol used for the connection)
- The domain name
- Resource

The domain name we use for any website is actually not the real address of the server. It's just a nice name that is easy to memorize. The domain name is converted to the real address of the server through **DNS**. DNS stands for _Domain Name Server_ and it is a special kind of server (like the phone book of the internet.)

The first step that happens when we access any web server, is that the browser makes a request to a DNS, and this special server will then match and convert the web address (domain name) of the URL to the server's real IP address. This happens through your internet service provider. After the real IP address has been sent back to the browser, it will call the address. A real address looks like this: https:// 104.27.142.889:443

Once we have the real IP address, a TCP socket connection is established between the browser and the server. This connection typically is kept alive for the entire time that it takes to transfer all data.

**TCP** **(Transmission Control Protocol)** and **IP** **(Internet Protocol)**: Together they are communication protocols that define exactly how data travels across the web. They are the internet's fundamentals control system, they set the rules about how the data moves on the internet.

<br>

## HTTP Request

**HTTP** **(HyperText Transfer Protocol)** is a communication protocol. A communication protocol is a system of rules that allows two or more parties to communicate. In the case of HTTP, it's a protocol that allows Clients and Web Servers to communicate. This works by sending request and response messages from Client to Server and back.

**A request message is composed of:**

1. **Start Line:** contains the HTTP method used in the request + the request target + HTTP version.

   Different HTTP methods: GET, POST, PUT, PATCH.

   The request target is the path section of the URL. If the target is empty, then we would be accessing the website's root.

2. **HTTP request headers** contain information about the request itself, like what browser is used, at what time, the user's language and many more.

3. **Request body** (only when sending data to the server "POST") contain the data that we're sending.

**HTTPS Requests** are encrypted using TLS or SSL (security protocols). Besides that, the logic behind HTTP requests and responses still applies to HTTPS.

<br>

## HTTP Response

The request hits the server, which will then prepare the data or webpage to be ready to send back. Once it's ready, it will send it back using a **HTTP response**. A HTTP response message is composed of:

1. **Start Line:** HTTP version + status code + status message. These are used to let the client know whether the request has been successful or failed. For example: 200 means "Ok", 404 means "Page not found".

2. **HTTP response headers** are information about the response itself.

3. **Response Body** contains the JSON data coming back from the API, or the HTML of the web page that we requested.

<br>

## TCP / IP

**TCP** and **IP** are communication protocols that define how data travel across the web.

First, TCP breaks down the requests and responses into thousands of small chunks called packets before they are sent. Once the small packets arrive at their destination, TCP will reassemble all the packets into the original request or response. This step is necessary so that each packet can take a different route through the internet, because this way the messages arrive at the destination as quick as possible, which would not be possible if we sent the entire data as a big chunk, that would be like trying to go through dense traffic with the biggest bus that you can imagine.

The job of the IP protocol is to send and route these packets through the internet using the IP addess that these packets contain, so it ensures that the packets arrive at the correct destination.

<br>

## Accessing a Web Page

When we access a web page, there will be multiple requests and responses. From the first request all we get back is just the initial HTML file. Then this HTML file will get scanned by the browser for all the assets it needs in order to build the page, like CSS files, images, or other assets. For each different file there will be a new HTTP request made to the server. There can be multiple requests and responses at the same time. But the amount is limited, because otherwise the connection would start to slow down. When all the files have finally arrived, the web page can be rendered in the browser according to the HTML, CSS and JS specifications. But for API calls, it is more like a response per request strategy.

<br>
