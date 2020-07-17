# More Redux and Client-Server Communication
1. [Redux Actions](#redux-actions)
2. [Redux Thunk](#redux-thunk)
3. [Client-Server Communication](#client-server-communication)
    - [Networking Alphabet Soup](#networking-alphabet-soup)
    - [Client-Server Communication](#client-server-communication)
    - [Hypertext Transfer Protocol (HTTP)](#hypertext-transfer-protocol-http)
    - [Web Services](#web-services)
    - [Representational State Transfer (REST)](#representational-state-transfer-rest)
4. [Fetch](#fetch)
    - [Promises](#promises)
5. [React Animations](#react-animations)
6. [Code](https://github.com/vanessaaleung/full-stack-notes/blob/master/react/redux-client-server/redux-client-server-code.md)

## Redux Actions
_Payloads of information that send data from your application to the store_
- Done through `store.dispatch()`
  ```js
  const mapDispatchToProps = (dispatch) => ({
    addComment: (dishId, rating, author, comment) => 
          dispatch(addComment(dishId, rating, author, comment))
  });
  ```
- Contains
  - type: indicates the type of action to be performed, best supported by String constants
  - data necessary for the action
  
### Action Creators
_Functions that create actions_
- Encapsulate the process of creating the action objects, and returns the action object
- Resulting action can be passed to the store through `dispatch()`
```js
export const addComment = (dishId, rating, author, comment) => ({
  type: ActionTypes.ADD_COMMENT,
  payload: {   // contains data sent back
    dishId: dishId,
    rating: rating,
    author: author,
    comment: comment
  }
})
```

### Actions and Reducers
- Reducers take the previous state and action, return the next state
- Actions typically handled through a switch statement switching on the action type
  ```js
  export const Comments = (state = COMMENTS, action) => {
    switch(action.type) {
      case ActionTypes.ADD_COMMENT:
        var comment = action.payload;
        ...
        return state.concat(comment);
      default:
        return state;
    }
  }
  ```
- Returns the previous state in the default case

### Splitting and Combining Reducers
- Split the reducer into simpler reducer funcitons that manage only parts of the global state
- Re-combine the simpler functions to generate the overall state
  ```js
  const store = createStore(
    combineReducers({
      dishes: Dishes,
      comments: Comments,
      promotions: Promotions,
      leaders: Leaders
    })
  );
  ```
## Redux Thunk
### Redux Middleware
_Provides capability to run code after an action is dispatched, but before it reaches the reducer_
- Enable third-party extension to be injected into the Redux application
- e.g. logging: want to log all the actions dispatched
- e.g. async API calls: dispatch an action that requires access to a server (where to fetch the data), and send the data to the redux store

#### How Middleware Works
- Forms a pipeline that wraps around the `dispatch()`
- Make any changes needed and Pass actions onward
- Restart the dispatch pipeline
- Access the store state

#### Usage
- Inspecting the actions and the state
- Modify actions
- Dispatch other actions before allowing this action to take place
- Stop actions from reaching the reducers
- `applyMiddleware()`: sets up the middleware pipeline, returns a `store enhancer` that is passed to `createStore`

### Thunk
_A subroutine used to inject an additional calculation in another subroutine_
_A function that returns a function_
- e.g.: delay a calculation until its result is needed
- e.g.: insert operations at the beginning/end of the other subroutine

### Redux Thunk
_Middleware that allows you to write action creators that return a function instead of an action_
- Be used to delay the dispatch of an action
- Dispatch only if a certain condition is met
- Useful for complex synchronous logic
  - Multiple dispatches
  - Conditional dispatches: e.g. dispatch different actions based on the API call returns successful/failure
  - Simple Async logic
- Redux Saga: use ES6 generators to control pausable functions
  - ongoing "background thread" like processing behavior

## Client-Server Communication
### Networking Alphabet Soup
- HTTP: Communicating between the client and the server, application layer protocol
- URL: Uniform  Resource Locator, string of characters seperated by slashes
- JSON: JavaScript Object Notation, encoding data that is being shipped from the server side to the client side, or vice versa
- XML: another way of encoding data
- SOAP: higher level protocol that allows communication between distributed entities within the network
- REST: Representational State Transfer
- GET, PUT, POST, DELETE

### Client-Server Communication
- Network operations cause unexpected delays
- Application need to recognize the asynchronous nature of communication - data is not instantaneously available

### Hypertext Transfer Protocol (HTTP)
_Encoding the messages exchanged between client and server side_
- Allows retrieving interlinked text documents
- HEAD, GET, POST, PUT, DELETE, TRACE, OPTIONS, CONNECT

#### HTTP Request Message
<img src="https://www3.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_RequestMessageExample.png" width="500px">

#### HTTP Response
##### Response Message
<img src="https://www3.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_ResponseMessageExample.png" width="500px">

- Status Line: how the request has been processed and what is being sent back to the client is stored
- Header: what is contained in the response message

##### Response Codes
<img src="https://www.steveschoger.com/status-code-poster/img/status-code.png" height="500px">

##### Data Format
- eXtensible Markup Language (XML)
- Javascript Object Notation (JSON), mainly use
    - Lightweight data interchange format
    - Language independent
    - A collection of name/value pairs
    
### Web Services
_A system designed to support interoperability among systems that are connected over a network_
- Service oriented architecture (SOA)
- Provide a standardized way for two machines that are connected to Internet to be able to communicate with each other at the application layer level using open stadards

#### Two Common Approaches
- SOAP (Simple Object Access Protocol) based
    - Use WSDL (Web services Description Language) to specify how two endpoints communicate with each other
    - XML format messages
- REST (Representational State Transfer)
    - Exchange of data using XML/ JSON
    - Simpler than SOAP, WSDL

### Representational State Transfer (REST)
_A style of software architecture for distributed hypermedia systems such as WWW_

#### Basic Design Principles
- Use HTTP methods explicitly
- Stateless: the server doesn't store any info about the state
- Expose directory structure-like URLs to provide resources
- Transfer using XML, JSON, or both

#### REST Concepts
<img src="https://image.slidesharecdn.com/asitrest-150317020843-conversion-gate01/95/learn-rest-api-at-asit-6-638.jpg?cb=1426576159" width="300px"> 

- Nouns (Resources)
    - identified by URLs, e.g. `http://www.conFusion.food/dishes/`
    - can be document, image, a collection of resources, etc.
- Verbs
    - specify the action to be done on the resources
    - e.g. GET: READ, POST: CREATE, PUT: UPDATE, DELETE:  DELETE
- Representations
    - how to encode the information
    - JSON or XML
    
#### Stateless Server
- Server side should not track the client state
    - Every request is a new request from the client
- Client side should track its own state
    - e.g. using cookies, client side database
    
## Fetch
### Promises
_Mechanism that supports asynchronous computation_
- Proxy for a value not necessarily konwn when the promise is created
- Represents a value that may be available now/future/never

<img src="https://javascript.info/article/promise-basics/promise-resolve-reject.svg" width="500px">

- Solves the callback hell (heavily nested callback code) problem
- Can be chained
- Can immediately return
    - Promise.resolve(Result)
    - Promise.reject(error)

### Fetch



## React Animations
