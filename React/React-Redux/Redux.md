# React Redux


## Step 1: Install Redux
- First, you need to install the Redux library and its companion library for React (if you're using React). Open your terminal and run:
```
npm install redux react-redux
```

## Step 2: Create Action Types
```
actionTypes.js

export const LOGIN_SUCCESS = 'LOGIN_SUCCESS';
export const LOGIN_FAILURE = 'LOGIN_FAILURE';
```
## Step #: Create Actions

```
userActions.js

import { LOGIN_SUCCESS, LOGIN_FAILURE } from './actionTypes';

export const loginSuccess = (userData) => ({
  type: LOGIN_SUCCESS,
  payload: userData,
});

export const loginFailure = (error) => ({
  type: LOGIN_FAILURE,
  payload: error,
});

```

## Step 3: Create Reducer
- Reducers are functions that specify how the state changes in response to actions.

  ```
  authReducer.js

  import { LOGIN_SUCCESS, LOGIN_FAILURE } from '../actions/actionTypes';

const initialState = {
  userData: null,
  error: null,
};

const authReducer = (state = initialState, action) => {
  switch (action.type) {
    case LOGIN_SUCCESS:
      return {
        ...state,
        userData: action.payload,
        error: null,
      };
    case LOGIN_FAILURE:
      return {
        ...state,
        userData: null,
        error: action.payload,
      };
    default:
      return state;
  }
};

export default authReducer;
```
Step 4: Combine the reducer using combineReducer

```
index.js

import { combineReducers } from "redux";
import authReducer from "./userReducer";

const rootReducer=combineReducers({
     auth:authReducer
})

export default rootReducer;
```

## Step 5: Set Up the Store
- Create a Redux store by defining your state and reducers. The store is the central hub that holds the entire state of your application.
```
store.js

import { createStore } from 'redux';

import rootReducer from '../redux/reducers/index';
const store = createStore(rootReducer);

export default store;
```

  
