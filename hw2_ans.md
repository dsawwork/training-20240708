

# Answers
1. Closures are useful because they provide a mechanism to encapsulate state for each function invocation. They can be used to simulate classes with private variables.
   ```
   function countFuncalls(method) {
    var count = 0;
    return {
        callFunc: function(...args) {
    method(...args);
   ++count; },
        get: function() { return count; },
        resetCount: function() {
   count = 0; }
    }
   }
   function add(x) {
   let b = 1;
   console.log("val", b+x);
   }
   let obj = countFuncalls(add);
   obj.callFunc(4);
   console.log(obj.get());
   
   ```
    above counts the time method is called while passing in the arguments to ca
3. `let` should be used when the variable will be updated, while `const` for variables that are fixed. Using both of them is good practice as it limits global variables that can pollute the namespace and makes code cleaner, debuggable and redable.

4.  a common mistake is declaring variable again inside a if block using `var`and defining it. as in the next code:
    ```  
    function foo() {
    var a = 3;
    console.log(a);
    if (true) {
        var a = 1;
        a = 2;
    }
    console.log(a);
    }

    foo();  
    ```

    `var a  =1 ` gets hoisted upwards and the value of `a` is the different in both log statements since `a` is redefined. TO fix this, use `let` or `const` to scope the variables to the block and limit values to the scope.
5.  
    ```
    [1,2,3] // push 3 to arr array ref
    [1,2,3] // no change as foo2 sets a new array reference
    [1,2,3,3] // b is set to the array reference and the number is pushed to the array
    [1,2,3,3] // no change as b is set
    ```


