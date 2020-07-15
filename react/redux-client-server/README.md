# More Redux and Client-Server Communication
1. [Redux Actions](#redux-actions)
2. [Redux Thunk](#redux-thunk)
3. [Client-Server Communication](#client-server-communication)
4. [Fetch](#fetch)
5. [React Animations](#react-animations)
6. [Code](https://github.com/vanessaaleung/full-stack-notes/blob/master/react/redux-client-server/redux-client-server-code.md)

## Redux Actions
_Payloads of information that send data from your application to the store_
- Done through `store.dispatch()`
- Contains
  - type: indicates the type of action to be performed, best supported by String constants
  - data necessary for the action

### Action Creators
_Functions that create actions_
- Encapsulate the process of creating the action objects, and returns the action object
- Resulting action can be passed to the store through `dispatch()`

### Actions and Reducers
- Reducers take the previous state and action, return the next state
- Actions typically handled through a switch statement switching on the action type
- Returns the previous state in the default case

### Splitting and Combining Reducers
- Split the reducer into simpler reducer funcitons that manage only parts of the global state
- Re-combine the simpler functions to generate the overall state

## Redux Thunk

## Client-Server Communication

## Fetch

## React Animations
