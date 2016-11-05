## Learning about [React + Redux](https://egghead.io/courses/getting-started-with-redux)

### Why use React altogether with Redux at all? As an analogy for beginners, I like to use the SQL. Redux gives you a lot of convenience over plain React in terms of storing data on the front-end. It's like an SQL database of your client-side app (not literally, just an analogy). With Redux, you can to query SELECT, INSERT and UPDATE the data in your single state tree. - Kamil Prezeorski ([best place to learn React.js reply on quora](https://www.quora.com/Whats-the-best-place-to-learn-React-js))

## Some reasons why Redux with React:
1.  One (and only one) `state`: It is an object that keeps the global state of your application. Everything has to be in that object, both data and ui.
2.  A bunch of `actions`: These are simple objects that are created/dispatched when something happens (ui interaction, server response etc) with a mandatory property (their type) and a number of optional properties that define the data that accompanies each action.
3.  A bunch of `action creators`: These are very simple functions that create action objects. Usually, there are as many action creators as actions (unless you use redux-thunk, we’ll talk about it later).
4.  One (and only one) `reducer`: It is a function that retrieves the current state and an action and creates the resulting state. This is the central component of a redux application - every action along with the current state will be passed to the reducer and the state of the application will be the resulting, new state.
5.  One (and only one) `store`: It is an object that is created by redux and is used as a glue between the state, the reducer and the components.

##  The general idea/flow is:
1.  Something (let’s call it event) happens (i.e a user clicks a button, a timeout is fired, an ajax request responds).
2.  An action describing that event is created by its the corresponding action creator and dispatched (i.e passed to the reducer along with the current state) through the store.
3.  The dispach calls the reducer with the current state object and the action as parameters.
4.  The reducer checks the type of the action and, depending on the action type and any other properties this action has, creates a new state object.
5.  The store applies the new state to all components.
