### User Authentication


#### Basic Authentication


##### Authorization Header



*   “Username:password”, encoded using Base64
*   Authorization method and a space
*   e.g. `Authorization: Basic QSxhZGGRpbjp==`


##### Express and Authentication



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")



##### HTTP Cookies

_Small piece of data sent from a web server and stored on the client side_



*   Has expiry date


##### Express and  Cookies

Cookies are parsed in Express server


##### Signed cookie

_Signed with a secret key on the server side_



*   A secret key is a specific string that only the server knows
*   Digital signature with key-has message authentication code, includes in the cookies


##### Express Sessions

_Combination of cookie with session id and server-side storage of information indexed by session id_

When a client sends a request over the server, then from within the cookie the session ID is retrieved and that is used as an index into the server side.

Session information:



*   Stored by default in-memory, wiped out when server restarts
*   Stored in permanent store on server side: session-file-store
*   Distributed session store if using multiple replicated servers, to ensure reliability of server operation


##### Passport

_Authentication middleware for Node.js_



*   Supports various strategies for authentication
    *   Local strategy: registering/authenticating users into your system using a username and password
    *   OpenID
    *   Oauth (Facebook, G+, etc.) single sign-on
*   Supports sessions
*   Passport-Local-Mongoose module, makes available Mongoose schema support for managing users


##### Token Based Authentication



*   Server will issue a token to a validated user, and all subsequent request coming from the client, will bear the token in the request
*   Why?
*   Session authentication have problem when need stateless servers and scalability
*   Mobile application have a hard time handling cookies/sessions
*   Cross-origin resource sharing (CORS) problem
*   Cross-site request forgery (CSRF)
*   How
    *   User requests access with username & password
    *   Server validates credentials
    *   Server creates a signed token and sends to the client
    *   All subsequent requests from the client should include the token
    *   Server verifies the token and  response  with data if validated
*   JSON Web Tokens(JWT)
    *   Encoded into a long string



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")




    *   Header: algorithm of encoding the JWT and type of the token
    *   Payload: carry information that identify the user, e.g. id
    *   Signature
        *   how the token is encoded
        *   A secret key on the server side for encoding the JWT
    *   Jsonwebtoken Node module
    *   Passport-JWT
        *   Authenticate RESTful endpoints using JWT without needing sessions


##### Mongoose Population

_Population is the process of automatically replacing specified paths within a document with documents from another collection_



*   Store the reference  to the other document in the form of the object ID in the document you want to populate the information
