[&larr; Back](./README.md)

# REST

[Codecademy: What is REST?](https://www.codecademy.com/article/what-is-rest)

**REST (REpresentational State Transfer)** is an architectural style for providing standards between computer systems on the web, making it easier for systems to communicate with each other.

REST-compliant systems, often called RESTful systems, are characterized by how they are stateless and separate the concerns of client and server. _RESTful systems characteristics:_

**Separation of Client and Server:** In the REST architectural style, the implementation of the client and the implementation of the server can be done independently without each knowing about ther other.

**Statelessness:** Systems that follow the REST paradigm are stateless, meaning that the server does not need to know anything about what state the client is in and vice versa.

## Communication between Client and Server

In the REST architecture, clients send requests to retrieve or modify resources, and servers send responses to these requests.

## Making Requests

REST requires that a client make a request to the server in order to retrieve of modify data on the server. A request generally consists of:

- an HTTP verb (defines what kind of operation to perform)
- a header (allows the client to pass along information about the request)
- a path to a resource
- an optional message body containing data

### HTTP Verbs

There are 4 basic HTTP verbs we use in requests to interact with resources in a REST system:

- `GET` - retrieve specific resources (by id)
- `POST` - create a new resource
- `PUT` - update a specific resource (by id)
- `DELETE` - remove a specific resource (by id)

[Codecademy: What is CRUD?](https://www.codecademy.com/article/what-is-crud)

### ...

<!-- ### Headers and Accept parameters -->
