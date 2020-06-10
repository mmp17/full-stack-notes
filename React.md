### React

_A JavaScript library for building user interfaces_


#### State

To “remember” things, components use **state**.

React components can have state by setting **this.state** in their constructors. this.state should be considered as private to a React component that it’s defined in. 

All React component classes that have a constructor should start with a super(props) call.

When you call setState in a component, React automatically updates the child components inside of it too.

It's conventional to use[Event] names for props which represent events and handle[Event] for the methods which handle the events.

Why immutable:



1. Detect changes, store past versions

It’s strongly recommended that you assign proper keys whenever you build dynamic lists.

Generally, if you refer to a method without () after it, such as onClick={this.handleClick}, you should bind that method.

[https://reactjs.org/docs/handling-events.html](https://reactjs.org/docs/handling-events.html)

React element has to return only one element.


#### React component Lifecycle



*   Three Stages
    *   Mounting
    *   Updating
    *   Unmounting: no longer needed


#### Functional Component

Cannot have local state


#### Virtual DOM



*   Lightweight representation of browser DOM
*   Tree data structure
*   From scratch every time calling every setState
*   Modify the browser DOM correspond to the changes of the virtual DOM
*   Using “key” no need to re-render where key do not change


#### Switch

Renders the first child [&lt;Route>](https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Route.md) or [&lt;Redirect>](https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Redirect.md) that matches the location.


#### Model-View-Controller Framework



*   Isolation of domain logic from the user interface
*   Permits independent development, testing, and maintenance



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")


Controller: accepts input from the user and instructs the model and viewport to perform actions based on that input


#### Flux Architecture



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")


Store: store the state, business logic behind the state

Requesting store: modify the state

Dispatcher: serializing actions that request for changing the store

View: cannot directly change the store


#### Redux

Realization of Flux architecture

Predictable state container for JavaScript apps


##### Principle of Redux



1. Single source of store: single state object
2. State is read-only: change should only be done through actions
3. Changes are made with pure functions: no mutation of the previous state, take the previous state and return the new state


##### Redux Overflow



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")




*   State can only be modified using Reducer function (takes state & action as params),  which returns the next state
*   State: store in plain JS object,  holds current state value
*   Action: payloads of information that send data to store. 
    *   create with action creator
    *   the type field indicates the type of action being performed
    *   only source of information for the store
*   Reducer: pure function, takes the current state and returns next state, update data immutably

&lt;Provider>: take store as an attribute, makes store  accessible to all connected components


#### &lt;React.Fragment>

A common pattern in React is for a component to return multiple elements. Fragments let you **group a list of children **without adding extra nodes to the DOM.


#### Redux Middleware

Run the code after an action is dispatched, but before it reaches reducer



*   Inspecting the action & state
*   Modify the action
*   Dispatch other actions
*   Stop actions from reaching reducers


#### Redux Thunk



*   Multiple dispatches
*   Conditional dispatch
*   Async logic


#### Redux Saga



*   Ongoing background thread


#### Client & Server Communication

Need to handle delay in client-side



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.png "image_tooltip")



#### Network Alphabet Soup


##### HTTP

Hypertext Transfer Protocol, Application layer protocol


##### 

<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image5.png "image_tooltip")



##### HTTP Request Message



*   Request Line: GET /index.html HTTP/1.1
*   Headers
    *   Host:  localhost:3000
    *   Connection
    *   User-agent
    *   accept-encoding
*   Blank Line
*   Body


##### HTTP Response Message



*   Status Line: HTTP/1.1 200 OK
*   Headers
    *   Connection
    *   Content-type
    *   Date
    *   transfer-encoding
*   Blank Line
*   Response Data: HTML code



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image6.png "image_tooltip")



##### URL

Uniformed Resource Locator


##### JSON

JavaScript Object Notation: Encodes data between client and server-side


##### XML

eXtensible Markup Language: Another way of encoding data


#### Web Services

_A system designed to support interoperability of systems connected over a network_

_A standardized way of integrating web-based applications using open standards operating over the Internet_


##### SOAP

Simple Object Access Protocol



*   XML based
*   Uses WSDL (Web Services Description Language)


##### REST

_A collection of network architecture **principles** which outline how resources can be made available on servers_



*   Representational State Transfer
*   Exchange data based on XML/JSON, simpler
*   Build on HTTP protocols
*   Design principles:
    *   Use HTTP methods explicitly
    *   Stateless
        *   Server-side should not track the client-side: every request is a new request from the client
        *   Client-side should track its own state, using cookies, client-side database etc.
        *   server doesn’t store any information about the state after the communication is complete
    *   Expose directory-structure like URLs: to identify resources
    *   Transfer using XML, JSON



<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image7.png "image_tooltip")




*   Resource: 
    *   Abstraction of information
    *   Image, document, collection of resources
    *   Identified by URIs, directory structure: http://www.name.food/dishes/
*   Verbs
    *   PUT: UPDATE
    *   POST: CREATE
    *   GET: request for information, transfers the data from the server to the client in representation like XML, JSON


##### Representations

_How data  is represented/returned to the client for presentation_


#### Promise

_Proxy for a value not necessarily known when the promise is created_

Represents a value that may be available now or in the future



<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image8.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image8.png "image_tooltip")




<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image9.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image9.png "image_tooltip")




*   Why Promises
    *   Solves heavily nested callback code problem
    *   Promises can be chained
    *   Can immediately return


#### Fetch



*   Replacement for XMLHttpRequest() -> XHR
*   Provides an interface for fetching resources
*   Promise based
*   Abstractions
    *   Request
    *   Response
    *   Headers
    *   Body

        ```
fetch(baseURL + 'dishes')
.then(response => response.json())
.then(data =>  console.log(data))
.catch(error => console.log(error.message));
```



 \
Fetch Posting data


```
fetch(baseURL + 'comments', {
method: 'POST',
body: JSON.stringify(newComment),
headers: ...,
credentials:
})
```



#### React Transition Group

A set of components for managing component states over time


##### CSS Transition

Applies a pair of class names during the appear, enter, and exit stages of the transition


##### Transition  Group

Transition between groups


##### React Animation Components

A set of components implemented using react-transition-group


#### Webpack



*   Module bundler
*   Builds a dependency graph
*   Treats every file as a module


##### Bundle

A JavaScript file that incorporates assets



*   Entry: the start point
*   Output: where to bundle
*   Loaders: transforms files to bundles as they are added to the dependency graph
*   Plugins:  perform actions and custom functionality on chunks of bundled modules 
