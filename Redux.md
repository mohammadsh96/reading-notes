# Redux 
[back to main](./README.md)

  very important recourse : [here](https://egghead.io/lessons/react-redux-the-reducer-function)

1.What is the first `principle` of` Redux`? 
 - represent he whole state of the application as a single javascript object
 -  every thing changed in the application is contained in a single object 
 -   
what is a store and what do we use our reducers for within that store?

`A store` is an immutable object tree in Redux. A store is a state container which holds the application’s state. Redux can have only a single store in your application. Whenever a store is created in Redux, you need to specify the reducer.

Let us see how we can create a store using the createStore method from Redux. One need to import the createStore package from the Redux library that supports the store creation process as shown below −
```js
import { createStore } from 'redux';
import reducer from './reducers/reducer'
const store = createStore(reducer);
```
A createStore function can have three arguments. The following is the syntax −

createStore(reducer, [preloadedState], [enhancer])
A reducer is a function that returns the next state of app. A preloadedState is an optional argument and is the initial state of your app. An enhancer is also an optional argument. It will help you enhance store with third-party capabilities.

A store has three important methods as given below −

`getState`
It helps you retrieve the current state of your Redux store.

The syntax for getState is as follows −
```js
store.getState()
```
`dispatch`
It allows you to dispatch an action to change a state in your application.

The syntax for dispatch is as follows −
```js
store.dispatch({type:'ITEMS_REQUEST'})
```
`subscribe`
It helps you register a callback that Redux store will call when an action has been dispatched. As soon as the Redux state has been updated, the view will re-render automatically.

The syntax for dispatch is as follows −
```js
store.subscribe(()=>{ console.log(store.getState());})
```
Note that subscribe function returns a function for unsubscribing the listener. To unsubscribe the listener, we can use the below code −
```js
const unsubscribe = store.subscribe(()=>{console.log(store.getState());});
unsubscribe();
```

>>
Name three Redux store methods given to us by createStore and describe their use.
Explain to a non-technical recruiter what combineReducers() does and why it is useful.

### `Reducers` : 
 are a pure function in Redux. Pure functions are predictable. Reducers are the only way to change states in Redux. It is the only place where you can write logic and calculations. Reducer function will accept the previous state of app and action being dispatched, calculate the next state and returns the new object.

The following few things should never be performed inside the reducer −

Mutation of functions arguments
API calls & routing logic
Calling non-pure function e.g. Math.random()
The following is the syntax of a reducer −
```js
(state,action) => newState
```
Let us continue the example of showing the list of product items on a web page, discussed in the action creators module. Let us see below how to write its reducer.
```js
const initialState = {
   isLoading: false,
   items: []
};
const reducer = (state = initialState, action) => {
   switch (action.type) {
      case 'ITEMS_REQUEST':
         return Object.assign({}, state, {
            isLoading: action.payload.isLoading
         })
      case ‘ITEMS_REQUEST_SUCCESS':
         return Object.assign({}, state, {
            items: state.items.concat(action.items),
            isLoading: action.isLoading
         })
      default:
         return state;
   }
}
export default reducer;
```
Firstly, if you do not set state to ‘initialState’, Redux calls reducer with the undefined state. In this code example, concat() function of JavaScript is used in ‘ITEMS_REQUEST_SUCCESS', which does not change the existing array; instead returns a new array.

In this way, you can avoid mutation of the state. Never write directly to the state. In 'ITEMS_REQUEST', we have to set the state value from the action received.

It is already discussed that we can write our logic in reducer and can split it on the logical data basis. Let us see how we can split reducers and combine them together as root reducer when dealing with a large application.

Suppose, we want to design a web page where a user can access product order status and see wishlist information. We can separate the logic in different reducers files, and make them work independently. Let us assume that GET_ORDER_STATUS action is dispatched to get the status of order corresponding to some order id and user id.

/reducer/orderStatusReducer.js
```js
import { GET_ORDER_STATUS } from ‘../constants/appConstant’;
export default function (state = {} , action) {
   switch(action.type) {
      case GET_ORDER_STATUS:
         return { ...state, orderStatusData: action.payload.orderStatus };
      default:
         return state;
   }
}
```
Similarly, assume GET_WISHLIST_ITEMS action is dispatched to get the user’s wishlist information respective of a user.

/reducer/getWishlistDataReducer.js
```js
import { GET_WISHLIST_ITEMS } from ‘../constants/appConstant’;
export default function (state = {}, action) {
   switch(action.type) {
      case GET_WISHLIST_ITEMS:
         return { ...state, wishlistData: action.payload.wishlistData };
      default:
         return state;
   }
}
```
Now, we can combine both reducers by using Redux combineReducers utility. The combineReducers generate a function which returns an object whose values are different reducer functions. You can import all the reducers in index reducer file and combine them together as an object with their respective names.

/reducer/index.js
```js
import { combineReducers } from ‘redux’;
import OrderStatusReducer from ‘./orderStatusReducer’;
import GetWishlistDataReducer from ‘./getWishlistDataReducer’;

const rootReducer = combineReducers ({
   orderStatusReducer: OrderStatusReducer,
   getWishlistDataReducer: GetWishlistDataReducer
});
export default rootReducer;
```

Now, you can pass this rootReducer to the createStore method as follows −
```js
const store = createStore(rootReducer);
```