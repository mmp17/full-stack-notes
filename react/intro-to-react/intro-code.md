# Introduction to React
1. [Reactstrap Configuration](#reactstrap-configuration)
2. [React Component](#react-component)

## Reactstrap Configuration
1. Install `reactstrap`
```shell
yarn add bootstrap@4.0.0
yarn add reactstrap@5.0.0
yarn add react-popper@0.9.2
```
2. Use Bootstrap4
Add following codes to `index.js`:
```javascript
import 'bootstrap/dist/css/bootstrap.min.css';
```
3. Adding a Navigation Bar
Add following codes to `App.js`:
```javascript
import { Navbar, NavbarBrand } from 'reactstrap';

class App extends Component {
  render() {
    return (
      <div className="App">
        <Navbar dark color="primary">
          <div className="container">
            <NavbarBrand href="/">Ristorante Con Fusion</NavbarBrand>
          </div>
        </Navbar>
      </div>
    );
  }
}
```
## React Component
### Basic Structure
1. Create a component in `MenuComponent.js`
```javascript
import React, { Component } from 'react';

class Menu extends Component {
    ...
}

export default Menu;
```
2. Add a constructor
```javascript
constructor(props) {
        super(props);     // supply the props to the super class
        ...
} 
```
3. Add render() method
- Any react component should implement the `render()` method
```javascript
render() {
    return (...);
}
```
4. Export the component
```javascript
export default Menu;
```
### Adding contents for the component
5. Add return content
```javascript
const menu;

return (
  <div className="container">
    <div className="row">
      <Media list>
        {menu}
      </Media>
    </div>
  </div>
);
```
6. Add state in constructor
```javascript
this.state = { // stores properties the component can make use of
  dishes: [...]
}
```
7. Make use of the dishes and construct the menu
- `key={dish.id}`: when construct a list of items, every item needs a key attribute to be specified for it. Helps React recognize each item.
- `mt-5`: top margin of 5
- `tag="li"`: so can display a list of item
```javascript
const menu = this.state.dishes.map((dish) => {
  return (
    <div key={dish.id} className="col-12 mt-5">
      <Media tag="li">...</Media>
    </div>
  );
});
```
8. Make use of the menu Component to `App.js`
```javascript
import Menu from './components/MenuComponent';
...
<Menu />
...
```
### State and Props
1. Add a `shared` subfolder under `src` to store all information that is used by components
2. Update `App.js` to add dishes to the state
3. Pass dishes to the Menu component
```javascript
<Menu dishes={this.state.dishes}/>
```
4. Update `MenuComponent`to make use of the props
```javascript
const menu = this.props.dishes.map((dish) => {
```
