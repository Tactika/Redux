# Redux

## About

- _*What is Redux?*_
  - JS Library & Pattern
>
- _*Why use Redux?*_
  - Manage Global State
  - Understanding of when, where, and why of state changes
  - More predictable outcomes
  - Better testing
>
- _*When to use Redux?*_
  - Medium to Large codebases
  - State frequently changes
  - Update logic is complex
  - Large Amount of Application State
> 
- _*When 'not' to use Redux?*_
  - Simple Applications
  - Minimal state changes
  - Lack of functional programming knowledge
  - Logic is simple to update state
>
- _*Redux Libraries & Tools*_
  - React-Redux
  - Redux Toolkit
  - Redux DevTools Extensions
    - [GitHub](https://github.com/reduxjs/redux-devtools/tree/main/extension)
>
- _**_
## Terms
- Actions
  - JavaScript object that has a type field
  - Event that describes something that happened in the app
  - i.e. `"todos/todoAdded"` format is `"domain/eventName"`
  - Action object contains what happened, goes in payload `payload`
  - example: 
    >```javascript
    >const addTodoAction = {
    >type: 'todos/todoAdded',
    >payload: 'Buy milk'
    >}

- Action Creators
  - Function that creates and returns an action object
  - example:
    > ```javascript
    > const addTodo = text =>  {
    >     return {
    >         type: 'todos/todoAdded',
    >         payload: 'text' 
    >     } 
    >}
- Reducer
  - Function that receives current `state` and an `action` object, then decides how to update state, then returns new state `(state, action) => newState`
  - Like an event listener which handles events based on the received action (event) type.
  - example:
    ```javascript
    const initialState = { value: 0 }
        function counterReducer(state = initialState, action) {
        // Check to see if the reducer cares about this action
        if (action.type === 'counter/increment') {
            // If so, make a copy of `state`
            return {
            ...state,
            // and update the copy with the new value
            value: state.value + 1
            }
        }
        // otherwise return the existing state unchanged
        return state
        }
    ```
>
- Store
  - Current Redux App State is in the object called store
  - Created by passing in a reducer and has a method `getState`, which returns state value
>
- Dispatch
  - Store has a method called `dispatch`
  - Only way to update state is by calling `store.dispatch(<object goes here)`
  - Dispatch actions are a way of 'triggering an event'

    ```javascript
        const increment = () => {
            return {
                type: 'counter/increment'
            }
        }

        store.dispatch(increment())

        console.log(store.getState())
        // {value: 2}
    ```
>
- Selectors
  - Functions that know how to extract exact pieces of information from state value.
  - example:
  ```javascript
    const selectCounterValue = state => state.value

    const currentValue = selectCounterValue(store.getState())
    console.log(currentValue)
    // 2
  ```
## Resources
- [Immutability in React and Redux](https://github.com/reduxjs/redux-devtools/tree/main/extension)