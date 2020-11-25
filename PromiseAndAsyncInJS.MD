# **Promise functions** 

## **what is a Promise?**
A promise in JavaScript is similar to a promise in real life. When we make a promise in real life, it is a guarantee that we are going to do something in the future. Because promises can only be made for the future.

A promise has 2 possible outcomes: it will either be kept when the time comes, or it won’t.

This is also the same for promises in JavaScript. When we define a promise in JavaScript, it will be resolved when the time comes, or it will get rejected.

### Promises in JavaScript

First of all, a Promise is an object. There are 3 states of the Promise object:

* Pending: Initial State, before the Promise succeeds or fails
* Resolved: Completed Promise
* Rejected: Failed Promise

For example, when we request data from the server by using a Promise, it will be in pending mode until we receive our data.

If we achieve to get the information from the server, the Promise will be resolved successfully. But if we don’t get the information, then the Promise will be in the rejected state.

Additionally, if there are multiple requests, then after the first Promise is resolved (or rejected), a new process will start to which we can attach it directly by a method called chaining

## Creating and Using A Promise Step by Step

### Firstly, we use a constructor to create a Promise object:
```
const myPromise = new Promise();
```

### It takes two parameters, one for success (resolve) and one for fail (reject):
```
const myPromise = new Promise((resolve, reject) => {  
    // condition
});
```
### Finally, there will be a condition. If the condition is met, the Promise will be resolved, otherwise it will be rejected:
```
const myPromise = new Promise((resolve, reject) => {  
    let condition;  
    
    if(condition is met) {    
        resolve('Promise is resolved successfully.');  
    } else {    
        reject('Promise is rejected');  
    }
});
```

So we have created our first Promise. Now let's use it.
### **then( ) for resolved Promises:**

If the Promise gets resolved (success case), then something will happen next (depends on what we do with the successful Promise).
```
myPromise.then();
```
The then( ) method is called after the Promise is resolved. Then we can decide what to do with the resolved Promise. 
For example, let’s log the message to the console that we got from the Promise:
```
myPromise.then((message) => {  
    console.log(message);
});
```
### **catch( ) for rejected Promises:**
However, the then( ) method is only for resolved Promises. What if the Promise fails? Then, we need to use the catch( ) method.

Likewise we attach the then( ) method. We can also directly attach the catch( ) method right after then( ):
```
myPromise.then((message) => { 
    console.log(message);
}).catch((message) => { 
    console.log(message);
});
```
So if the promise gets rejected, it will jump to the catch( ) method and this time we will see a different message on the console.    
<br/>
<br/>
<br/>
<br/>
# Async functions

## Introduction

Promises give us an easier way to deal with asynchrony in our code in a sequential manner. Considering that our brains are not designed to deal with asynchronicity efficiently, this is a much welcome addition. Async/await functions, a new addition with ES2017 (ES8), help us even more in allowing us to write completely synchronous-looking code while performing asynchronous tasks behind the scenes.

The functionality achieved using async functions can be recreated by combining promises with generators, but async functions give us what we need without any extra boilerplate code.


### **Simple Example**
In the following example, we first declare a function that returns a promise that resolves to a value of funtion "hello" after 2 seconds. We then declare an async function and await for the promise to resolve before logging the message to the console:
```
function hello() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('🤡');
    }, 2000);
  });
}

async function msg() {
  const msg = await scaryClown();
  console.log('Message:', msg);
}

hello(); // Message: 🤡 <-- after 2 seconds
```
```
await is a new operator used to wait for a promise to resolve or reject. It can only be used inside an async function
```