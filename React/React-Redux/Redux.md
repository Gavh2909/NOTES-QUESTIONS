# React Redux


## Step 1: Install Redux
- First, you need to install the Redux library and its companion library for React (if you're using React). Open your terminal and run:
```
npm install redux react-redux
```
## Step 2: Set Up the Store
- Create a Redux store by defining your state and reducers. The store is the central hub that holds the entire state of your application.
```
// src/store.js

import { createStore } from 'redux';
import rootReducer from './reducers'; // We'll create this file shortly

const store = createStore(rootReducer);

export default store;
```
