![Promise](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSCKpHUdbefR8cy81Kg-umxY02uH4X_OFaQ7XoHN2vj8zWa1DRj)
# **Promise**


A promise is an object that may produce a single value  in the future: either a `resolved` or `reject` value(a reason that it’s not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states: fulfilled, rejected, or pending. 



`Resolve` :- It means fulfilling the promise.

`Reject` :- It means promise is not fulfilled in given time or given contraint.

`Pending` :- The promise will always log pending as long as its results are not resolved or not reject yet. You must call .then on the promise to capture the results regardless of the promise state (resolved / reject or still pending)

![Prototype](https://www.nearform.com/wp-content/uploads/2019/02/Blog-img-01-1024x427.png)

<!-- Promise users can attach callbacks to handle the fulfilled value or the reason for rejection. -->



Let's understand with example:-


```js
// If condition is true

const flip = new Promise((resolve, reject) => {
  if (true) {
    resolve('success');
  } else {
    reject('failure');
  }
});

flip
  .then(result => console.log('result', result))
  .catch(error => console.log('error', error));

console.log('after flip');


// after flip
// result success
```  


```js
// If condition is false

const clean = new Promise((resolve, reject) => {
  if (false) {
    resolve('Cleaned Successfully');
  } else {
    reject('Not Cleaned');
  }
});

clean
  .then(result => console.log('result', result))
  .catch(error => console.log('error', error));

console.log('Cleaning must be completed');

// Cleaning must be completed
// error Not Cleaned

```
The flow has become a familiar top-to-bottom rather than left-to-right as in call-backs, which is a plus. However, **Promises** still suffer from some problems : —

![Promise](https://firebasestorage.googleapis.com/v0/b/bootcamp-5e181.appspot.com/o/image2.png?alt=media&token=6e9409e6-0c95-4582-9e2c-8e431a3c17c0)

- We still have to give a call back to every .then.
- Instead of using a normal try/catch, we have to use .catch for error handling.
- Looping over multiple promises in a sequence is challenging and non-intuitive. 



![Promise](https://firebasestorage.googleapis.com/v0/b/bootcamp-5e181.appspot.com/o/image5.jpg?alt=media&token=ce466eb6-52f3-4786-9529-0be7f914dc16)



To overcome this problem, async and await come to picture.


Let's continue async and await in another chapter.
