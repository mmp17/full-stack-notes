## Integrating  the React Client and Server
### User Authentication
1. Client POST request to /users/login
    1. Request body contains username, pwd
2. Server validates and replies with the token if successful
    2. Response body contains token
3. Client saves the token in local storage
4. Client includes the token in the header of every request
5. Setting authorization header in the fetch request
