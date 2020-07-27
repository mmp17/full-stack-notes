# [Code]React Native UI Elements and Redux
1. [Icons and Buttons](#icons-and-buttons)
2. [Redux](#redux)
3. [React Debugging](#react-debugging)

## Icons and Buttons
- `raised`: add box shadow to button
- `reverse`: reverses color scheme
```js
<Icon raised
  reverse
  name={ props.favorite ? 'heart' : 'heart-o'}
  type="font-awesome"
  color='#fc9d9d'
  size={20}
  onPress={() => 
    props.favorite ? console.log('Already favorite') : props.onPress()} 
/>
```
## Redux
### Setting up Redux
1. Install packages
```shell
yarn add redux react-redux redux-thunk redux-logger
```
2. Create a `baseUrl.js` file and specify the address of the server
```js
export const baseUrl = 'http://localhost:3001/';
```
3. Create a redux folder
4. Create a `ActionTypes.js` to store all the action types
```js
export const DISHES_LOADING = 'DISHES_LOADING';
export const ADD_DISHES = 'ADD_DISHES';
export const DISHES_FAILED = 'DISHES_FAILED';
```
4. Create a `configureStore.js`
- import packages
```js
import { createStore, combineReducers, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import logger from 'redux-logger';
```
- import reducers
```js
import { dishes } from './dishes';
import { comments } from './comments';
import { promotions } from "./promotions";
import { leaders } from "./leaders";
```
- configure store
```js
export const ConfigureStore = () => {
  const store = createStore(
    combineReducers({
      dishes,
      comments,
      promotions,
      leaders
    }),
    applyMiddleware(thunk, logger)
  );

  return store;
}
```
5. Create reducers files
```js
import * as ActionTypes from './ActionTypes';

export const dishes = (state = {
  isLoading: true,
  errMess: null,
  dishes: []
}, action) => {
  
  switch(action.type) {
    case ActionTypes.ADD_DISHES:
      return {...state, isLoading:false, errMess: null, dishes: action.payload};

    case ActionTypes.DISHES_LOADING:
      return {...state, isLoading:true, errMess: null, dishes: []};

    case ActionTypes.DISHES_FAILED:
      return {...state, isLoading:false, errMess: action.payload, dishes: []};
       
    default:
      return state;
  }
}
```
6. Create `ActionCreators.js`
```js
import * as ActionTypes from './ActionTypes';
import { baseUrl } from '../shared/baseUrl';

export const fetchDishes = () => (dispatch) => {
  dispatch(dishesLoading());

  return fetch(baseUrl + 'dishes')
        .then(response => {
          if (response.ok) {
            return response;
          }
          else {
            var error = new Error('Error ' + response.status + ': ' + response.statusText);
            error.response = response;
            throw error;
          }
        },
        error => {
          var errMess = new Error(error.message)
          throw errMess;
        })
        .then(response => response.json())
        .then(dishes => dispatch(addDishes(dishes)))
        .catch(error => dispatch(dishesFailed(error.message)))
};

export const dishesLoading = () => ({
  type: ActionTypes.DISHES_LOADING
});

export const dishesFailed = (errmess) => ({
  type: ActionTypes.DISHES_FAILED,
  payload: errmess
});

export const addDishes = (dishes) => ({
  type: ActionTypes.ADD_DISHES,
  payload: dishes
});
```
### Using Redux in React Native
1. Connect Redux to the app in `App.js`
- get the store
```js
import { ConfigureStore } from './redux/configureStore';

const store = ConfigureStore(); // will return store
```
- connect the app with store
```js
<Provider store={store}> 
  <Main />
</Provider>
```
2. Map state to props in components
```js
const mapStateToProps = state => {
  return {
    leaders: state.leaders
  }
}
```
3. connect components to redux store
```js
export default connect(mapStateToProps)(About);
```
4. connect dispatchers to props in `MainComponent.js`
```js
import { fetchDishes } from '../redux/ActionCreators';

const mapDispatchToProps = dispatch => ({
  fetchDishes: ()  => dispatch(fetchDishes())
})
```
## React Debugging
1. Install packages
```shell
yarn add react-devtools
```
2. Start React devtools
```shell
react-devtools
```
