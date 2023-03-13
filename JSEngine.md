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

## Hoisting

**Behaviour**

1. Being able to use a variable's value in its scope before the line it is declared. ("Value hoisting")
2. Being able to reference a variable in its scope before the line it is declared, without throwing a ReferenceError, but the value is always undefined. ("Declaration hoisting")
3. The declaration of the variable causes behavior changes in its scope before the line in which it is declared.

**Observations** 
1. Function declarations above are hoisted with type 1 behavior
2. var declaration is hoisted with type 2 behavior.
3.  let, const, and class declarations (also collectively called lexical declarations) are hoisted with type 3 behavior.

**Note:- let, const are non-hoisting, because the temporal dead zone strictly forbids any use of the variable before its declaration.**

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

## Global execution context

Global Execution Context (GEC)
Whenever the JavaScript engine receives a script file, it first creates a default Execution Context known as the Global Execution Context (GEC).

The GEC is the base/default Execution Context where all JavaScript code that is not inside of a function gets executed.

For every JavaScript file, there can only be one GEC.
## Function Execution Context (FEC)
Whenever a function is called, the JavaScript engine creates a different type of Execution Context known as a Function Execution Context (FEC) within the GEC to evaluate and execute the code within that function.

Since every function call gets its own FEC, there can be more than one FEC in the run-time of a script.


## Task queue
The task queue is used for asynchronous tasks that are not part of the current execution context. These tasks will be executed after all synchronous code has finished executing.


## Microtask queue
The microtask queue is used for asynchronous tasks that are part of the current execution context. These tasks will be executed before any tasks in the task queue.

## Event loop


- It takes the event/function from the task queue, to the call stack.
- It only do so, whenever the call stack is empty.
- First it give priority to the Microtask queue, if stack is empty.
- If Stack is empty, microtask queue is empty then it will execute task queue.
  
## How to identify the given task is part of Microtask queue or Task queue?

- In JavaScript, you can determine whether an asynchronous task is part of the current execution context or not based on the mechanism by which it was scheduled.

- Tasks scheduled via setTimeout, setInterval, or requestAnimationFrame are considered to be part of the task queue and are not part of the current execution context. These tasks will be executed after all synchronous code has finished executing, as I explained in my previous response.

- Microtasks, on the other hand, are scheduled via Promise.then(), Promise.catch(), or queueMicrotask(). These tasks are considered to be part of the current execution context and are executed before any tasks in the task queue.

- So, if you're unsure whether an asynchronous task is a microtask or a task, you can look at the API that was used to schedule it. If it was scheduled using setTimeout, setInterval, or requestAnimationFrame, it's a task. If it was scheduled using Promise.then(), Promise.catch(), or queueMicrotask(), it's a microtask.

**Note:- Learn About the Promise First Before Going through these example**  
Example:- 
~~~
console.log('Start');

setTimeout(() => {
  console.log('Timeout');
}, 0);

Promise.resolve().then(() => {
  console.log('Microtask');
});

console.log('End');

Output:- 
Start
End
Microtask
Timeout


~~~
Example:-2 
~~~
console.log("Start");

setTimeout(()=>{
    console.log("set Timeout")
},0);

let promise=new Promise((resolve,error)=>{
    console.log("Success");
    resolve();
})


console.log("End");


~~~
**Note:- 
1. The first console.log("Start") statement is executed synchronously and logs "Start" to the console.
2. The setTimeout callback is added to the task queue and will be executed after all synchronous code has finished executing. Since the delay is set to 0ms, it will be executed as soon as possible, but after any currently executing code.
3. The Promise constructor is called synchronously and logs "Success" to the console. The resolve() function is also called synchronously, but the then callback that was attached to the promise is not executed yet, because it's scheduled as a microtask.
4. The last console.log("End") statement is executed synchronously and logs "End" to the console.
5. At this point, all synchronous code has finished executing, so the microtask queue is checked for any pending microtasks. If not then task from task queue is executed "set Timeout" to the console.




