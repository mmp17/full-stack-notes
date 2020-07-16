# More Redux and Client-Server Communication
1. [Redux Actions](#redux-actions)
2. [Redux Thunk](#redux-thunk)
3. [Client-Server Communication](#client-server-communication)
    - [Networking Essentials](#networking-essentials)
4. [Fetch](#fetch)
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
### Networking Essentials
#### Networking Alphabet Soup
- HTTP: Communicating between the client and the server

## Fetch

## React Animations
