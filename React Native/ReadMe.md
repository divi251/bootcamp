![enter image description here](https://actyv-bootcamp.s3.ap-south-1.amazonaws.com/banners/React+native.jpg)
# REACT Native
React native is same as React but instead of using HTML elements as JSX we use native components.
For example, in react we create a web app for running it into a browser, and the browser understands only HTML. In case of React Native we create apps for android or ios, Android will not understand HTML. Android has there own Native elements.


**HTML Elements** : div , P, header, footer, h1, h2, h3, h4, input, etc.
**Android Elements** : TextView, TouchableOpacity, Button, etc.

So React native has its own elements called react-native elements which get changed to android native elements or ios native elements

All logical concepts are same in react and in react native like STATES, PROPS, FRAGMENTS, PORTALS. Just a few concepts are different for example We use Navigators instead of Routers.
Some CSS properties will not work

But if you are not aware of concepts of React. You don't have to go anywhere.


# How Code Looks

    import React, { Component } from 'react'; 
    import { Text, View } from 'react-native';
    
    export default class HelloWorldApp extends Component {
      render() {
        return (
          <View style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
            <Text>Hello, world!</Text>
          </View>
        );
      }
    }

1: the first line is importing the react library to use the features of react to handle the components.

2: Second line is importing Text component to use it and show some text on the screen.

3: Third line is defining a class to make class component by using "Components" class of react which we have imported. This Hello word class will behave as child class for the Component class we have imported because we are using keyword Extends which is used to create a child class.

4: the Fourth line is using render function to render the js code and UI elements for Android and ios for example, if we will see in render function it is returning a View element which is wrapped inside Text element show some text.



# BASIC  KEYS   IN REACT JS

## REACT NATIVE ELEMENTS :
in this section, we will see some react native elements basics. Let just compare the elements in react native. for example, You will never see div tag in react native code. you will always see the View tag instead of div. if you have to write some text then you have to use"Text "element.
Let us have look on some Components

  
 **Text input:**
   This is a basic component that allows the user to enter text. 

    <TextInput />

 **Button:**
 It provides a basic button component that is rendered nicely on all platforms. The minimal example to display a button looks like this:

    <Button />
**Touchable Opacity:**
This works the same as button. It can be used to provide feedback by reducing the opacity of the button, allowing the background to be seen through while the user is pressing down.

    <TouchableOpacity />

**Scroll View:** 
The scroll view is used to scroll the page if the content is more then the required height. So we use scroll view to wrap the content so it can be scrolled and  not get hidden

    <ScrollView>
     <Text>some larger text........</Text>
    <ScrollView>

Some components we can not apply "onPress" events directly. So before applying any styles or event listener check the official documentation that what props we can pass to component. If component not taking the on press events and styles then it will not work

## React Native Styles:
applying styles to react native is same as react and in normal HTML CSS. We can apply inline styles like this:

    <Text style={{color: "blue"}}>just red</Text>
We can apply styles as embeded by creating a object of styles and then passing that object into component as style prop:

  

     const styles = StyleSheet.create({
       bigBlue: {
         color: 'blue',
         fontWeight: 'bold',
         fontSize: 30,
       },
       red: {
         color: 'red',
       },
      });
      
      <Text style={styles.red}>just red</Text> // calling styles as object


## COMPONENTS :
Let us take an example of an app. If you will see any app then you will see that it is made up of individual units like buttons, cards, menu etc. if you will see the menu then there will be a lot of options will be listed inside the menu in form of smaller cards. So what you will do?
are you going to create each of the options repeatedly? If you do it will take time and memory as well. Another approach is that we can create one card and we can call it on a menu with what amount of number we want. We can pass the different values to that same component which will behave differently with different inputs.
The component is a building block of the UI, which we can reuse it.

Type of components : 

>> **Functional components:** 
are those components which takes Props or values and return some JSX or Native Elements .
Basically, it is a function which takes props/values and gives JSX/Native Elements

    import React from  'react';
    import { Text, View } from 'react-native';
    function  App()  {
      const greeting =  'Hello Function Component!';
      return  <Text>{greeting}<Text>;
    }
    export  default App;=
> >  **Class components:**  
> > are those components which takes Props or values and return some JSX or Native Elements .  
> > Basicly it is a class which takes props/values and gives Native Elements
> >They are having there states

```
class Welcome extends React.Component {
  render() {
    return <Text>Hello, {this.props.name}</Text>;
  }
}
```

## PROPS :  
As we discussed above, we can pass the values in components so they can give different output.
For example:  In the menu's options, the component is the same but the name will be different like option1, option2, option3, etc. but shape size will be the same.
So, how it is changing the name only but shape and size is common. This is what is called Prop.
We have to pass the values to components so it can show the name or any other values. The values which we pass to a component, are called Props

    <option> <option/>                      //this is option component
    <option name = "option1"> <option/>     //this is component with props

In the following example, the options component will show its name as option1. Because we have passed props to component. You can also say that you are passing some values to a component.

## STATE  :
 The state is that variable of a component on which behaviour of a component is decided.
Suppose we have to change the colour of the component then there should be a variable which is directly connected to the behaviour of the components. If we will change the value that variable then the colour will be get changed.
How it is different from the normal variable?
State behaves like a live variable. when the state will be getting changed we don't have to again give the command to change the behaviour. It is directly subscribed to the component

Points to be noted : 
1: State is immutable. Use setState() method to change the state

## FRAGMENTS:
 In react you can not render more than one component or element in a render function. You have to wrap all the component in a single element. But it will show the wrapper element as well.
if we want to wrap up the element so it will not be counted on dom, we can use Fragments
 
 
     *****Wrong CODE******
     
     render(
        return(
           <Text>line one</Text> . // 1st element
           <Text>line one</Text> . // 2nd element
          )
        )
    
  upper code wrong  in one time we can use one component to render but two 
  "< Text >" component is loading which returns error

    *****Right Code******
    
         render(
            return(
            <View>
               <Text>line one</Text>. // 1st element
               <Text>line one</Text> . // 2nd element
            <View>
              )
            )
this is right code in which we wrapping the 'P' elements/tag/components  in a single "View" 

now the best  code is that which uses Fragments

    *****Best Code******
        
             render(
                return(
                <Fragments>
                   <Text>line one</Text> . // 1st element
                   <Text>line one</Text>. // 2nd element
                <Fragments>
                  )
                )
this will not show the fragment when it is mounted it will show only two wrapped components. No, any extra view will be there for formality.

## Lifecycle of a component
when you open any app then you load the components and when you switch to another page those components get removed. So these thing happens with the component.
1: Mount
2: Update
3: Unmount

Now let just chek what methods react js giving for the lifecycle of components and why!


    
-   **componentDidMount**  is executed after the first render only on the client-side. This is where AJAX requests and DOM or state updates should occur. This method is also used for integration with other JavaScript frameworks and any functions with delayed execution such as  **setTimeout**  or  **setInterval**. We are using it to update the state so we can trigger the other lifecycle methods.
    
    
-   **shouldComponentUpdate**  should return  **true**  or  **false**  value. This will determine if the component will be updated or not. This is set to  **true**  by default. If you are sure that the component doesn't need to render after  **state**  or  **props**  are updated, you can return  **false**  value.
    

    
-   **componentDidUpdate**  is called just after rendering.
    
-   **componentWillUnmount**  is called after the component is unmounted from the dom. We are unmounting our component in  **main.js**. 

## LIST HANDLING
As we use UL and Li elements in HTML, we use FlatList to React native.
The `FlatList` component requires two props: `data` and `render item`. `data` is the source of information for the list. `render item` takes one item from the source and returns a formatted component to render.


    <FlatList
          data={[
            {key: 'Devin'},
            {key: 'Dan'},
            {key: 'Dominic'},
            {key: 'Jackson'},
            {key: 'James'},
            {key: 'Joel'},
            {key: 'John'},
            {key: 'Jillian'},
            {key: 'Jimmy'},
            {key: 'Julie'},
          ]}
          renderItem={({item}) => <Text>{item.key}</Text>}
        />
      </View>
    
##  WHAT is "Ref"
If you have to select element on dom then there are 3 famous querry function to serach the  element. 
1: document.getElementById()
2: document.getElementsBytagName()
3:document.getElementsByClassName()

But in react you right the UI code in JSX and that JSX rendered as HTML element so you should not have to use these functions because react will not know the changes.
so we can use Ref to select the elements and change the value.

Refs are created using `React.createRef()` and attached to React elements via the `ref` attribute.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();     // here we are defining ref
  }
  render() {
    return <input ref={this.myRef} />;   // here we are putting ref to select elemnt
  }
}

