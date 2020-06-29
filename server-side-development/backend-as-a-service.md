
# Backend as a Service (BaaS)


## HTTPS and Secure Communication


### Symmetric Key Cryptography



*   Shared secret key between two parties


### Public Key Cryptography

Asymmetric Encryption



*   Public key can be widely distributed
*   Private key is only known to the receiver
*   Expensive process


![alt_text](images/image2.png "image_tooltip")



### Secure Sockets Layer (SSL)/ Transport Layer Security (TLS)



*   Uses a combination of public-key cryptography and symmetric cryptography


### SSL/TLS Handshake





*   Same session key: both follow same process for generating the session key


### HTTPS






*   Transport layer: TCP & IP forms the network
*   Secure socket layer: SSL/TLS, ensure secure communication between server and client
*   HTTPS: HTTP + encryption/decryption through SSL & TLS
*   Run on port 443


### Generating Keys



*   Open SSL: generate self-signed certificate
*   Self-signed keys: not acceptable in the outside work
    *   In postman, need to turn off SSL certificate verification
*   Production environment: get the keys and certificate from a certification authority (CA)


## Uploading Files



*   The boundary separates the multipart request body


### Multer

Supports multipart/ form-data included inside the request body



*   Written on top of busboy, a Node module for parsing incoming HTML form data
*   Parses the incoming form data and adds a body object and file/files object to request body


## Cross-Origin Resource Sharing (CORS)


### Origin

_Defined by **(Protocol, host name, port number)**_


### Same-Origin Policy

_Web app security model that restricts how a document or script loaded from one origin can interact with a resource from another origin_



*   Isolating potentially malicious documents



### Cross-Origin HTTP request

_Accessing a resource from a different domain, protocol or port_


### Cross-Origin Resource Sharing (CORS)

_Give web servers cross-domain access controls_



*   HTTP headers that allow servers to describe the set of origins that are permitted to read the information using a web browser
*   Access-Control-Allow-Origin
*   Access-Control-Allow-Credentials
    *   Access-Control-Allow-Headers

Simple Requests


#### Preflighted Requests



*   Contact server for information before actual requests
*   Upon “approval” from the server sending the actual request





#### Credentialed Requests



*   Request accompanied by Cookies or HTTP Authentication information
*   Server responds with Access-Control-Allow-Credentials


## OAuth and User Authentication


### OAuth 1 and OAuth 2

Authorization framework based on open standard for Internet users to log into third party websites using Social network accounts



*   OpenID: complementary service
*   OAuth2: focuses on simplifying client development


### OAuth 2 Roles



*   **Resource Owner**: the user that authorizes a client application to access their account
*   **Client Application**: application that wants to access the resource server, e.g. Express server
*   **Resource Server**: hosting protecting data - e.g. personal information
*   **Authorization Server**: issues an access token to the client application to request resource from resource server



User Agent: the Front-End App


### OAuth 2 Tokens



*   **Access token**: allow access to user daya by the client application
    *   Issued by e.g. Facebook OAuth 2 server
    *   Limited lifetime
    *   Need to be kept confidential
    *   Scope: limit the rights of the access token
*   **Refresh token**: refresh an expired access token


### Client Application Registration

Register the client application on the OAuth service provider



*   Client App Id
*   Client Secret
*   Redirect URL: for the client receiving the authorization code and access token


### Passport-Facebook-Token Module

Passport strategy for authenticating with Facebook using OAuth 2.0 API
