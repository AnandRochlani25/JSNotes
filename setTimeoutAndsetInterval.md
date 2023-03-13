# setTimeout()

The global setTimeout() method sets a timer which executes a function or specified piece of code once the timer expires.  

If you do not specify the timer by default it will be considered as 0.

As setTimeout is an async functions

~~~
Example:- 
setTimeout(() => {
  console.log("Delayed for 1 second.");
}, "1000");
~~~


All the setTimeout will execute in parallel.

~~~

setTimeout(() => {
  console.log("this is the first message");
}, 5000);
setTimeout(() => {
  console.log("this is the second message");
}, 3000);
setTimeout(() => {
  console.log("this is the third message");
}, 1000);

// Output:

// this is the third message
// this is the second message
// this is the first message
~~~

## setInterval()

 Repeatedly calls a function or executes a code snippet, with a fixed time delay between each call.  

This method returns an interval ID which uniquely identifies the interval, so you can remove it later by calling **clearInterval()**.  

Syntax:-  
setInterval(code)  
setInterval(code, delay)  

Example:- 
~~~

// variable to store our intervalID
let nIntervId;

function changeColor() {
  // check if an interval has already been set up
  if (!nIntervId) {
    nIntervId = setInterval(flashText, 1000);
  }
}

function flashText() {
  const oElem = document.getElementById("my_box");
  oElem.className = oElem.className === "go" ? "stop" : "go";
}

function stopTextColor() {
  clearInterval(nIntervId);
  // release our intervalID from the variable
  nIntervId = null;
}

document.getElementById("start").addEventListener("click", changeColor);
document.getElementById("stop").addEventListener("click", stopTextColor);
~~~