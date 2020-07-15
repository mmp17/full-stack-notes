# React Forms, Flow Architecture and Introduction to Redux
1. [Controlled Forms](#controlled-forms)
2. [Uncontrolled Forms](#uncontrolled-forms)
3. Redux
4. Redux Form

##  Controlled Forms
_Form information is directly tied into the state of the component_
- each element maintain its own state
- every state mutation will have  an associated handler function

##  Uncontrolled Forms
- ideally should implement controlled forms
- simpler, limited interaction with components
- use a ref to get form values from the DOM instead of writing an event handler for every state update
