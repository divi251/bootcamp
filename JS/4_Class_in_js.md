# **Class Definition**
>In the real world, you often have many objects of the same kind. `For example`, your bicycle is just one of many bicycles in the world. ... A software blueprint for objects is called a class . Definition: A **class** is a `blueprint` that defines the variables and the methods common to all objects of a certain kind.


# Classes Are Functions
A JavaScript class is a type of function. Classes are declared with the `class` keyword. We will use function expression syntax to initialize a function and class expression syntax to initialize a class.

```js
// Initializing a function with a function expression
const x = function() {}

```

```js
// Initializing a class with a class expression
const y = class {}


```
>The code declared with function and class both return a function [[Prototype]]. With prototypes, any function can become a constructor instance using the new keyword.

---
## class syntax

```js
// Initializing a class definition
class Hero {
    constructor(name, level) {
        this.name = name;
        this.level = level;
    }
}
```
---
## constructor function
```js
// Initializing a constructor function
function Hero(name, level) {
    this.name = name;
    this.level = level;
}

```
---
>The only difference in the syntax of the initialization is using the class keyword instead of function, and assigning the properties inside a `constructor()` method.


We know a constructor function is meant to be an object blueprint by the capitalization of the first letter of the initializer (which is optional) and through familiarity with the syntax. The class keyword communicates in a more straightforward fashion the objective of our function.


---
# Defining Method


>The common practice with constructor functions is to assign methods directly to the `prototype` instead of in the initialization, as seen in the greet() method below.


```js
/****** Constructor Function ******/

function Hero(name, level) {
    this.name = name;
    this.level = level;
}

// Adding a method to the constructor
Hero.prototype.greet = function() {
    return `${this.name} says hello.`;
}


```
>With classes this syntax is simplified, and the method can be added directly to the class. Using the method definition shorthand introduced in ES6, defining a method is an even more concise process.

```js
/********   Class   *******/
class Hero {
    constructor(name, level) {
        this.name = name;
        this.level = level;
    }

    // Adding a method to the constructor
    greet() {
        return `${this.name} says hello.`;
    }
}

```
---

# Extending the Class
An advantageous feature of constructor functions and classes is that they can be extended into new object blueprints based off of the parent. This `prevents repetition of code` for objects that are similar but need some additional or more specific features.

New constructor functions can be created from the parent using the call() method. In the example below, we will create a more specific character class called Mage, and assign the properties of Hero to it using `call()`, as well as adding an additional property.


```js
//parent 
function Hero(name, level) {
    this.name = name;
    this.level = level;
}
// Creating a new constructor from the parent
function Mage(name, level, spell) {
    // Chain constructor with call
    Hero.call(this, name, level);

    this.spell = spell;
}


const hero2 = new Mage('Lejon', 2, 'Magic Missile');

```

---

>With `ES6 classes`, the `super` keyword is used in place of `call` to access the _parent functions_. We will use `extends` to refer to the _parent class_.



```js
// Initializing a class definition --- parent
class Hero {
    constructor(name, level) {
        this.name = name;
        this.level = level;
    }
}

// Creating a new class from the parent
class Mage extends Hero {
    constructor(name, level, spell) {
        // Chain constructor with super
        super(name, level);

        // Add a new property
        this.spell = spell;
    }
}

```





Although the syntax is **quite different**, the underlying result is nearly the _same between both methods_. `Classes` give us a more concise way of creating object blueprints, and `constructor functions` describe more accurately what is happening under the hood.

In this this, we learned about the similarities and differences between JavaScript `constructor functions` and `ES6 classes`. Both classes and constructors imitate an object-oriented inheritance model to JavaScript, which is a prototype-based inheritance language.



