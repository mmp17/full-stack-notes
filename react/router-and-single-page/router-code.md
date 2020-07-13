# React Router and Single Page Applications
  1. [React Fragment](#react-fragment)
  2. [React Router](#react-router)

## React Fragment
_Enable to group a bunch of React elements, alternative way of div_
- long form
```jsx
<React.Fragment>
```
- short form
```jsx
<></>
```
- use `<div>` will add in one more node into the DOM, while React Fragment won't

## React Router
1. Enclose the app in BrowserRouter
```jsx
import { BrowserRouter } from 'react-router-dom';
...
<BrowserRouter>
  <div className="App">
    ...
  </div>
</BrowserRouter>
```
2. Configure the Router
- `<Switch>`: grouping together several routes
```jsx
<Switch>
  <Route path="/home" component={HomePage} />
  ...
  <Redirect to="/home" />
</Switch>
```

3. If need to pass in a props to the component
  - Method 1: Define function component inline
```jsx
<Route path="/menu" component={() => <Menu dishes={this.state.dishes} /> } />
```
  - Method 2: explicitly declare the function component
```jsx
const HomePage = () => {
  return (
    <Home />
  );
}
...
<Route path="/home" component={HomePage} />
```

4. Configure `<NavLink>`
- `<NavLink>`: attaches the active CSS class to the link when its prop matches the current location
```jsx
<Nav navbar>
  <NavItem>
    <NavLink className="nav-link" to="/home">
      <span className="fa fa-home fa-lg"></span>&nbsp;&nbsp;Home
    </NavLink>
  </NavItem>
</Nav>
```









