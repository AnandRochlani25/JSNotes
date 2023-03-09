# Types of Error

1. ReferenceError: "x" is not defined

Whenever you try to access the variable which is not being declared. You will get **ReferenceError: "x" is not defined**.

**Example:-**
console.log(x);

2. TypeError: "x" has no properties

Example:-  
Lets say you are assuming that m1() will return an array. To this result you have to call length property.

~~~
function m1(flag){
 let ar=[1,2,3];
    if(flag)
        return ar;
}

let arr=m1(false);
console.log(arr.length);

Error:- TypeError: Cannot read properties of undefined (reading 'length')

~~~

But if you pass true to m1() you won't get this error as in this particular case.m1() will return an array.

~~~
function m1(flag){
 let ar=[1,2,3];
    if(flag)
        return ar;
}

let arr=m1(true);
console.log(arr.length);

Output:-
3

~~~

Example:-
~~~
<html>
    <body>
        <button id="#btn1" type="button" onclick="m1()">Click me</button>
        <button type="button" onclick="m2()">Click me-2</button>
      <script>

document.querySelector("btn2").addEventListener("click",function m1(){
 console.log("m1");
});

</script>
    </body>
</html>

 


~~~
3. TypeError: invalid assignment to const "x"

If you will try to modify the variable which is declared as const you will get this error.

Example:- 

~~~
const dummy= 80;

// …

dummy = 120; // TypeError: invalid assignment to const `dummy'

~~~

4. Syntax Error:- 
SyntaxError: Unexpected end of input (at <FileName_LineNumber>  
In this example function closing bracket is missing.  
~~~   
const charge = function (flag) {
  if (flag) {
    useSolarCells();
  } else {
    promptBikeRide();
};
~~~
