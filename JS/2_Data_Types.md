<!-- ![Data types header](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQS9wM5KfmAz9UzqsifDbYTdETcP6aH0hSh0qYOk9k4xchkPsAC) -->
![Data types](https://geekboots.sfo2.cdn.digitaloceanspaces.com/post/javascript-data-type-1567745251906.jpg)
<!-- ![Data types](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRda9C1TreGl_mddDbxDB16OXDXaBSuIEwYnUH8cdUO0sfcprYx) -->
# DATA TYPE 




***A data type is a kind of data being store in a variable.***




****The latest ECMAScript standard defines six data types:****




**1.** Boolean:-  It represents only one of two values true or false like On or Off of switch.



```
var a = true;
var flag = false;

```


**2.** String:- String are text must be inside double and single quotes.

```
var name = "Sita";
```
**3.** Null:- It is a value which is explicitly nothing.

```
var a = null;

```
**4.** Number:- It is a type of number can be written with or without a decimal point.Number can be +infinity, -infinity and NaN(not a number).

```
var number = 12;

```
**5.** Undefined:- A variable that has no value is undefined like declaration of a variable.

```
var foo;
```
**6.** Symbol:- It is in ES6 value that is unquine.

```
const mySymbol = Symbol('mySymbol');
console.log(mySymbol);
```





***According to the mutability(non-primitive) and immutability(primitive) :-***

`
Primitive data types are immutable meaning not able to be changed.`

`
Non-primitive data types are mutable meaning able to be changed.`



- String,Number,Boolean,Null,Symbol,Undefined are primitive data type.


- Objects are non-primitive data type.







**Questions :-**

**1.** Is js loosely typed language?


**2** .
```
 typeof 12 == typeof 12;
 typeof 13 == typeof "String";
 typeof "Number" == typeof "String";
 false == true; 
```

**3.**  
```
var name;
console.log(name);
```

**Answer :-**  

**1.**

Yes, javascript is loosely typed because we don't have to declare a variable type.JS automatically determine the type and that cane be change.Like

```
var type = "String";
var type = 12;
```

**2.**
```
true
false
true
false
```

**3.**
```
undefined
```
SAVE TO CACHER
