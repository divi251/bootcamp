![variables image](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRdlwTjYxevrCXigDBYFzDItpA6fs3grODhz0Rp7XyqfXDBgdT8)
<!-- ![variables image](https://i1.wp.com/www.geekstrick.com/wp-content/uploads/2017/10/javascript-variables.png?w=756&ssl=1) -->
# **Variable**  
`Variable` which holds the data value and it can be changed anytime.
```javascript
var age = 10;
age = "String";
console.log(a); // String
```




_JavaScript_ uses reserved keyword `var`,`let` and `const`   to declare a variable.


## **Var :-**

It is used to declare a variable and, optionally, we can `initialize` the value of that variable.

- The var statement declares a local variable in a [Function Scope](#FunctionScope).

- [Hoisting](#Hoisting) works in var keyword.


## **Let :-**

The let statement declares a local variable in a [Block Scope](#BlockScope).


## **const :-**
const statement values can be assigned once and they cannot be reassigned. The scope of const statement works similar to let statements.

```js
const number = 42;
const number = 45;
// SyntaxError: Identifier 'number' has already been declared
```


> ## **Scope :-)**   

Scope determines the visibility or accessibility of a variable or other resource in the area of your code.



## **GlobalScope**

The area outside all the functions is consider the global scope and the variables defined inside the global scope can be accessed and altered in any other scopes.

<details>
<summary>Examples</summary>

```js
//global scope
var fruit = 'apple'
console.log(fruit);        //apple

function getFruit(){
    console.log(fruit);    //fruit is accessible here
}

getFruit();                //apple
```
</details>


> |||||||

## **LocalScope**


Variables declared inside the functions become Local to the function and are considered in the corresponding local scope.


<details>
<summary>Examples</summary>

```js
//global scope
function foo1(){
    //local scope 1
    function foo2(){
        //local scope 2
    }
}

//global scope
function foo3(){
    //local scope 3
}

//global scope
```
</details>


Local scope can be divided into function scope and block scope. The concept of block scope is introduced in ECMA script 6 (ES6) together with the new ways to declare variables:- const and let.


### `FunctionScope`
The variable is visible  only within the function. You can't access it outside the function

<details>
<summary>Code Snippet</summary>

```js
function foo(){
    var fruit ='apple';
    console.log('inside function: ',fruit);
}

foo(); //inside function: apple
console.log(fruit);//error: fruit is not defined 

```

</details>


### `BlockScope`


A block scope is the area within `if, switch conditions or for and while loops`.  whenever you see {curly brackets}, it is a block. In ES6, const and let keywords allow developers to declare variables in the block scope, which means those variables exist only within the corresponding block.

<details>
<summary>Code Snippet</summary>

```js
function foo(){
    if(true){
        var fruit1 = 'apple';        //exist in function scope
        const fruit2 = 'banana';     //exist in block scope
        let fruit3 = 'strawberry';   //exist in block scope
    }
    console.log(fruit1);//apple
    console.log(fruit2);//error: fruit2 is not defined
    console.log(fruit3);//error: fruit3 is not defined
}

foo();



```
</details>



> ||||||

## **LexicalScope**
 Lexical scope means the children scope have the access to the variables defined in the parent scope. The children functions are lexically bound to the execution context of their parents.



<details>
<summary>Code Snippet</summary>

```js
 function foo1(){
    var fruit1 = 'apple';        
    const fruit2 = 'banana';     
    let fruit3 = 'strawberry';
    function foo2(){
        console.log(fruit1);
        console.log(fruit2);
        console.log(fruit3);
    }
    foo2();
}

foo1();

//result:
//apple
//banana
//strawberry
```
</details>

> ||||||


## **Hoisting**

>In General, **`Hoisting`** according to Google Dictionary is to **raise** (something) by means of ropes and pulleys. E.g. "a white flag was hoisted” etc. But what do you think hoist would be in the JavaScript’s Context ?? Does Javascript pull something up ? Read below to find out...



```js
    x=10;//Initialize variable x with 10,

    console.log(x) //Print the variable x,

    var x;//And then Declare variable x.


```
**OUTPUT:**

```js

    //What do you think would be the result of the above piece of code in Java/C?
    ERROR!

```
But in JavaScript you would swiftly be answered as 10. Yes, this is because of a concept called Hoisting in JavaScript. In Plain words **Hoisting in JavaScript means you can use a variable without declaring it before after initialization. This is because of the JavaScript’s default behavior to move all the declarations to the top of the respective block and then start the execution of code**.


![image1](https://firebasestorage.googleapis.com/v0/b/bootcamp-5e181.appspot.com/o/image1.png?alt=media&token=e10c579d-eaaa-4627-b55f-2f592ee4bae7)




But wait, don’t to conclusions so soon… What do you think would be the result of this line of code below.




![image3](https://firebasestorage.googleapis.com/v0/b/bootcamp-5e181.appspot.com/o/image6.png?alt=media&token=3d30604e-fae4-48df-bacd-eec64b68c537)


If you are thinking that the result would be 10, then sorry my dear friend the result is `UNDEFINED`. Puzzled?! Yes, because only the `DECLARATIONS` are moved to the top but not the `INITIALIZATIONS`. And so variable x was declared but the value was unknown until the last line of code and hence the result was undefined.




![image2](https://firebasestorage.googleapis.com/v0/b/bootcamp-5e181.appspot.com/o/image5.png?alt=media&token=4213d1a0-aa45-4608-91e6-90558a6f9693)

<br>

>But does this rule apply to all types of declarations? I mean does this rule apply to declarations of variable using ‘let/const’ keyword. No!! This rule of Hoisting is applicable only to variable declared using the `VAR` keyword.
Variables defined with let/const are not hoisted to the top. Using a let variable before it is declared will produce a result “ReferenceError”. This variable is in a "TEMPORAL DEAD ZONE" from the start of the block until it is declared and so we have our answer.
Just as an Extra info, the var declarations are declared directly into the window object when declared in global scope with value as undefined until initialized but this doesn’t happen in the case of variable declared using let/const. This can be verified using the below animation.

<br>

![Hoisting gif by @mohan_drive](https://firebasestorage.googleapis.com/v0/b/bootcamp-5e181.appspot.com/o/image2.gif?alt=media&token=96ed5a29-49c7-4b7a-a7cf-dce5221ede27)


Just to verify what you have learnt, Guess the result of this line of code below,

![image4](https://firebasestorage.googleapis.com/v0/b/bootcamp-5e181.appspot.com/o/image3.png?alt=media&token=2f217238-c9b8-4f9f-b53e-065154159225)

For the guys who think the answer is 10, you are wrong ! Take a look at the first paragraph. The declarations are moved to the top but in their own block so x is undefined in global scope as it is declared in the function and hence gives us an Error.


![image6](https://firebasestorage.googleapis.com/v0/b/bootcamp-5e181.appspot.com/o/image4.png?alt=media&token=a395cd2c-a7c4-4ada-be14-88d4aa4a740e)



<br>
<br>




**_Questions:-_**

1. Different between let,var and const ?

<details>
<summary>Answer</summary>

Keyword | Scope | Hoisting | Can Be Reassigned | Can Be Redeclared
------- | ------- | ------- | ------- | -------
var | Function scope | Yes | Yes | Yes
let | Block scope | No | Yes | No
const | Block scope | No | No | No

</details>

2. How to make a variable global in this code ?


```js
{
let a = 10;
let b = 13;
let c = 20;
}
```

<details>
<summary>Answer</summary>
A can become a global variable without using  a keyword because js will by default take this var.

```js
{
 a = 10;
let b = 13;
let c = 20;
}

// But this is not a good approach because anyone can manipulate with our object easily.
```
</details>


3. If var is functional scope.Where is the function in this code?
<details>
<summary>Answer</summary>


```js
{
 var a = 10;
 var b = 13;
 var c = 20;
}

```
In js main function runs first. In other programming languages like Java, c++. We have to write the main function but it’s already by default store  in js when code will compile first main function will run.

</details>

4. How hoisting works with var ?

<details>
<summary>Answer</summary>

Hoisting works with var because at compiling time the variable if declared with the var keyword will get stored in window object.

```js
let b = 10;
var a = 20;

window.b; //undefined  because b is not store in window object.

window.a // 20 because a stored in window object.
```


</details>

5. Why let and const don’t work with hoisting ?

<details>
<summary>Answer</summary>
let and const keywords value will store in memory while executing time.
</details>
