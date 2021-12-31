![clone](https://miro.medium.com/max/2400/1*ZXPmfUIwyW8RgeTChDfThg.png)

# **_Clonning in Javascript_**

## **_What is Clonning?_**

In plain words, Clone is a copy of a thing. And Clonning is just the process of making a copy.

![clonning image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ3R9oK71bTLk1aAafluUW3nbj7I9v8OKnpWuUnEggD45J8WKSl&s)

But In JS, it's a bit different, 
Clonning is either making a copy of the existing **block of memory** or creating another reference that points to the existing **block of memory**.

> **Note:** _Here "Block of memory" can be any defined Object in Javascript._

## **_Why do we use Clonning ?_**

To create a copy of Existing Object instead of creating the same object from the scratch.

**Added Benifits**:

>* To reduce our work in Manual-Copying.
>* To reduce errors, caused due to Manual-Copying.

## **_What are the types of Clonning ?_**

In JS, Clonning is of two types :

1. **Shallow Clonning**

>* Creates an extra reference to the existing Block of Memory (Object).
>* Separate memory is not allocated.
>* Change in block of memory(Object) affects all the reference pointers that are pointing to it.

2. **Deep Clonning**
>* Creates another copy of the existing Block of Memory (Object).
>* Separate memory is allocated.
>* Change in a block of memory(Object) does not affect other reference pointers as they both are different Blocks of Memory.

![pic1](https://miro.medium.com/max/488/0*RGt-o4ovYiIt_9nS.)
_Image to depict the differences between Shallow and Deep Clone._

**Consider this Example:**
```js
function jsonCopy(src) {                    //Function returning a new object copied using src object
  return JSON.parse(JSON.stringify(src));
}

const source = {a:1, b:2, c:3};             //Creating source object
const deepCopy = jsonCopy(source);          //Creating an object using deep Clone.
const shallowCopy = source;                 //Creating an object using shallow Clone.

console.log(target);                        // output: {a:1, b:2, c:3}
source.a = 'a';                             // Changing the value of 'a' in source object

console.log(source.a);                      // output: 'a' Value Changed
console.log(deepCopy.a);                    // output: 1   Value did not Change
console.log(shallowCopy.a);                 // output: 'a' Value Changed
```

**Here in this above example,**

When the value of `a` is changed from `a` to `1` of `source object`, there is a change in the value of `a` in `shallowCopy` object but not in the `deepCopy` object. This is caused because the `shallowCopy` object was reffering to the same `source` Object and hence the change was seen.

## **What are the ways to Clone?**

Clonning can be done in JS either making it a shallow copy or a deep copy. The usual methods followed are:

**1. Using Object.assign method.**

> * It’s a built-in static method on the Object object and is handled and provided by the language.
> * This method has a flaw that it only does a shallow copy. It means that nested properties are still going to be copied by reference.

*Consider this Example:*
```js
function bestCopyEverUsingAssign(src) {
  return Object.assign({}, src);
}
const source = {a:1, b:2, c:3};
const target = bestCopyEverUsingAssign(source);
console.log(target);                    // {a:1, b:2, c:3}

source.a = 'a';                         // Changing the value of 'a' in source object
console.log(source.a);                  // 'a'
console.log(target.a);                  // 1
```

**2. Using Spread (...) operator.**

> * The Rest/Spread Properties for ECMAScript proposal (stage 4) adds spread properties to object literals. It copies own enumerable properties from a provided object onto a new object.
> * Shallow-cloning (excluding prototype) or merging of objects is now possible using a shorter syntax than Object.assign().
> * This method has a flaw that it only does a shallow copy. It means that nested properties are still going to be copied by reference.

*Consider this Example:*
```js
function bestCopyEver(src) {
  const spreadClone = { ...source };
  return spreadClone;
}
const source = {a:1, b:2, c:3};
const target = bestCopyEver(source);
console.log(target);                    // {a:1, b:2, c:3}

source.a = 'a';                         // Changing the value of 'a' in source object
console.log(source.a);                  // 'a'
console.log(target.a);                  // 1
```
**3. Using Equal to (=) operator.**

> * This method only does a shallow copy. It means that nested properties are still going to be copied by reference.

*Consider this Example:*
```js
function returnObjectUsingEqualTo(src) {
  const obj = src;
  return obj;
}
const source = {a:1, b:2, c:3};
const target = returnObjectUsingEqualTo(source);
console.log(target);                    // {a:1, b:2, c:3}

source.a = 'a';                         // Changing the value of 'a' in source object
console.log(source.a);                  // 'a'
console.log(target.a);                  // 1
```
**4. Using Json Methods.**

> * Here we explicitly convert Object to JSON and back using JSON.parse and JSON.stringify.
> * They are built-in static methods on the JSON object and is handled and provided by the language.
> * This method creates a Deep copy. It means that nested properties are still not going to be copied by reference.

> **Note:** _Be careful about using this method as your source object must be JSON safe. So it may need some sort of exception handling to keep it safe in cases in which the source object is not convertible to JSON._

*Consider this Example:*
```js
function jsonCopy(src) {
  return JSON.parse(JSON.stringify(src));
}
const source = {a:1, b:2, c:3};
const target = jsonCopy(source);
console.log(target);                    // {a:1, b:2, c:3}

source.a = 'a';                         // Changing the value of 'a' in source object
console.log(source.a);                  // 'a'
console.log(target.a);                  // 1
```
**5. Using _.deepclone() from loadash library.**

> * It’s a  method from lodash library which is to be imported explicitly.
> * It is based on Structured cloning algorithm.
> * This method uses deep copy. It means that nested properties are not going to be copied by reference.

*Consider this Example:*
```js
import _ from 'lodash';
function returnObjectUsingLodash(src) {
  const lodashClone = _.cloneDeep(source);
  return lodashClone;
}
const source = {a:1, b:2, c:3};
const target = returnObjectUsingLodash(source);
console.log(target);                    // {a:1, b:2, c:3}

source.a = 'a';                         // Changing the value of 'a' in source object
console.log(source.a);                  // 'a'
console.log(target.a);                  // 1
```
SAVE TO CACHER