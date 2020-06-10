### Database


#### Express Generator

Quick scaffolding tool to generate an Express application skeleton


##### Generated Application



*   app.js: starting application
*   package.json
*   public: static resources
*   routes: application routes
*   views: template engine templates


#### Why NoSQL

Scalability



*   Availability
*   Consistency
*   Partition tolerance

Ease of deployment



*   No object-relational mapping required
*   Document databases: MongoDB
    *   Document: **Self-contained** piece of information
    *   E.g. JSON
    *   Collection: a group of documents
    *   Database: a set of collections
    *   Server can support multiple databases
*   Key-value databases: Redis
*   Column-family databases: Cassandra
*   Graph databases: Neo4j


#### MongoDB

_Stores data in the form of documents_


```
sudo lsof -iTCP -sTCP:LISTEN -n -P
```



```
sudo kill <mongo_command_pid>
```



```
mongod --dbpath=data --bind_ip 127.0.0.1
```


Stores the documents in BSON (Binary JSON) format



*   Supports length prefix on each value: easy to skip over a field
*   Information about the field type

ObjectId

Unique for each document, created by default

12 byte field



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")


Timestamp: resolution of a second

Machine ID: the machine the server is running on

Process ID: the process that created the document

Increment: distinguish documents stored within the same secondCallback Hell



*   Heavily nested callback code
    *   Write code top to bottom
    *   Pyramid of doom
*   Use promises


#### Promise

_Mechanism that supports asynchronous computation_



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")


Can be chained

Consumers of promise are notified of the fulfillment (.then) or rejection (.catch) of the promise


#### Mongoose


##### DOM

_Adds structure to MongoDB documents with schema_



*   Object Data Model
*   Object Document Mapping
*   Object Relational Mapping


##### Schema



*   structure of data to be stored
*   Be Used to create a Model function
*   Can be  nested


##### Full-Fledged REST API Server

Doing business logic in the Express server

Doing the interaction with the database from the node application from Express server which is a node application using Mongoose



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



##### HTTP Request to Database Operation Mapping



1. Every incoming request needs to be decoded to decide the nature of the request
    1. GET, PUT, POST, DELETE
    2. Resource affected
    3. Data in the body of the request
2. Translate request to an equivalent database operation
