# React Router and Single Page Applications
1. [React Virtual DOM](#react-virtual-dom)

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
