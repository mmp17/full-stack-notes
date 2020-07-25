# UI Elements and Redux
1. [Redux](#redux)
    - [Flux Architecture](#flux-architecture)
    - [Main Principles of Redux](#main-principles-of-redux)
    - [Redux Data Flow](#redux-data-flow)
    - [Redux Thunk](#redux-thunk)
    - [Fetch](#fetch)
    
## Redux
### Flux Architecture
- Any changes to the store have to be initiated through actions that are dispatched from the application
- Dispatcher: ensure actions are properly managed
- View: watch the store state and re-render if needed
<img src="https://facebook.github.io/flux/img/overview/flux-simple-f8-diagram-explained-1300w.png" width="600px">

### Main Principles of Redux
- Single state object tree within a single store
- State is read-only
  - changes should only be done through actions
- Changes are made with pure functions
  - Take previous state and action, returns next state
  - **No mutation** of the previous state

### Redux Data Flow
- **Uni-direction**
- State: controlled through reducer
- Reducers: receive actions through Dispatch, result in a new state being generated
- Views: re-render based on the state changes
<img src="https://miro.medium.com/max/2400/1*Z51D-5uz7hNWakGIbG_bQA.png" width="600px">

### Redux Thunk
_Middleware that allows you to write action creators that return a function intead of an action_
- Can be used to delay the dispatch of an action
- Dispatch only if a certain condition is met

### Fetch
_Communication with Server_
- XMLHttpRequest(): outdated
- Fetch API: modern replacement
  - Promisebased
  - provides an interface for fetching resources
