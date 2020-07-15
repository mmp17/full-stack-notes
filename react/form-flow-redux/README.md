# React Forms, Flow Architecture and Introduction to Redux
1. [Controlled Forms](#controlled-forms)
2. [Uncontrolled Forms](#uncontrolled-forms)
3. [Redux](#redux)
    - [Model View Controller Framework](#model-view-controller-mvc-framework)
    - [Model View View-Model (MVVM)](#model-view-view-model-mvvm)
    - [Flux Architecture](#flux-architecture)
    - [Intro to Redux](#intro-to-redux)
    - [React with Redux](#react-with-redux)
4. Redux Form

##  Controlled Forms
_Form information is directly tied into the **state** of the component_
- each element maintain its own state
- every state mutation will have  an associated handler function

##  Uncontrolled Forms
- ideally should implement controlled forms
- simpler, limited interaction with components
- use a ref to get form values from the DOM instead of writing an event handler for every state update

## Redux
### Design Patterns
_Architectural pattern, Well-documented solution to a recurring problem_

### Model View Controller (MVC) Framework
_Software engineering architecure pattern_

<img src="https://i.ytimg.com/vi/xTPzz_2jbDc/maxresdefault.jpg" width="600px">

- isolation of domain logic from user interface
- permits independent development, testing, and maintenance

#### Model
- manages the behavior and  data of the application
- responds to requests for state information (from the view)
- responds to requests for change of state (from the controller)
- notifies views when the information changes

#### View
- renders the model into a user interface element
- multiple views can exist for a single model, i.e. a model can have different ways to represent the information

#### Controller
- receives user input and instructs the model and viewport to perform actions

### Model View View-Model (MVVM)
_Model-View-Binder_
- Descendent of MVC

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/MVVMPattern.png/500px-MVVMPattern.png" width="600px">

#### View Model
- Encapsulates that information required for the view
- Abstraction of view that exposes public properties and commands
- Declarative data binding

### Flux Architecture
<img src="https://i.stack.imgur.com/qmqki.png" width="600px">

- Unidirecional Data Flow
    - tackles MVC's cascading flow of updates within the models
    - All updates have unidirecional flow

#### Store
_Storehouse for the application state and any business logics that modifies the state_

#### Action
_Request for changes_

#### Dispatcher
_Controlling unit for serializing any actions request for changing the store_
- No other way to change the state of the application

#### View
_Subscribe to the store_
- When the store updates it state, controller views will re-render parts of views
- Any change want to make in the store because of user's interaction will have to be reflected back to the dispatcher in the form of action

### Intro to Redux
_Realization of Flux-like Architecture_
- Predictable state container for JS apps
- Is different from React
- Single store and single state tree enables powerful techniques:
    - Logging: changes of states
    - API hanlding
    - Undo/redo: of operations
    - State persistence
    - "time-traveling debugging"

#### Main Principles
- Single state object tree within a single store
- State is read-only
    - Changes should only be done through actions
- Changes are made with pure functions
    - Pure function: take previous state and action and return next state
    - No mutation of the previous state

#### Redux Data Flow
<img src="https://www.esri.com/arcgis-blog/wp-content/uploads/2017/09/react-redux-overview.png" width="600px">

- State can only be modified by reducer function

##### Reducer
_Pure functions that take the  current state and action, return a new state_
- Update data immutably

##### State
- Stored in plain JS object

##### Action
_Plain JS object with a type field that specifies how to change something in the state (payload)_

#### Redux Store
_Holds the current state value_
- Created using `createStore()`
- Supplies 3 methods:
    - `dispatch()`: state update with provided action object
    - `getState()`: returns the current state
    - `subscribe()`: accepts a callback cuntion that will be run every time an action is dispatched

### React with Redux
- Use `react-redux` package for binding
    - `connect()`: generates a wrapper "container" component that subscribes to the store
    - Surround the App root with `<Provider>`
        - Takes the store as an attribute
        - Makes store accessible to all connected components
        ```jsx
        <Provider store={store}>
            <BrowserRouter>
              <div className="App">
                <Main />
              </div>
            </BrowserRouter>
        </Provider>
        ```
- `connect()` function takes two optional arguments:
    - `mapStateToProps()`
        - called every time store state changes, return s an object full of data with each field being a prop for the wrapped component
        - state will be mapped into and become available to the props of the component
        ```jsx
        const mapStateToProps = state => {  // state: from redux store
            return {
              dishes: state.dishes,
              comments: state.comments,
              promotions: state.promotions,
              leaders: state.leaders
            }
        }
        ```
    - `mapDispatchToProps()`
        - receives the `dispatch()` method and returns an object full of functions that use `dispatch()`

### React Redux Forms
- Collection of reducer creators and action creators
- Validation support
- Form data stored in Redux store in a model

#### Local Form
_Maps form model to local state of the component_
- Suitable when don't need form data persistence across component

