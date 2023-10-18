# Authentication

## How Does Authentication Work (In React & NextJS Apps)?

Client (Browser) <---> Server (connected to a database)

After filling the "login" form, we send a request to the server with the user data. On the server we validate that input and we send back a response with yes/no. If the user was successfully authenticated, he can access protected routes, send requests to other protected endpoints to the server. The authentication to be trustworthy we need "proof", and for this we got 2 main mechanisms:

1. **Server-side Sessions** - store unique identifier on the server, and the same identifier to the client that sent us the credentials. The client sends identifier along with requests to protected resources. With SSL the identifier can't be stoled. On the client it is stored on a cookie typically, that cookie can be configured such that it's not accessible through JavaScript, to prevent cross-site-script attacks, so that it's readable only to the server when requests are made. If we protect from cross site scripting (XSS) then the client is pretty secure, only the user and server have access.

2. **Authentication Tokens** - no identifiers, instead the server creates and asigns (but not store) "permission" tokens (random strings) on the server, and sends a token to the client. These random strings (tokens) can be unpacked to data packages. The client saves this token and asigns it to ongoing requests to protected resources. The server doesn't store this token anywhere, still the server knows how it signed that token, so the server will be able to verify if the token was created by it or not.

When building SPAs, we typically work with Tokens instead of Sessions. Why? Pages are served directly and populated with logic without hitting the server, we don't send a request for every page you visit, the server doesn't see every request you have send, therefore you load pages without the server being able to directly find out if you are authenticated ot not.

Another reason for SPAs + Tokens: Backend APIs which are used for SPAs are typically stateless, they don't care about the individual connected clients, they don't keep track of all the connected clients, instead that API can work pretty much on its own, it just is able ot hand out permissions to clients who authenticated so that they can then later request access to protected resources. The API itself does not store any extra information about any connected clients.

For SPAs, the server is not involved in every request and every action that's happening on our page, because we handled that with frontend JavaScript, and we have that stateless API connected to the SPA.

This results in a "detached" forntend and backend combination, they do talk to each other sometimes, but not for every action that's going on on the page.

- Servers don't save information about authenticated clients.
- Instead, clients should get that permission which allows them to prove that they are authenticated.

That's why we use tokens (JWT: JSON Web Tokens).

### JSON Web Tokens (JWT)

JWT is generated with 3 main building blocks.

- Issuer Data (data "metadata" automatically added into a token by the server when that token is generated, preconfigured by 3rd party packages we use for generating tokens).
- Custom Data (e.g. user data)
- Secret Signing Key - we set this on the server, the client never gets to see this key.

We generate a token with some third-party package by combining all these pieces together, by creating a long random string that incorporates all that data and is signed by that key.

Server-side Token Creating + Signing = JSON Web Token.

"Signing" does not mean encryption, JWT is not encrypted, you can unpack it and read the data inside of it without knowing that key, that key only proves that a given server created that token, but you can read the content of the token without knowing that key, the key will not be included in the token, you can't read the key even if unpack the token.

So it's that token that is stored by the client, which then is attached to requests to protected resources on the server, for example if you want to change the password, we don't just send the old and new password, but we also include that token in the outgoing request.

That token then is validated by the server, by checking if it could generate that token using the key that only it has. So it can omly generate the token by knowing the key.

For token creation and validation we can rely on secure third-party packages
