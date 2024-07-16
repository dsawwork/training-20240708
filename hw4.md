## q1
- Instance method - function defined for an object that operates on an instance - particular object. the object at the prototype methods will be present for all object instances defined on the prototype.
- Class method - function defined on a class that operates on a broad level = like creating arrays from object, `Array.from`


## q2
- Javascript is by nature single threaded - so the runtime context uses an event loop that takes tasks from a  task queue and executes them. Tasks can be callbacks, event handlers etc.
- An illusion of concurrency is maintained by running one task at a time.

## q3
- async/await is basically a kind of syntactic sugar over promises handling that makes promises iterative and easier to read and write in some cases. After a promise is resolved, subsequent promises are executed using `then` handlers and errors are handled using `catch`.
- The same flow can be implemented using `async` functions which return a promise that is wrapped around a return value of the function. `await` waits on a promise and unwraps the value that can be used subsequently, in the same format as the `then` handler
- with the parameter as the corresponding unwrapped value.

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
- No, `await` can only be used inside a `async` function as `await` expects a promise and unwraps a value after resolving the promise.  The `async` function should return a promise, and since `await` works on promises it makes sense that there might be issues in vanilla functions.

## q5

- Callback hell is when 
