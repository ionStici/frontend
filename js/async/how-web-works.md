[&larr; Back](./README.md)

# How the Web Works

When we try to access a web server, the browser (client) sends a request to the server and then the server will then send back a response. That response contains the data or the web page that we requested. This process works exactly the same whether we're accessing an entire web page or just some data from a web API.

This process is called: **Request-Response Model** or **Client-Server Architecture**.

<br>

## Table of Content

- [Accessing an URL for data](#accessing-an-url-for-data)
- [HTTP Request](#http-request)
- [HTTP Response](#http-response)

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
