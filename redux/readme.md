![Redux](https://actyv-bootcamp.s3.ap-south-1.amazonaws.com/banners/redux.jpg)
# Redux

Redux is a design pattern to maintain the state of app.
Ok, then what is state of the app ? States of the app are those states which are getting used by most of the components of the app  and have to be get passed from one parent component to other inner levels of the components and get applies to those components

For example  : language, theme color, etc.

so the following examples are required by almost each component for there color when theme changes and laguage when language changes . So the color and language of whole app will be get changed. 
we can also maintain the states for particular sections of the app in redux. not only for the whole app status


## Redux is only for react ? 

NO, redux is not only for react. Redux is a design pattern which can be used by any frameworks.
You need to just install the library of redux for the particular framework.
 

## Is redux compulsory

No redux is not . you can also use Context in react for passing the global  states or you can use the manual passing of states to the inner level of app tree
But if you will use redux . it will be more easy to code and this design pattern will let you to code with less complexity

## Basic rules

1: App state is stored in a single **Store**
2: You can not change state directly 

## Structure of redux

As we checked that redux contains store but we can not change them directly. so to change and use the store , redux uses the functionalities called ACTION and REDUCER.
When our app loads then UI is loaded on screen with some existing values of state from store.
Now . let suppose we have to change the color of the app by changing the theme, then we have to click on change theme on UI. This is called ACTION. So ,to change the color state from store we have to tell Reducer that what action we are performing. Reducer will take the action and change the state and the updated state is catched by UI and UI color will change .
UI is always suscribed to Store so any changes in state will reflect in UI

 

![Structure of redux](https://miro.medium.com/max/1838/1*EdiFUfbTNmk_IxFDNqokqg.png)

Chronology: to create a STORE we need to create REDUCER and to create REDUCER, we need to create ACTION

## ACTION 
Actions are plain JavaScript objects. They usually have a payload and always have a type.

    const action = {
    type: "changeColor",  //type of action
    payload: {color: "white"} // what to do - here changing the color
    }

In given code we define the action as object which tell the redux that what type of action is this and what action has to be done or which state has to be changed

## Reducers
Reducers take current state and action as a parameter to return new state

    const reducer(state = "black" , action) => {
      switch(action.type){
      case "changeColor" : return "white" ;
      default : return state
      }
    }

## STORE
To create a store we have to just use a function createStore from redux library.

    import {createStore} from 'redux'     // importing from redux library
    import reducer from './reducer'       //importing reducer
    const store = createStore(reducer)    //creating store

## Dispatch the action
Now , to change the states we have to dispatch our action by using storeName.dispatch

    const action = {
    type: "changeColor",  
    payload: {color: "green"} 
    } 
    store.dispatch(action) // dispatching action
    
## Getting the states to UI (Subscribe)

Now if we have to get the current state then we can use **store.getState()**

    store.subscribe( ()=> {
     store.getState()
    })







