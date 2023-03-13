# JSEngine

## What is JS Engine?

- It's a piece of software that executes JS code.  
- The most popular engine is V8 developed by google.
- JavaScript engine always contains a call stack and a heap.
- The call stack is where our code is executed
using execution contexts.
- Then the heap is an unstructured memory pool
which stores all the objects that our application needs.

## What happen when you run your code?

1. So the first step, whenever you try to run the application, is to parse the code which essentially means to read the code.  
During the parsing process, the code is parsed into a data structure called
the abstract syntax tree or AST.  

Example of ATS ➖  
let x=2022;  

[AST explorer](https://astexplorer.net/)   
Use the above link to show it to the users.  
It has no connection with the DOM.

2. The next step is the compilation which takes the generated AST and compiles it into machine code.

3. The final step is Execution it takes machine code then gets executed right away.  

## Execution Context:- 
- Environment in which a piece of JS code is executed. It stores all the necessary information for a piece of code to be executed.

- Consider that you have placed the order from zomato/swiggy; when you receive the order, Can i say that its wrapped around, it contains the cutlery, tissue and etc.   
So in order to deliver the food, these are the add-ons, right? Which provides an adequate environment to deliver the food.

**Similarly, the execution contest provides an environment to execute the code.**

Execution Context contains 
- Variable Environment:-  
Inside a variable Environment (let var and const declaration).  
- All the functions that are declared in the top-level domain will be present. (Global Execution Context).  
- Scope chain.(Discussed in the function docs).   
- This keyword.  

## Temporal dead zone (TDZ)
A let or const variable is said to be in a "temporal dead zone" (TDZ) from the start of the block until code execution reaches the line where the variable is declared and initialized.  

While inside the TDZ, the variable has not been initialized with a value, and any attempt to access it will result in a ReferenceError. The variable is initialized with a value when execution reaches the line of code where it was declared. If no initial value was specified with the variable declaration, it will be initialized with a value of undefined.  

This differs from var variables, which will return a value of undefined if they are accessed before they are declared. The code below demonstrates the different result when let and var are accessed in code before the line in which they are declared.  

Example 1:-
~~~
{
  // TDZ starts at beginning of scope
  console.log(bar); // undefined
  console.log(foo); // ReferenceError
  var bar = 1;
  let foo = 2; // End of TDZ (for foo)
}

~~~
Example 2:-  
~~~

 <script>
          const x=1;
          {
            console.log(x);
            const x=2;
          }
</script>

~~~








