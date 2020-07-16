# [Code] More Redux and Client-Server Communication
1. [Combining Reducers](#combining-reducers)
2. [Redux Actions](#redux-actions)
3. [Client-Server Communication](#client-server-communication)
4. [Fetch](#fetch)
5. [React Animations](#react-animations)

## Combining Reducers
1. Create a reducer function for each model and delete the `reducer.js` file
```js
// reducer that only manages dishes

import { DISHES } from '../shared/dishes';

export const Dishes = (state = DISHES, action) => {
  switch(action.type) {
    default:
      return state;
  }
}
```
2. Import reducers to `configureStore.js`
```js
import { Dishes } from './dishes';
import { Comments } from './comments';
import { Promotions } from './promotions';
import { Leaders } from './leaders';
```
3. Import `combineReducers` method
```js
import { combineReducers } from 'redux';`
```
4. Implement `combineReducers`
```js
const store = createStore(
  combineReducers({
    dishes: Dishes,
    comments: Comments,
    promotions: Promotions,
    leaders: Leaders
  })
);
```
## Redux Actions
1. Create a `ActionTypes.js` to define various action types by using string constants
```js
export const ADD_COMMENT = 'ADD_COMMENT';
```
2. Create a `ActionCreators.js` and import ActionTypes
```js
import * as ActionTypes from './ActionTypes';
```
3. Create a Action object in `ActionCreators.js`
```js
export const addComment = (dishId, rating, author, comment) => ({
  type: ActionTypes.ADD_COMMENT,
  payload: {   // contains data sent back
    dishId: dishId,
    ...
  }
})
```
4. Implement the reducer function
```js
export const Comments = (state = COMMENTS, action) => {
  switch(action.type) {
    case ActionTypes.ADD_COMMENT:
      var comment = action.payload;
      ...
      return state.concat(comment);    // pushes new comment and returns
    default:
      return state;
  }
}
```
5. Make the action available within components
- obtain action object
```js
import { addComment } from '../redux/ActionCreators';
```
- dispatch the action
```js
const mapDispatchToProps = (dispatch) => ({
  addComment: (dishId, rating, author, comment) => 
        dispatch(addComment(dishId, rating, author, comment))
});
```
- make the action function available within the component
```js
export default withRouter(connect(mapStateToProps, mapDispatchToProps)(Main));
```
- pass in the action function to the elements, to dispatch the action to the store
```js
<DishDetail dish={...}
            addComment={this.props.addComment}
/> 
```


