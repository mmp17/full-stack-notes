## Integrating  the React Client and Server

### Server Side
#### User Authentication
1. Client POST request to /users/login
    1. Request body contains username, pwd
2. Server validates and replies with the token if successful
    2. Response body contains token
3. Client saves the token in local storage
4. Client includes the token in the header of every request
5. Setting authorization header in the fetch request

#### Adding a /comments REST API end point
1. Create a new Comments.js model with a `dish` field that refers to the Dish model
2. Remove the Comment schema from dish.js in the models folder, and also remove the comments property from the Dish schema.
3. Remove the /:dishId/comments and /:dishId/comments/commentId endpoints from `dishRouter.js`
3. Add a new file named commentRouter.js
4. Add the new /comments endpoint in `app.js`

### Client Side


### React Application using Firebase as BaaS
1. Store images in Storage and other data in Database
2. Change auth rule to 
```
allow read; 
allow write if rule.auth != null
```
3. install the firebase module
4. Set up config.js with information in the setting
5. In `ActionCreator.js`, use `firestore.collections("abc")` instead of `fetch`
