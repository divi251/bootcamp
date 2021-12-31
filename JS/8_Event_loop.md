![Event Loop](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSlZnVlsnssbTV7DczGWQ16CzOs0CJqtNuQQ6AMZbDw_xoh4PnP)
<!-- ![Event loop](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRc43XAD6FlkwjPV61kwg00Mg4FpllZ6imw-Nc-nojJnQ-dnMoE) -->
# EventLoop


<!-- **What is Single Threaded**

- A single threaded application is an application where only one process can run at any given poin. -->

The **`event loop`** is basically an endless loop, which keeps on checking whether there is something to be executed in the **`call stack`**. If the **`call stack`** is empty it checks the **`Event Queue`**, whether there is something to move to the **`call stack`**. If there is a method present, it moves it to the **`call stack`** and the method gets executed.


**Event Loop :-**

It's job is to look at stack or task queue.If stack is empty it takes  first thing on queue to stack.

**Call Stack :-** 

It’s a data structure which records the function calls, basically where in the program we are. If we call a function to execute , we push something on to the stack, and when we return from a function, we pop off the top of the stack.

![Prototype](https://miro.medium.com/max/600/1*E3zTWtEOiDWw7d0n7Vp-mA.gif)


**Event Queue :-**

A JavaScript runtime contains a Event queue, which is a list of 
events to be processed and the associated callback functions to execute. When the stack has enough capacity, a message is taken out of the queue and processed which consists of calling the associated function (and thus creating an initial stack frame). The message processing ends when the stack becomes empty again. In basic words , these messages are queued in response to external async events(such as a mouse being clicked or receiving the response to an HTTP request), given a callback function has been provided. If, for example a user were to click a button and no callback function was provided — no message would have been enqueued.


```js

function main(){
  console.log('A');
  setTimeout(
    function display(){ console.log('B'); }
  ,0);
	console.log('C');
}
main();

//	Output
//	A
// C
//  B
```


**`Explaination of code:-`**



The call to the main function is first pushed into the stack (as a frame). Then the browser pushes the first statement in the main function into the stack which is console.log(‘A’). This statement is executed and upon completion that frame is popped out.**A** is displayed in the console.

The next statement (setTimeout() with callback exec() and 0ms wait time) is pushed into the call stack and execution starts. setTimeout function uses a Browser API to delay a callback to the provided function. The frame (with setTimeout) is then popped out once the handover to browser is complete (for the timer).

console.log("C") is pushed to the stack while the timer runs in the browser for the callback to the exec() function. In this particular case, as the delay provided was 0ms, the callback will be added to the message queue as soon as the browser receives it (ideally).

After the execution of the last statement in the main function, the main() frame is popped out of the call stack, thereby making it empty. For the browser to push any message from the queue to the call stack, the call stack has to be empty first. That is why even though the delay provided in the setTimeout() was 0 seconds, the callback to exec() has to wait till the execution of all the frames in the call stack is complete.

Now the callback exec() is pushed into the call stack and executed. The alphabet C is display on the console. This is the event loop of javascript.


![Prototype](https://maxisam.github.io/2016/09/27/JavaScript-Note-Thread-Event-Loop/javascript_event_loop.png)





## **Questions :-**

**1. Is Node.js completely single-threaded ?**

This is a very common misconception about this technology. Node runs on a single thread, but some of the functions included in the Node.js standard library do not (the fs module functions, for example ); their logic runs outside of the Node.js single thread. This is done in order to preserve our programs’ speed and performance.



