
![async & await](https://nodehq.io/content/images/size/w2000/2019/07/cover-3.png)
____
# Async/Await
____

To work with promises more comfortably we use Async/await.

**ASYNC functions**

Let’s start with the async keyword. It can be placed before a function, like this:

> ```js
> async function f() {
>   return 1;
> }
> 
> ```

Always any async function returns a promise. even if you don’t return a promise the values which are returned wrapped into a resolved promise automatically.

**Point to be noted:**

So, async ensures that the function returns a promise, and wraps non-promises in it
Now let's understand the Await keyword.

**AWAIT:**

Async functions pause at each await `expression`.
An await acts on an expression. When the expression is a promise, the evaluation of the async function halts until the promise is resolved

ex:
> ```js
> async function f() {
> 
>   let promise = new Promise((resolve, reject) => {
>     setTimeout(() => resolve("done!"), 1000)
>   });
> 
>   let result = await promise; // wait until the promise resolves (*)
> 
>   alert(result); // "done!"
>}
>
>```

When the expression is a non-promise value, it is converted to a promise using Promise.resolve and then resolved.

Ex:
> ```js
> async function fn() {
> const a = await 9;
> const b = await delayAndGetRandom(1000);
> const c = await 5;
> await delayAndGetRandom(1000);
> 
> return a + b * c;
> }
> 
> ```

Here delayAndGetRandom is function which returns a promise with time-delayed.

**Point to be noted:**

If you try to use await in non-async function,there would be a syntax error.

**Async/Await:**
In the following example, we first declare a function that returns a promise that resolves to a value of 🤡 after 2 seconds. We then declare an async function and await for the promise to resolve before logging the message to the console:
> ```js
> function scaryClown() {
>   return new Promise(resolve => {
>     setTimeout(() => {
>       resolve('🤡');
>     }, 2000);
>   });
> }
> 
> async function msg() {
>   const msg = await scaryClown();
>   console.log('Message:', msg);
> }
> 
> msg(); // Message: 🤡 <-- after 2 seconds
>```