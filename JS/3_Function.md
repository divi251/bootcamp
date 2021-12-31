![function ](https://d36dc0i8phs68b.cloudfront.net/wp-content/uploads/2019/09/functions-2.png)

# **Function**


A `function` is a block of organized, reusable code that is used to perform a single, related action.



![function](https://www.frontamentals.com/static/function-breakdown-e46e54ec2e0de641547f63411acb1d84-bf43a.png)



**There are 3 types of functions in JavaScript:**

* **`Named function:-`**

The anonymous functions  have names.

```js
function sum(a, b) {
  console.log(a+b)
}
```
- **`Anonymous function:-`**

The anonymous functions don't have names.

```js
(function (a, b) {
  console.log(a+b)
})
```

- **`Immediately invoked function expression:-`**

It runs as soon as the browser finds it.

```js
(function (a, b) {
  console.log(a+b)
})(3, 5 )
```

----------------------------

## Arrow Function:-

 Arrow functions make our code more concise, and simplify function scoping and the this keyword.
 


Arrow functions do not create a new context. When you use the `this` keyword to access the context in an arrow function, it will always refer to the context in the outer scope. This is very useful when you want to maintain the context in places where you call functions that take a callback. The simplest example is when you call setTimeout with a callback

```js
function hello() {
  setTimeout(() => {
    console.log(this.name);
  }, 200);
}
hello.call({name: 'tom'});
```


## Higher Order Functions :-


Higher order functions are functions that operate on other functions, either by taking them as arguments or by returning them. In simple words, A Higher-Order function is a function that receives a function as an argument or returns the function as output.


```js

const arr1 = [1, 2, 3];
const arr2 = arr1.map(function(item) {
  return item * 2;
});
console.log(arr2);
```
```js
const numbers = [1, 2, 3];

const callback = number => {
  console.log('number', number);
};


numbers.forEach(callback);


function lessThan(y) {
  return function(x) {
    return x < y;
  }
}

const lessThan30 = lessThan(30);
lessThan30(20)
```

## Factory Function

A factory function is any function which is not a class or constructor that returns a  object. In JavaScript, any function can return an object. When it does so without the new keyword, it's a factory function.

```js

const createUser = ({userName = 'Anonymous',avatar = 'anon.png'} = {}) => ({
  userName,
  avatar
});

console.log(createUser())
     { userName: 'Anonymous', avatar: 'anon.png' }


console.log(createUser({userName: 'echo'}))
   { userName: "echo", avatar: 'anon.png' }
```
 



## Function Expression:- 

Function expressions load only when the `interpreter` reaches that line of code.

```js

console.log(foo()); 
// foo wasn't loaded yet
const foo = function() { return 5; }

```
## Function Declaration:-

Function declarations load `before` any code is executed

```js

console.log(foo()); 
// Declarations are loaded before any code can run.
function foo() { return 5; }

```