```
Now if we want to access the value of input box then we can acces it by using  
```
 this.myRef.current;   // it will select the input box 
 this.myRef.current.value;  // it will show the value of input box 
```

   

## Error Boundaries
Error Boundaries are react component that captures error and shows a fallback UI. It is done  by using getDerivedStateFromError(error) or componentDidCatch(Error) by changing the state to show fallback UI

   ```
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Update state so the next render will show the fallback UI.
    return { hasError: true };
  }

  render() {
    if (this.state.hasError) {
      // You can render any custom fallback UI
      return <Text>Something went wrong.</Text>;
    }

    return this.props.children; 
  }
}
```

## Passing Props From parent to child : 
To pass props in the child component, We can directly pass it where a component is called.
 
      <View>
      <Greeting  color={green}  /> passing prop/data color as green
      </View>
 Now we have to recive it where we have defined the componet 


    import React,  { Component }  from  'react';
    import {Text, View } from 'react-native';
    class  App  extends  Component  {
      render(props)  {               // reciving props
      return  (
      <View>
      <Text>{props.greeting}</Text>     // using prop value to display
      </View>
      );
      }
    }
    export  default App;

## Passing Props From child to parent : 

To pass props from parent to child is too easy . but there is no any portal looks to pass some data from child to parent.because when we call the element or component then we can pass the data but we cannot send data from where it is defined.
But we can do it by passing callback function from parent to child and passing the data and running the callback function from the child component.
   

        import ChildComponent from ".../location"
        class SomeParentComponent extends React.Component {
          constructor(props) 
           { super(props); 
             this.state = {color: 'red'}; 
           }
          function recieveDataAndChangeColor(data) {
            this.setState(
              {
               color : data
              }
            )
          }
         render() { 
            return  <ChildComponent color = {this.recieveDataAndChangeColor.bind(this)} />; 
            } 
         }

 Now getting the function and calling it in the child component.
 when we call the recieveDataAndChangeColor("green") it will pass the value green from child component  and run the function and function will set the state's colour as green
 

      class ChildComponent extends React.Component {
           constructor(props) 
            { super(props);
            }
            componentDidMount(){
            this.props.recieveDataAndChangeColor("green")  // calling function here
            }
           render() { 
             return  <Text> This is child component <Text/>; 
             } 
      }

## Navigation : 
In a normal web app, the browser has a back button to go back and forward button to come forward. Similarly in React Native if we want to navigate from one page to another page without refreshing the page keeping app data alive then we use Navigator.
react Navigation provides a straightforward navigation solution, with the ability to present common stack navigation and tabbed navigation patterns on both Android and iOS.

Following are the steps to use react-navigation

1: First we have to install the React navigation library

    npm install  --save react-navigation
2: Install react-native-gesture-handler

    npm install --save react-native-gesture-handler
3: Now you have to set the screens as follows if you have a home page and profile screen

    import  {createAppContainer}  from  'react-navigation'; 
    import  {createStackNavigator}  from  'react-navigation-stack';
    
    const MainNavigator =  createStackNavigator(
     {
      Home:  {screen: HomeScreen}, 
      Profile:  {screen: ProfileScreen},  
     }
    );
    
    const App =  createAppContainer(MainNavigator);
    export  default App;
    

In the first line, we are importing createAppContainer from react-navigation to create app container which can hold the main navigator.
In the second line, we are importing createStackNavigator from  react-navigation-stack which will create a stack of the screens
now in the third line, by using create navigator we are defining the screens in the stack 
In the fourth line, we are using createAppContainer to create an index App element from which navigation will start.

