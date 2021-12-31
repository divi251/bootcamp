![rest andspread operators](https://www.bram.us/wordpress/wp-content/uploads/2018/01/esnext-destructure-and-rest-props-ftw.png)
# **Rest Operator[...rest]**



It is a collection of all remaining elements into an object.


```js
var myName = ["Marina" , "Magdy" , "Shafiq"] ;
const [firstName , ...familyName] = myName ;
console.log(firstName); // Marina ;
console.log(familyName); // [ "Magdy" , "Shafiq"]
```

If you are going to call a function and send a number of arguments , you will receive them into rest parameter in the function implementation.



```js
function name(firstName,...restName){
    return restName;
}

console.log(name("Marina" , "Magdy" , "Shafiq"))
```

If we want to skip any element in an array.We can skip.

```js
let numbers = [1,2,3,4,5,67,89];
let [one,two, , ,five,sixtySeven,eightyNine] = numbers;
console.log(one,two,five);  // 1 2 5
```


# **Spread Operator[...spread]**

Spread Operator is unpacking collected elements such as arrays into single elements .


```js
var myName = ["Marina" , "Magdy" , "Shafiq"];
// if you want to append myName array in newArr in a spread form.So,you can append through spread operator [...myName].
var newArr = [...myName ,"FrontEnd" , 24];
console.log(newArr) ; // ["Marina" , "Magdy" , "Shafiq" , "FrontEnd" , 24 ] ;
```


**pass elements of an array as a arguments to a function**

```js
function add(a,b,c){
    return a+b+c;
}
let numbers = [12,13,14];
console.log(add(...numbers))
```