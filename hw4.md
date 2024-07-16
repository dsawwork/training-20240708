## q1
- Instance method - function defined on a class that operates on an instance - particular object of that class with its own field values. Eg: Array methods like `join` operate on each instance (`Array.prototype.join`), with `this` inside the method set to the instance.
- Class method - function defined on a class that operates on the class, not on the object of the clas.  Eg: For creating arrays from object a static method `Array.from` is used. `this` inside the method will be the class constructor itself.


## q2
- Javascript is by nature single threaded - the runtime context uses an event loop that is a continuously loop that if idle, takes tasks from a  task queue and executes them. Tasks can be callbacks, event handlers, scripts etc.
- There are practical tasks that are asynchronous in nature like fetching request data, waiting for an event to handle it etc that. For such asynchronous tasks can be scheduled and put on a microtask or macrotask queue, which are eventually executed in first in - first out order.
- In this way, concurrency is handled.

## q3
- async/await is basically a kind of syntactic sugar over promises handling that makes promises iterative and easier to read and write in some cases. After a promise is resolved, subsequent promises are executed using `then` handlers and errors are handled using `catch`.
- The same flow can be implemented using `async` functions which return a promise that is wrapped around a return value of the function. `await` waits on a promise and unwraps the value that can be used subsequently, in the same format as the `then` handler with the parameter as the corresponding unwrapped value.

```
//Promise
fetch(url).then((val) => {val.json()}).catch((err) => console.log(err));


//await async same code different iterative flow. error can be wrapped inside a try catch
try {
const response = await fetch(url);
const jsonv = await response.json();
}
catch(e) {
  console.log(e);
}
```  

## q4
- No, `await` can only be used inside a `async` function as `await` expects a promise and unwraps a value after resolving the promise.  The `async` function would return a promise.

## q5

- Callback hell occurs when a bunch of event callbacks are nested multiple levels deep,making it difficult for developers to understand the functionality. For example, on a browser a user would click a button to trigger an API call and display that data on the page. A button event trigger callback should be defined inside which a fetch callback should be defined which hould handle error conditions, inside which another callback to display the data in a DOM element should be called, once all the operations happen successfully. Example of nested callbacks below. 
```
event.on(() => {
  if (..) {
    fetch().on((data) => {
       if(error) {
//handle error
}
}
}

```
- Using promises and async/await are a few better ways to rewrite such kind of code.
