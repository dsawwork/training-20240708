

# Answers
1. Closures are useful because they provide a mechanism to encapsulate state for each function invocation. They can be used to simulate classes with private variables.
2. `let` should be used when the variable will be updated, while `const` for variables that are fixed.

3.  a common mistake is declaring variable again inside a if block using `var`and defining it. as in the next code:
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

    `var a  =1 ` gets hoisted upwards and the value of `a` is the different in both log statements since `a` is redefined. TO fix this, use `let` or `const` to scope the variables to the block.

    4. 
    ```
    [1,2,3] // push 3 to arr array ref
    [1,2,3] // no change as foo2 sets a new array reference
    [1,2,3,3] // b is set to the array reference and the number is pushed to the array
    [1,2,3,3] // no change as b is set
    ```


