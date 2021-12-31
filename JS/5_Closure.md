![closure header image](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQKpYRzPMFHuyl_iFzVXjMBtW0BOBW-ORanT-h0IZoxKZrRVdBx)

# Closure
>A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the [lexical environment](#lexical-scoping)). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created `every time a function is created`, at function creation time.





## Lexical scoping
>A lexical scope in Javascript means that a `variable defined outside a function can be accessible inside another function` defined after the variable declaration. But the opposite is not true, the variables defined inside a function will not be accessible outside that function.


#### Sample Program 1:
```js

function lexical() {
  var name = 'Mozilla'; // name is a local variable created by lexical
  function displayName() { // displayName() is the inner function, a closure
    console.log(name); // use variable declared in the parent function
  }
  displayName();
}
lexical();

```
[For Answer Click Here](#program-1)

#### Explanation :
`lexical()` creates a local variable called `name` and a function called `displayName()`. The **displayName()** function is an inner function that is defined inside lexical() and is only available within the body of the lexical() function. Note that the displayName() function has no local variables of its own. However, since inner functions have access to the variables of outer functions, displayName() can access the variable name declared in the parent function, lexical().

![Lexical image : Reference from google](https://dmitripavlutin.com/static/955adfa7435c76ac16bfaf9d7d992ac1/04b03/javascript-closure-2.png)

---

# For every **closure** we have ```Three scopes```:

>Local Scope (Own scope)

>Outer Functions Scope

>Global Scope


![Closure : Reference from google](https://miro.medium.com/max/740/1*NamyWBedolrH4-N3iwUMfw.png)



#### Sample Program 2:
```js
// global scope
var e = 10;
function sum(a){
  return function(b){
    return function(c){
      // outer functions scope
      return function(d){
        // local scope
        return a + b + c + d + e;
      }
    }
  }
}

```
[For Answer Click Here](#program-2)



#### Sample Program 3:
```js
function foo(outer_arg) { 
  
    function inner(inner_arg) { 
        return outer_arg + inner_arg; 
    } 
    return inner; 
} 
var get_func_inner = foo(5); 
  
console.log(get_func_inner(4)); 
console.log(get_func_inner(3));

```

[For Answer Click Here](#program-3)



#### Program 1

```
   Mozilla
```

#### Program 2

```js
   20
```

#### Program 3

```js
   9
   8 

```






```js
/* 
 Reference : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures  
*/
```
