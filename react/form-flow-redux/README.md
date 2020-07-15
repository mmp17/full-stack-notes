# React Forms, Flow Architecture and Introduction to Redux
1. [Controlled Forms](#controlled-forms)
2. [Uncontrolled Forms](#uncontrolled-forms)
3. [Redux](#redux)
    - [Model View Controller Framework](#model-view-controller-mvc-framework)
    - [Model View View-Model (MVVM)](#model-view-view-model-mvvm)
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



