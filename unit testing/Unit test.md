![enter image description here](https://actyv-bootcamp.s3.ap-south-1.amazonaws.com/banners/unit+testing.jpg)

Learn Unit testing with Chai and Mocha


# Why Testing ?
It comes always in mind that why testing is necessary. So basically the testing is a process of checking our product that it is not failing somewhere and it is satisfying all business needs. If we write code and somewhere it is giving wrong output even in decimals then it can lead to lot of financial loss to the company and loss of customer's trust will not let you grow. So testing can lead us to give a quality product. We will discuss the Test Driven Approch of coding with Unit Test by learnig Chai and Mocha. Let just see what is Test Driven Approch.

# Test Driven Approach
See the following figure this is how test driven development works.

![enter image description here](https://miro.medium.com/max/768/1*ieVWcSsJmeBbZFo6a_dL5g.png)

 Let us take an example of creating a building then we have to write the cases of handling like each room should be Fireproof, snowfall resistant, window should be wind resistance, a building should be tolerable to the earthquake. So when we are creating the rooms then we will chek that it is passing the fire test or not if it is not passing the required case then we have to build those things.
Similarly Test Driven approach works . As you can see in the figure we first write the test cases and that cases will fail because no code is there to pass it . so we will write the code that can pass it and then we refactor it.

# Unit test
Now let us have look that what the Unit test is ! Unit test is testing of individual modules of an application in isolation (without any interaction with dependencies) to confirm that the code is doing things right.
Do not be get confused with functional testing because functional testing is black box approach and unit testing is white box approach . In functional testing we chek the module's functionality, we don't have to care that how it is doing it from inside.

Folllowing figure demonstrating unit test 😂 . Before assembling all body parts we have to check the individual body parts that they are working or not.

![enter image description here](https://66.media.tumblr.com/3d4c0c08b7ee1787b4cf229251632da9/tumblr_inline_no7oigASv41raprkq_400.gifv )
 
 
 This is how unit test for body will look like
 

       Leg is able to run : Passing
       Hand is able to do push ups : passing
       Brain is able to see text on slate : passing


 
If we get faulty part then at begining we can save the cost. otherwise after assembling it will affect other parts. for example  if every thing is working but brain is not working then, after assembling nothing will work and it can lead to loss of time and money. After assembling the parts we again do a testing called Integration Testing so we can chek that all parts are working with each other's coordination or not.


**These are the points about unit test**
-   Unit testing is done before Integration testing by software developers using  [white box testing techniques]().
-   Unit testing does not only check the positive behavior i.e. the correct output in case of valid input, but also the failures that occur with invalid input.
-   Finding issues/bugs at an early stage is very useful and it reduces the overall project costs. As Unit testing is done before the integration of code, issues found at this stage can be resolved very easily and their impact is also very less.
-   A unit test tests small pieces of code or individual functions so the issues/errors found in these test cases are independent and do not impact the other test cases.
-   Another important advantage is that the unit test cases simplify and make testing of code easier. So, it becomes easier to resolve the issues at a later stage too as only the latest change in the code is to be tested.
-   Unit test saves time and cost, and it is reusable and easy to maintain.

# Basic Keys Before starting  :

To do unit test we will require `Chai` and `MochA`. We will se it deeply in this section but before starting those things let us understand the basic keywords in unit testing.

## Stubs & Drivers
**Stub** is basically a piece of code that Stub is created by the tester to simulates the activity of missing modules. When high-level modules are being tested and the other modules are not yet created.

![enter image description here](https://programsbuzz.com/sites/default/files/styles/large/public/2018-05/Please%20join%20us%20celebrateAdam%27s%208th%20Birthday%21_1.png?itok=gZi6BSSr)

**Driver**: Driver is a piece of code which is created by the tester in place of missing parent module. Test Drivers are the modules that act as a temporary replacement for a calling module(main module) and give the same output as the actual product.


## Code Smell
code smell is any characteristic in the source code of a program that possibly indicates a deeper problem.
![enter image description here](https://miro.medium.com/max/2554/1*ufqp4eDLabgkKTxqi168yA.png)

If we find any code smells then we have to rectify it or discard it as following figure says.

## Assertion Library 
Assertion libraries are tools to verify that things are correct.  
This makes it a lot easier to test your code, so you don't have to do thousands of `if` statements. Chai is a famous assertion library.

## Testing Framework
Testing frameworks are used to organize and execute tests.  
Mocha and Jasmine are two popular choices (and they're actually kinda similar).

## Chai

Chai  is an assertion library for NodeJS and the browser that can be delightfully paired with any javascript testing framework. Chai will provide features so you dont have to write lot of if  and else . Each module can be tested by writing normal english gramer like sentances. It provide assert, should, expect functions  to chek the modules.

Basically, mocha is a framework and chai is a library. Let's go a little deeper in mocha.

## Mocha
Mocha is a JavaScript test framework running on Node.js and in the browser. Mocha allows asynchronous testing, test coverage reports, and use of any assertion library.

We will directly go with mocha  framwork and will use chai library inside that framwork. So let just started with Mocha.


# Let us start with Mocha

Mocha uses hooks to organize its structure. Let's talk about them.

-   **describe()**: It's used to group, which you can nest as deep;
-   **it()**: It's the test case;
-   **before()**: It's a hook to run before the  _first_  it() or describe();
-   **beforeEach()**: It’s a hook to run before  _each_  it() or describe();
-   **after()**: It’s a hook to run after it() or describe();
-   **afterEach()**: It’s a hook to run after  _each_  it() or describe();

Do not be get worry by seeing these keywords. you will get it when we will start. Now let just see how we use it.
Basicaly we have to describe that what test we are performing so so we use `Describe` function. `Describe` takes two parameters. first will be string explaining the test and other parameter is a callback function in which we provide that what it should have to perfrom.


    describe('Description', () => {
    
        it('what module will give on pertical input ', () => {
    
         //perform test
    
        })
    
    })

## Unit Test for normal Function
let us suppose that we have a function which checks that value is greater then 0 or not and we have to write a unit test for it


     function isGreaterThenZero(value){
          if(value > 0){
            return true
          } else
             {
               return false
             }
        }

So unit test wiil be as follows :

    describe('Cheking the function  isGreaterThenZero', () => {
        
            it('it should return true', () => {
        
             expect.isGreaterThenZero(1).to.equal(true)
        
            })
        
        })
the above function will pass .

![enter image description here](https://actyv-bootcamp.s3.ap-south-1.amazonaws.com/unit-testing/1ehD.gif)


Means your code is qualifying for the test and we can move it for production

## Unit Test for APIs
To write unit test for APIs, Now we will require http-status-code library for cheking the status.

    const  HttpStatus  =  require("http-status-codes");
  we will also require chaiHttp

    const  chaiHttp  =  require("chai-http");
    
We will chek our api that it is giving the user list or not. Let suppose our API is this : `/users/read/5da3165fe845ca13587b51ac` . Unit test for this will be :

     chai.use(chaiHttp);
        
        describe("Reading the user", () => {
          // API Call
        
          it("it should read the user with an actual api call", done => {
            chai
              .request(server)
              .get("/users/read/5da3165fe845ca13587b51ac")
              .end((err, res) => {
                res.should.have.status(HttpStatus.OK);
                res.body.should.be.a("object");
                res.body.should.have.property("message").eql("User Found");
                done();
              });
          });

Let just try to understand first we are describing that what this Api will do and then we use `chai.request(server)` for requesting our server and then we use  `get` for accesing the route because we are reading the routes . if error will occur or response will be come then it will be pass in `end` and then we can write the logics to test the response. here we are cheking that response is having http status "ok" or not and further it is cheking that reponse is in form of object or not  and then it is cheking for particular keys to be matched by given value.

# Unit Test Patterns 

If you are doing unit test the you can write it in good way and those good approaches are tested and released by computer science engineers which is having less complexity and good performance . Let just see how to write unit test for differnt scenerios

## Dummies

Dummy objects are passed around but never actually used. Usually they are just used to fill parameter lists. It is an object that simply implements an Interface, and does nothing else. It’s not intended to be used in your tests and will have no effect on the behavior, sometimes a null object could be sufficient. An example would be passing an object into a constructor that isn’t used in the path you’re taking, or a simple object to add to a collection.

```

var TaskManager = function(){
    var taskList = [];

    return {
        addTask: function(task){
            taskList.push(task);
        },
        tasksCount: function(){
            return taskList.length;
        }
    }
}

// Test
var assert = require("assert")
describe('add task', function(){
    it('should keep track of the number of tasks', function(){
      var DummyTask = function(){ return {} };
      var taskManager = new TaskManager();

      taskManager.addTask(new DummyTask());
      taskManager.addTask(new DummyTask());

      assert.equal( taskManager.tasksCount(), 2 );

    })
})

```

## Spies

A test spy is an object that records its interaction with other objects throughout the codebase. When deciding if a test was successful based on the state of available objects alone is not sufficient, we can use test spies and make assertions on things such as the number of calls, arguments passed to specific functions, return values and more.

Test spies are useful to test both callbacks and how certain functions/methods are used throughout the system under test. The following simplified example shows how to use spies to test how a function handles a callback:

```

it("it should read the user using stub and spies", done => {
    let req = {
      params: {
        id: "5da3165fe845ca13587b51ac"
      }
    };

    // Spying on send and status method of a response object
    let res = {
      send: sinon.spy(),
      status: sinon.stub().returns({ json: sinon.spy() })
    };

    readUser(req, res, () => {
      // Testing Response Object
      expect(res.status.calledOnce).to.be.true;
      expect(res.status.firstCall.args[0]).to.equal(HttpStatus.OK);
      done();
    });
  });

```

## Stubs 

Test stubs are fake objects with pre-programmed behavior ( Simulation of behavior from other units ), Most of times they are simply returning fixed values. They are typically used for one of two reasons:

-   To avoid some inconvenient interface - for instance to avoid making actual requests to a server from tests.  
    
-   To feed the system with known data, forcing a specific code path.  
    

Javascript is flexible enough to accomplish this easily without any library


![enter image description here](https://miro.medium.com/max/2048/0*KdpZaEVy6GNnrUpB.png)

You can see in the following figure that there is no connection for grade system to fetch from a database then we are using stub for that. Means lower module is not available so stub is doing the mimicry of that module

Example of simple stub without any lib: 
```

 function () {
    var task = { completed = true }
}

```
















