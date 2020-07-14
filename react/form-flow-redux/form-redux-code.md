# React Forms, Flow Architecture and Introduction to Redux

1. [Controlled Forms](#controlled-forms)

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

   
