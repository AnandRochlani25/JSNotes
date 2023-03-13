# Asynchronous Programming

## How does Async Programming work?

### Analogy

Imagine you have to execute a task,

Step1. Make a call to google to process the result. -> It will take 12 sec  
Step2. Make a call to chatgpt to process the result→ It will take 13 sec  
Step-3 Print the result of google → It will take 2 sec  
Step-4 Print the result of chatgpt→ It will take 2 sec.  

So overall, in order to finish off the task if you go for synchronous way, it will take 25+2+2 sec because once you finish the task, you can go to the next one.   

But what if you call Google to let him process the result? Meanwhile, you should also make a call to chatpt, So overall it will take Max(12,13)+4 sec.  


## Which way is better asynchronous?


So if we have a scenario where we can execute 2 task parallelly, it is better to go for asynchronous if not its better to go for synchronous way.  

Let's understand more about asynchronous programming.  

So what will happen in this case is, 
Both the console will be displayed, and the event listener will be handled by the browser. Once the button is clicked, it will facilitate the execution of the m1 function.   

In short, your code won’t wait for the user to click on it.  


### Example:-1
~~~


let button=document.querySelector("button");
console.log("Before Event Listner");
button.addEventListener("click",m1);
function m1(){
    console.log("Execute m1");
}
console.log("After Event Listener");

~~~

**Note :- All the dom function are asynchronous and browser takes the responsibility of executing them**  

### Example:-2
~~~


let button=document.querySelector("button");
console.log("Before Event Listner");
button.addEventListener("click",m1);
function m1(){
    console.log("Execute m1");
}
let res=0;
for(let i=0;i<1000000000;i++){
    res=res+i;
}
console.log("After Event Listener");
~~~

If you try to execute this piece of code, Can I say that doesn’t matter how many times you click on this button? You have to wait to for loop to finish its execution before getting the response from the addEventListener.

Can I say that for loop is blocking the execution.

### Example:-3

Even When there is an alert box, can I say that it blocks the execution? Unless you click on it, there is no further execution.   
~~~
let button=document.querySelector("button");
console.log("Before Event Listner");
button.addEventListener("click",m1);
function m1(){
    console.log("Execute m1");
}
let res=0;
alert("HEllo");
console.log("After Event Listener");
~~~

So these 2 example shows that JS is a single thread. It will execute one task at a time. With the support of the browser, we can achieve asynchronous behaviour. 

### Example:- 4


This example shows that until and unless the call stack is not empty, the event from the callback queue/message queue won’t be taken. For the execution. 

~~~
let button=document.querySelector("button");
console.log("Before Event Listner");
button.addEventListener("click",m1);
function m1(){
    console.log("Execute m1");
}
let res=0;
alert("Hello");
console.log("After Event Listener");


setTimeout(m1,2000);
alert("I won't allow you to execute code unless clicked on it");

~~~
### Example:-5


This function shows, the timer of whichever function is completed that function will be pushed to callback for the execution. 


~~~

let button=document.querySelector("button");
console.log("Before Event Listner");
button.addEventListener("click",m1);
function m1(){
    console.log("Execute m1");
}
function m2(){
    console.log("Execute m2");
}
let res=0;
//alert("HEllo");
//console.log("After Event Listener");


setTimeout(m1,10000);
setTimeout(m2,5000);

~~~
Both tasks will execute in parallel as the browser supports multithreading. 
So both the task will be done in 10 sec.

## Custom Requirement

Let's say I don’t want this kind of behaviour. What I want now once the m1 function is done m2 function should be executed. Once m2 is done, m3 should execute, So If you want to execute your code in this way. It will look something like this, and I don’t want someone should call to the m2 and m3 functions. So, I this is the case, can I say that I have to make it an anonymous function? 


This piece of code has multiple callbacks, it kills the readability.
This is nothing but a **callback hell.**

~~~
let button=document.querySelector("button");
console.log("Before Event Listner");
button.addEventListener("click",m1);
function m1(){
    console.log("Execute M1");
    setTimeout(()=>{
        console.log("Execute m2");
        setTimeout(()=>{
            console.log("Execute m3");
           
        },10000)}
        ,10000);
}







let res=0;


setTimeout(m1,10000);


~~~



