# Understanding Questions:
1. What are the steps of execution from the pressing of the 1 button to the rendering of our updated value? List what part of the code excutes for each step.
* The user presses the 1 button.
* the 1 button's onClick function fires, which calls handleClick
* handleClick calls dispatch, which takes in one argument, the action object, consisting of a type property, which is required, and an optional payload property. In this case we are reaching that argument via a function imported from the actions file which evaluates to the action object that dispatch() requires. This object's literal representation looks like { type: "ADD_ONE"}. Because we want to pass the object, not the addOne function itself, we need to call the function using addOne(), not just addOne sans parens. 
* dispatch makes a call to the reducer while passing in the action object, whose type property then determines the case selection in the switch block. In this case the function associated with the ADD_ONE action type does not require any parameters, so there is no need for a payload property to be provided. 
* the switch block also somehow has access to the state object although it is unclear to me now whether that access comes from it's association with useReducer which was set up in App.js, or if dispatch() is somehow providing it implicitly, probably the former. 
* the logic in the ADD_ONE block replaces the former state object with a new version, spreading all of the values from the former state into a new object and overwriting the 'total' property (or slice) with a value that is greater by one than the earlier version. 
* The state is updated, forcing a re-render of the component.
* TotalDisplay shows the total plus 1.
