# Functions

## Default Parameter

Thsi demonstrate all the possible scenario  
**Example:-1**
~~~
 m1(1,2,3);
    function m1(a,b,c){
        console.log("M1");
        console.log(a,b,c);
    }
  Output:-1,2,3 
~~~

**Example:-2**
~~~
    function m2(a,b,c){
        console.log(a,b,c);
    }
    m2(1,2);
   Output:- 
    //1 2 undefined
~~~
**Example:-3**

~~~
    function m3(a,b,c=3){
        console.log(a,b,c);
    }
    m3(1,2);
Output:- //1 2 3

~~~

**Example:-4**
~~~
    function m4(a,b,c){


        console.log(a,b,c);
    }
    m4(1,undefined,3);

Output:- //1 undefined 3
~~~
**Example:-5**
~~~

function m5(a=1,b=2,c=3){


console.log(a,b,c);
}
m5(1,undefined,3);

Output:- //1 2 3
~~~

## Abstraction:-

The details how the m1 function is called is being hidden from you, that is nothing but abstraction.

Example:- 

~~~
function m1(age){
    console.log(age);
}


let m2 = function(age){
    console.log(age);
}


function m3(value,fn){
    console.log(fn.name);
    fn(value);
}


m3(10,m1);
~~~



PLease read about HOF, First Class function, Callback Function[--5 min]


## Closure->
 Once the function execution is done, you cannot access its variable, but if
 function has return a function then it allows to access that memory location to that function.  
 In short inner function can access the variable declare in the outer function even the execution of outer function is completed.  
 Whenever you call the m1() it will return you the incrementCount().  
 That means incrementCount function can access the variable declare in m1().    

~~~
function m1(){
    let counter=0;
    return function incrementCount(){
        counter++;
        console.log(counter);
    }
}


let fn=m1();
 fn();
 fn();
 /*
 
~~~

## Scope 

There are 3 types of scope.
1. Global Scope
2. Function Scope
3. BLock Scope

Global Scope :- If I declare a variable outside of any function, can I say that its nothing but the global scope.

If Let is declared globally you can access it anywhere.  

**Example-1:-** 

~~~
let x=2;
function m1(){
    x=x+10;
    console.log("Inside a function",x);
}


m1();
x=x+5;
console.log("Outside a function",x);

~~~

**Example-2:-**   
If Var is declared globally you can access it anywhere.
~~~
var x=2;
function m1(){
    x=x+10;
    console.log("Inside a function",x);
}


m1();
x=x+5;
console.log("Outside a function",x);

~~~

**Note:- If Something is being declared global, it will be accessible outside as well as inside the function.**

**Example-3:-**

~~~
const x=2;
function m1(){
   let x=10;
    console.log("Inside a function",x);
}


m1();
//x=x+5;
console.log("Outside a function",x);


Output:- Inside a function 10
Outside a function 2

~~~

It looks for the variable **x** inside the function, if not found then it will look for the global declaration.   
If you notice careful, local variable shadow the value provided by the global variable if both are having same.This concept is called variable shadowing.    

**Example-4:-** 


## Scope Chaining

- If its a nested function,  
- First it will search for the declaration in the function  
- If not found, check the outer function  
- If not found, check the global declaration.  
- If not found,then throw the error.  
~~~
const x=2;
function m1(){
   let x=10;
    console.log("Inside a function",x);
   return function m2(){
        let x=5;
        console.log("Nested ", x);
    }
}


let fn=m1();
fn();
//x=x+5;
console.log("Outside a function",x);

Output:- 
Inside a function 10
 Nested  5
Outside a function 2

~~~


**Example-5:-** 

If something is defined inside a function it will be access inside that function only, unless a until you return that value.

~~~
const x=2;
function m1(){
    console.log("Inside a function",x);
   return function m2(){
        let x=5;
        console.log("Nested ", x);
    }
}


let fn=m1();
fn()
//x=x+5;
console.log("Outside a function",x);


~~~

**Example-6**:-  
//It will give error at the last line since the variable is declared inside a function, doesn’t matter whether its var/let/const.

~~~
function m1(){
   var x=10;
    console.log("Inside a function",x);
   return function m2(){
       
        console.log("Nested ", x);
    }
}


let fn=m1();
fn();
//x=x+5;
console.log("Outside a function",x);

~~~

**Example:-7**:-
//If you forget to declare the variable, even inside a function it will be declared globally by JS with var.  

~~~
function m1(){
    x=10;
    console.log("Inside a function",x);
   return function m2(){
       
        console.log("Nested ", x);
    }
}


let fn=m1();
fn()
//x=x+5;
console.log("Outside a function",x);

~~~

**Example:-8**  

//It will give error

~~~
function m1(){
    x=10;
    console.log("Inside a function",x);
   return function m2(){
       
        console.log("Nested ", x);
    }
}
console.log("Outside a function",x);
let fn=m1();
fn()
//x=x+5;


~~~

## Block Scope

**Block Scope is same as functional scope.
But only let & const supports it.**


**Example:-9**  
//You cannot keep var in the block scope even if you do, it will have the scope of its parent→ functional/global.
~~~
function m1(){
   let x=10;
   if(x>5){
    var t=10;


   }
    console.log("Inside a function",t);
 
}
console.log("Outside a function",t);
let fn=m1();
~~~







