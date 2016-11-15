## Learning about with [React + Redux](https://egghead.io/courses/getting-started-with-redux) and [CRUD with REDUX](https://www.youtube.com/watch?v=h1ivekTEC2M&list=PLuNEz8XtB51KfnHc99GwscPy1UbLJyXHW&index=1)

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


##  Some notes the lessons are going through:
1.  The first principle of Redux is that everything that changes in your application, including the data and the UI state, is contained in a `single object`, we call the `state` or the `state tree`.
2.  The second principle of Redux is that the `state tree is read only`. You cannot modify or write to it. Instead, anytime you want to change the state, you need to dispach an action.
3.  An `action` is a plain JavaScript object describing the change. The example in the counting app they, the dispatching action is `type: "INCREMENT"` and `"DECREMENT"`.
4.  Understanding the difference between the `pure` and `impure` functions is an important distinction because some of the function that you're going to write in Redux have to be pure, and you need to be mindful of that.
5.  The `pure` functions are the functions whose returned value depends solely on the values of their arguments. Pure functions do not have any observable side effects, such as network or database calls. The pure functions just calculate the new value. You can be confident that if you call the pure function with the same set of arguments, you're going to get the same returned value. They are predictable. Also, pure functions do not modify the values passed to them. In the example they used they had a `squareAll` function that accepts an array, this function does not overwrite the `items` inside this array. Instead, it returns a new array by using `items.map`.
6.  All Redux application have to implement the `reducer`: which is a function that calculates the next state tree based on the previous state tree and the action being dispached. This function has to be pure.