If you do not add the last 2 lines someone can code in this way, and this is not callback hell.

~~~
let button=document.querySelector("button");
console.log("Before Event Listner");
button.addEventListener("click",m1);
function m1(){
    console.log("Execute M1");
    setTimeout(m2,10000);
}


function m2(){
    console.log("Execute m2");
    setTimeout(m3,10000);
}


function m3(){
    console.log("Execute m3");
   
}
//Can I say that this code will translate something to this.






let res=0;


setTimeout(m1,10000);

~~~


## Fetch API

In JS make a call to the fetch function, by passing the URL you will get the promise object as a return type.


Example:-
~~~
const request=fetch("https://jsonplaceholder.typicode.com/posts");
console.log(request);
~~~
## What is Promise?

- Its a JS object  
- It is like a placeholder that can store the result of an asynchronous call.
- The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

_**Analogy**_

Consider the promise as a box of Christmas gifts.  
Now till the time you haven’t opened the box.
The result of your expression is in a pending state, right? You may like the present or you may not.  

So initially, can I say that promise made to you for Christmas is in a pending state?  

Now once you open the box, can I say that your expression is settled now?  

Either you will be happy, or you will be sad.  

So your promise is either fulfilled or rejected.  

Also, understand this point.   

### Are you creating the promise object?  
--------------------------------
No, right, it's being created by a fetch function.  

We are responsible for right down the logic to consume the promise.    

Let's say I want to create the Promise then how can I do that?  


## Chained Promises
The methods then(), catch(), and finally() are used to associate further action with a promise that becomes settled. As these methods return promises, they can be chained.

~~~
fetch("https://jsonplaceholder.typicode.com/posts").then((res)=>{
    return res.json();
}).then((data)=>{
     console.log(data);
});

~~~


Next promises are being used to get the data, that doesn’t make much sense why they have made res.json() to return the promise, but this is how it works.  

## How does .then Method Works?

The .then() method takes up to two arguments; the first argument is a callback function for the fulfilled case of the promise, and the second argument is a callback function for the rejected case. Each .then() returns a newly generated promise object, which can optionally be used for chaining.




## How to handle if a promise fails?

What you can do you can add a function that should execute once you encounter an error.
~~~
<button type="button" onclick="m1()">CLick Me</button>
<script>
function m1(){
fetch("https://jsonplaceholder.typicode.com/posts/").then((res)=>{
    console.log("hii")
    return res.json();
}, (error)=>{
    console.log("error");
    return error;
});
}
</script>

~~~

So you can pass 2 callback functions, 1st one will execute when it success, 2nd will execute when its fails.



## Catch()

 Before writing the catch, if there is any error, it will be handled, and after that, it will allow the normal execution of the program.

**Problem:-**

~~~

function m1(){
    fetch('https://jsonplaceholder.typicode.com/posts').then((res)=>{
            return res.json();
    },(error)=>{
        console.log(error.message);
    }).then((data)=>{
        if(data!==undefined)
        console.log(data);
    },(error)=>{
        console.log("error");
    });
};


~~~


 The simple way of handling the error


~~~
function m1(){
fetch("https://jsonplaceholder.typicode.com/posts/").then((res)=>{
    console.log("hii")
    return res.json();
}).then((data)=>{
     console.log("Success");
}).catch((error)=>{
    console.log("error");
});
}
console.log(“End of the Program”);

~~~

## finally()

You can also add finally function to the chain. This will execute no matter whether it’s a success or failure.

~~~
<button type="button" onclick="m1()">CLick Me</button>
<script>
function m1(){
fetch("https://jsonplaceholder.typicode.com/posts/").then((res)=>{
    console.log("hii")
    return res.json();
}).then((data)=>{
     if(data!==undefined)
           console.log(data);
}).catch((error)=>{
    console.log("Error Occured in our program",error);
}).finally(()=>{
    console.log("Always Execute this");
});
}
</script>

~~~

## Async/Await

~~~
async function m2(){
    console.log("Async");
    const result=await fetch("https://jsonplaceholder.typicode.com/posts/");
    const data=await result.json();
    console.log(data);


}

~~~

You can use try,catch and finally block in order to handle the error and to execute a piece of code which will execute irrespective of you caught the error or not. 





