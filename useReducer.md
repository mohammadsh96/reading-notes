# useReducer
[back to main](./README.md)

## - what is useReducer ? 

- useReducer is usually preferable to useState when you have complex state logic that involves multiple sub-values or when the next state depends on the previous one. useReducer also lets you optimize performance for components that trigger deep updates because you can pass dispatch down instead of callbacks.

- An alternative to useState. Accepts a reducer of type (state, action) => newState, and returns the current state paired with a dispatch method.


 counter example from the useState section, rewritten to use a reducer: 
 ```js
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}

 ```
 **Note**

- React guarantees that dispatch function identity is stable and won’t change on re-renders. This is why it’s safe to omit from the useEffect or useCallback dependency list.


## What are two ways to set the initial state?
 1-The simplest way is to pass the initial state as a second argument:
 ex : 
 ```js
  const [state, dispatch] = useReducer(
    reducer,
    {count: initialCount}
  );
 ```
 2-Lazy initialization  : you can pass an init function as the third argument. The initial state will be set to init(initialArg).
 ex : 

 ```js
function init(initialCount) {
  return {count: initialCount};
}

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    case 'reset':
      return init(action.payload);
    default:
      throw new Error();
  }
}

function Counter({initialCount}) {
  const [state, dispatch] = useReducer(reducer, initialCount, init);
  return (
    <>
      Count: {state.count}
      <button
        onClick={() => dispatch({type: 'reset', payload: initialCount})}>
        Reset
      </button>
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
 ```

## when to Use useReducer ?
 when you move past managing primitive data, i.e., a string, integer, or Boolean, and instead must manage a complex object, like with arrays and additional primitives, you’re likely better off with useReducer



 ## what does useReducer expect to receive as a parameter?

 Basically: useReducer: expect 2 parameters, (a) a function (known as the reducer function), and (b) the initial value for the state. The reducer function will be called to modify the state whenever you call fn with some value. And the value passed to fn will be passed through to the reducer function (as the second parameter)


 ## What does useReducer return?

 the useReducer hook returns two things: the state, and a function called dispatch. This is pretty similar to useState, which also returns the state and a function to modify the state. const [ state, dispatch] = useReducer(reducer, initialState);