### NodeJS


#### CommonJS API

Defining APIs for common application needs


#### Node Modules


##### Modules

_Self-contained units of functionality that can be shared and reused across projects_



*   Organize and decouple codes, make applications easier to understand and maintain
*   Each file in Node is its own module
*   require function is used to import a module
*   File-based modules
*   Core modules: path, os, fs, util…
*   Third-party modules
*   exports: make module available for import elsewhere


#### Features of JavaScript



*   First-class functions
    *   A function can be treated as any other variable
    *   Functions can be passed as parameters to other functions
*   Closures: 
    *   A function defined inside another function has access to all variables declared in the outer function
    *   The inner function will continue to have access to the variables from the outer scope even after the outer function has returned


#### Asynchronous Programming



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")


Computation 2 turns into callback function for Long-Running Computation


#### Node, Async I/O and Callbacks



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")



##### Single-threaded event loop

_Execute requests one after another_

Node.js is organized into a single-threaded event loop

When the I/O request completes, put the Callback into request queue, then Callback will be handled by the event loop


##### Event Loop



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



#### Express

_Minimalist framework that supports development of server on top of Node.js_



*   Third-party node modules/ frameworks for building HTTP servers
*   Serve up content for consumption by front-end
*   Many third-party middleware to extend functionality


#### Semantic Versioning

&lt;Major Version>.&lt;Minor Version>.&lt;Patch>



*   Major Version: breaking changes
*   Patch: bug fix
*   Exact: @4.0.0
*   Patch:  @”~4.0.0”
*   Minor: @”^4.0.0”

Package-lock.json: additional information that is used by npm to do the correct installation of all the npm modules that are required

--save: save the information that this third-party node module is a dependency in the package.json file


#### Express Middleware

_Functions that have access to the req, res object, and the next function_


##### next

_When invoked, executes the middleware succeeding the current middleware_


##### Morgan

Log information to the screen


#### Express Router 

_Subdivide the application and organize it into multiple mini Express-like applications_

Creates a mini-Express application


##### Body Parser

Middleware to parse the body of the message
