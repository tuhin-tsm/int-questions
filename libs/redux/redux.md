# Redux

Redux is a pattern and library for managing and updating application state, using events called "actions".

### Why Redux

- Centralized store
- Predictable: when, where, why, and how the state in your application is being updated

### Redux is more useful when:

You have large amounts of application state that are needed in many places in the app
The app state is updated frequently over time
The logic to update that state may be complex
The app has a medium or large-sized codebase, and might be worked on by many people

### Immutability

"Mutable" means "changeable". If something is "immutable", it can never be changed.
In order to update values immutably, your code must make copies of existing objects/arrays, and then modify the copies.

We can do this by:

- Array/Object spread operator (`const obj2 = {...obj1, a; 1}`)
- Array.concat()
- Array.slice()

## Terminology

### Actions

An action is a plain JavaScript object that has a type field. You can think it as event.
We usually write that type string like `"domain/eventName"` for ex. `"todos/todoAdded"`.

```javascript
const addTodoAction = {
  type: "todos/todoAdded",
  payload: "Buy milk",
};
```

### Action Creators

An action creator is a function that creates and returns an action object.

```javascript
const addTodo = (text) => {
  return {
    type: "todos/todoAdded",
    payload: text,
  };
};
```

### Reducers

A reducer is a function that receives the current state and an action object, decides how to update the state if necessary, and returns the new state: (state, action) => newState.

"Reducer" functions get their name because they're similar to the kind of callback function you pass to the `Array.reduce()` method(reducing the array down to one value").

Reducers must always follow some specific rules:

- They should only calculate the new state value based on the `state` and `action` arguments
- They are not allowed to modify the existing state. Instead, they must make immutable updates.
- They must not do any asynchronous logic, calculate random values, or cause other "side effects"

```javascript
const initialState = { value: 0 };

function counterReducer(state = initialState, action) {
  // Check to see if the reducer cares about this action
  if (action.type === "counter/increment") {
    return {
      ...state,
      value: state.value + 1,
    };
  }
  // otherwise return the existing state unchanged
  return state;
}
```

### Store

The current Redux application state lives in an object called the store.

```javascript
import { configureStore } from "@reduxjs/toolkit";

const store = configureStore({ reducer: counterReducer });

console.log(store.getState());
// {value: 0}
```

### Dispatch

The Redux store has a method called dispatch. **The only way to update the state is to call store.dispatch() and pass in an action object.**

```javascript
store.dispatch({ type: "counter/increment" });
```

### Selectors

Selectors are functions that know how to extract specific pieces of information from a store state value.

```javascript
const selectCounterValue = (state) => state.value;

const currentValue = selectCounterValue(store.getState());
console.log(currentValue);
// 2
```

### Async logic and data fetching

By itself, a Redux store doesn't know anything about async logic. It only knows how to synchronously dispatch actions. But, what if you want to have async logic interact with the store by dispatching or checking the current store state? That's where Redux middleware come in. They extend the store, and allow you to:

#### Thunk Functions

```javascript
const store = configureStore({ reducer: counterReducer });

const exampleThunkFunction = (dispatch, getState) => {
  const stateBefore = getState();
  console.log(`Counter before: ${stateBefore.counter}`);
  dispatch(increment());
  const stateAfter = getState();
  console.log(`Counter after: ${stateAfter.counter}`);
};

store.dispatch(exampleThunkFunction);
```

#### Fetching Data with createAsyncThunk

`createAsyncThunk` accepts two arguments:

- A string that will be used as the prefix for the generated action types
- A "payload creator" callback function that should return a Promise containing some data, or a rejected Promise with an error

```javascript
export const fetchPosts = createAsyncThunk("posts/fetchPosts", async () => {
  const response = await client.get("/fakeApi/posts");
  return response.data;
});

const initialState = {
  posts: [],
  status: "idle",
  error: null,
};

const postsSlice = createSlice({
  name: "posts",
  initialState,
  reducers: {
    // omit existing reducers here
  },
  extraReducers(builder) {
    builder
      .addCase(fetchPosts.pending, (state, action) => {
        state.status = "loading";
      })
      .addCase(fetchPosts.fulfilled, (state, action) => {
        state.status = "succeeded";
        // Add any fetched posts to the array
        state.posts = state.posts.concat(action.payload);
      })
      .addCase(fetchPosts.rejected, (state, action) => {
        state.status = "failed";
        state.error = action.error.message;
      });
  },
});
```

## Performance and Normalizing Data

### Memoizing Selector Functions

`Reselect` is a library for creating memoized selector functions, and was specifically designed to be used with Redux. It has a createSelector function that generates memoized selectors that will only recalculate results when the inputs change. Redux Toolkit exports the createSelector function, so we already have it available.

```javascript
import {
  createSlice,
  createAsyncThunk,
  createSelector,
} from "@reduxjs/toolkit";

// omit slice logic

export const selectAllPosts = (state) => state.posts.posts;

export const selectPostById = (state, postId) =>
  state.posts.posts.find((post) => post.id === postId);

export const selectPostsByUser = createSelector(
  [selectAllPosts, (state, userId) => userId],
  (posts, userId) => posts.filter((post) => post.user === userId)
);
```

### Normalizing Data

#### Normalized State Structure

"Normalized state" means that:

-We only have one copy of each particular piece of data in our state, so there's no duplication

- Data that has been normalized is kept in a lookup table, where the item IDs are the keys, and the items themselves are the values.
- There may also be an array of all of the IDs for a particular item type
