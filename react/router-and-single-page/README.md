# React Router and Single Page Applications
1. [React Virtual DOM](#react-virtual-dom)
2. [React Router](#react-router)
3. [Single Page Applications (SPA)](#single-page-applications-spa)
4. [Code](https://github.com/vanessaaleung/full-stack-notes/blob/master/react/router-and-single-page/router-code.md)

## React Virtual DOM
_A lightweight Representation of the Browser DOM, a React object_
- Manipulations are extremely fast compared to modifying the browser DOM - In-memory object
- Created completely from scratch on every setState

### Browser DOM
_A browser object_

### Virtual DOM Diffing and Re-rendering
_Do a difference between the previous version of the DOM and the current modified version to notice which parts have changed and need to be re-rendered_
<img src="https://survivejs.com/950d04f6f2ce70288627835f007bb9eb.png" width="300px">

### Updating the DOM
_Run a diffing algorithm to detect nodes that have changed_
- Updates the entire sub-tree
- Use "key" attribute in list items to indicate which items have changed/stable
  - no need to re-render where keys do not change
- React Fiber
  - new reconciliation algorithm
  - faster in performing diffing
  - incremental rendering

## React Router
_Collection of navigational components_
- Enable navigation among views
- Router components, Route matching components, and Navigation components
- Route passes 3 props to the component
  - match: provides information about how a <Route path> matched the URL
  - location: URL location
  - history will allow you to go back

### Web App Routing
- `react-router-dom`
- Router component: `<BrowserRouter>`
  - Creates specialized history object
  - `<HashRouter>` if using a static file server, enable navigation to URLs that contain hashes
  - Enclose the app in BrowserRouter
  
### Route Matching
-_Route Matching components: `<Route>` and `<Switch>`_
- `<Route>` path: enable specification of the current location's pathname
- `<Route>` component: specifies the corresponding view for the location
    ```jsx
    <Route path="/home" component={HomePage} />
    ```
-  `exact` attribute: ensures the path must be exactly matched
    ```jsx
    <Route exact path="/home" ... />
    ```
- `<Redirect>`: default route specification, anything that doesn't match the `<Route>`s will be redirected to the location
    ```jsx
    <Redirect to="/home" />
    ```
- `<Switch>`: grouping together several routes
  - iterate over all the childrean and find the first matches the path

### Router Parameters
- Can be specified in the path specification as a token, e.g., `menu/:id` where id is the token
- Can be specified using a link parameter, e.g. `<Link to{`/menu/${dish.id}`} >`
- match Object
  - params: key/value pair parsed from the URL
  - e.g. `/menu/42` will result in `match.params.id`: `42`

### Navigation
_Supported through `<Link>` and `<NavLink>`_
- `<Link>`: creates links in the application, rendered as `<a>`
- `<NavLink>`: attaches the active CSS class to the link when its prop matches the current location

## Single Page Applications (SPA)
_A web application that fits in a single page_
- No need to reload the entire page
- Most resources are retrieved with a single page load
- Redraw parts of the  page without requiring a full server roundtrip
