# More Redux and Client-Server Communication
1. [Combining Reducers](#combining-reducers)
2. [Redux Thunk](#redux-thunk)
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







