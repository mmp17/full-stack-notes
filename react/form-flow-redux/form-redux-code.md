# React Forms, Flow Architecture and Introduction to Redux

1. [Controlled Forms](#controlled-forms)
2. [Controlled Form Validation](#controlled-form-validation)
3. [Uncontrolled Forms](#uncontrolled-forms)
4. [Redux](#redux)
5. [React Redux Form)(#react-redux-form)

## Controlled Forms
1. Import components
```javascript
import { Button, Form, FormBroup, Label, Input, Col } from 'reactstrap';
```

2. Set up properties that are linked to the form in state
```javascript
this.state = {
    firstname: '',
    lastname: '',
    telnum: '',
    email: '',
    agree: false,
    contactType: 'Tel.',
    message: ''
}
```
3. Create the form
- `<FormBroup row>`: occupies a row
- `htmlFor="firstname"`: avoid confusion with javascripts' `for`
- `md={10}`: occupies 10 columns
- `name="firstname"`: ties to the Label
- `value={this.state.firstname}`: ties to the state
```jsx
<Form>
    <FormBroup row>
        <Label htmlFor="firstname" md={2}>First Name</Label>
        <Col md={10}>
            <Input type="text" id="firstname" 
                    name="firstname" placeholder="First Name"
                    value={this.state.firstname} />
        </Col>
    </FormBroup>
</Form>
```

4. Handle Submission
- Submit button
```javascript
<Col md={{size: 10, offset: 2}}>
    <Button type="submit" color="primary">
        Send Feedback
    </Button>
</Col>
```
- handleSubmit
  - `event.preventDefault();`: prevent the browser to go to the next page
```javascript
handleSubmit(event) {
    console.log("Current State is: " + JSON.stringify(this.state));
    alert("Current State is: " + JSON.stringify(this.state));
    event.preventDefault();
}
```

- handleInputChange
```javascript
handleInputChange(event) {
    const target = event.target;  // retrieve target input
    const value = target.type === 'checkbox' ? target.checked : target.value;
    const name = target.name; // retrieve field name

    this.setState({
        [name]: value
    })
}
```
- Implement the functions
```jsx
<Form onSubmit={this.handleSubmit}>
```
```jsx
<Input type="text" id="firstname" name="firstname" placeholder="First Name"
        value={this.state.firstname}
        onChange={this.handleInputChange} />
```
- Bind the functions
```javascript
this.handleSubmit = this.handleSubmit.bind(this);
```

## Controlled Form Validation
1. Add `touched` to the state
```javascript
touched: {
    firstname: false,
    lastname: false,
    telnum: false,
    email: false
}
```

2. Add the `handleBlur` method to indicate which field has been modified
```javascript
handleBlur = (field) => (event) => {
    this.setState({
        touched: { ...this.state.touched, [field]: true}
    });
}
```
- Bind the functions
```javascript
this.handleBlur = this.handleBlur.bind(this);
```

3. Implement the `handleBlur` method in each field
```jsx
onBlur={this.handleBlur('firstname')}
```
4.  Add the `validate` method:
```javascript
validate(firstname, lastname, telnum, email) {
    const errors = {
        firstname: '',
        lastname: '',
        telnum: '',
        email: ''
    };

    if (this.state.touched.firstname && firstname.length < 3) {
        errors.firstname = 'First Name should be >= 3 characters';
    }
    else if (this.state.touched.firstname && firstname.length > 10) {
        errors.firstname = 'First Name should be <= 10 characters';
    }
}
```
5. Display the errors in the form
```jsx
<FormFeedback>{errors.firstname}</FormFeedback>
```
6. Set the valid flag for each field
```jsx
valid={errors.firstname === ''}
invalid={errors.firstname !== ''}
```

## Uncontrolled Forms
1. Create the form
```jsx
<Form onSubmit={this.handleLogin}>
  <FormGroup>
    <Label htmlFor="username">Username</Label>
    <Input type="text" id="username" name="username" />
  </FormGroup>
  ...
  <Button type="submit" value="submit" className="bg-primary" color="primary">Login</Button>
</Form>
```
2. Retrieve input directly from the DOM
```javascript
handleLogin(event) {
    this.toggleModal();
    alert(" Username: " + this.username.value + 
          " Password: " + this.password.value +
          " Remeber: " + this.remember.checked);
    event.preventDefault();
}
```
3. Add the `innerRef` to the `Input`
```jsx
innerRef={(input) => this.username = input}
```
## Redux
1. Install redux & react-redux
```shell
npm install redux react-redux
```
2. Add a `reducer.js` file to implement reducer functions
3. Create a initialState const
```javascript
export const initialState = {
  dishes: DISHES,
  comments: COMMENTS,
  leaders: LEADERS,
  promotions: PROMOTIONS
}
```
and remove state from the component
4. Implement the `Reducer` function
```javascript
export const Reducer = (state = initialState, action) => {
  return state;
};
```
5. Add a `configureStore.js` file to store the configuration
```javascript
import { createStore } from 'redux';
import { Reducer, initialState } from './reducer';
```
6. Implement the `ConfigureStore` method to configure Redux Store
```javascript
export const ConfigureStore = () => {
  const store = createStore(
    Reducer, 
    initialState
  );

  return store;
}
```
7. Make use of the store
- In `App.js` import
```javascript
import { Provider } from 'react-redux';
import { ConfigureStore } from './redux/configureStore';
```
- Makes store accessible to all connected components
```jsx
const store = ConfigureStore();
```
```jsx
<Provider store={store}>
    <BrowserRouter>
      <div className="App">
        <Main />
      </div>
    </BrowserRouter>
</Provider>
```
8. Connect React component with Redux store
```javascript
import { withRouter } from 'react-router-dom';
import { connect } from 'react-redux';
```
- `withRouter`: connect component to React Router
- `connect()`: generates a wrapper "container" component that subscribes to the store
```jsx
export default withRouter(connect(mapStateToProps)(Main));
```
- `mapStateToProps()`:state will be mapped into and become available to the props of the component
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
- change `this.state.xxx` to `this.props.xxx`
```jsx
<Home dish={this.props.dishes.filter(...)} />
```
   
## React Redux Form
1. Install the package
```shell
npm install react-redux-form
```
2. Get rid of state, handleInputChange, handleBlur, , validate, and `FormFeedback`, which will all be managed automatically by `react-redux-form`
3. Replace `<FormGroup row>` with `<Row className="form-group">`
4. Replace `<Input>` with `<Control.text>`, get rid of `type={} valid={} invalid={} onBlur={} onChange={}`, add `model="firstname"` and `className="form-control"`
5. Replace `<FormGroup check>` with `<div className="form-check">`, replace `<Input type="checkbox">` with `<Control.checkbox className="form-check-input">`, get rid of `checked={}` 
6. Replace `<Input type="select">` with `Control.select`
7. Replace `<Input type="textarea">` with `Control.textarea`
8. Edit the `handleSubmit` function to
```javascript
handleSubmit(values) {
    console.log("Current State is: " + JSON.stringify(values));
    alert("Current State is: " + JSON.stringify(values));
}
```
