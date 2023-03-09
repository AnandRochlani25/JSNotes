# DOM

## What is DOM?

Analogy  
  
If I wanted to control by television I have to do it using the Remote.
So can I say that remote act as bridge between you and the television.  

**Similarly DOM act as a bridge between JS and the HTML.  
DOM is like a tree like representation of the web-page.
Web browser are creating this DOM.**  
Example:-
~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Document</title>
</head>
<body>
    <h1>Prepbytes</h1>
    <<div> JS is easy to learn </div>
</body>
</html>
~~~




## Document Tree

For the above code the document tree will look something like this.  
~~~

DOCTYPE: html
HTML lang="en"
HEAD
#text:
TITLE
#text: Document
#text:
#text:
BODY
#text:
H1
#text: Prepbytes
#text: <
DIV
#text: JS is easy to learn
#text:

~~~

**In order to write JS code we have to use the script tag.**


~~~

<!DOCTYPE html>
<html lang="en">
<head>
     <title>Document</title>
</head>
<body>
    <h1>Prepbytes</h1>
    <<div> JS is easy to learn </div>
</body>
</html>


<script>
    console.log("Here I will write JS code");
</script>

~~~

## OnClick Event:- 

The onclick event is generated when user click on something.
Based on that event I want to execute certain logic.

**Syntax :-**

<element onclick=”functionName()”></element>

_Example:-_

~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Document</title>
</head>
<body>
    <h1>Prepbytes</h1>
    <div> JS is easy to learn </div>
    <button onclick="testMe()">Click ME</button>
</body>
</html>


<script>
 
    function testMe(){
        console.log("Test Function is executed");
    }
</script>

~~~

**Execution:-**  
User will click on ➖
Click Me(Button) → onClick=”testMe()”--> function testMe is being executed.


## Alert(<message>):-

The alert() function is used to display an alert box.  
Use :- It is used to give warning   
Example to Illustrate separation of logic using function  

~~~

<!DOCTYPE html>
<html lang="en">
<head>
     <title>Document</title>
</head>
<body>
    <h1>Prepbytes</h1>
    <div> JS is easy to learn </div>
    <button onclick="dummyFunction1()">Submit</button>
    <button onclick="dummyFunction2()">Reset</button>
</body>
</html>


<script>
 
    function dummyFunction1(){
        console.log("Dummy 1");
    }
    function dummyFunction2(){
        console.log("Dummy 2");
    }


</script>
~~~

## Document.getElementById(<id>)

- Example of Element :- h1, title, h2, h2,h3,div,span  
- That’s why in order to distinguish between the elements we provide them id’s.  
- These id are unique inside the HTML page.  

- So whenever I call document.getElementById(ID_NAME), it will return the matching element object or null.  

- Example:-

~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Document</title>
</head>
<body>
    <h1 id="heading">Prepbytes</h1>
    <div> JS is easy to learn </div>
    <button id="button1" onclick="dummyFunction1()">Submit</button>
    <button id="button2" onclick="dummyFunction2()">Reset</button>
</body>
</html>


<script>
 
console.log(document.getElementById("button1"));
</script>

~~~

## HTML Elements:-
~~~
<p> I am paragraph </p>

<p> :- This is nothing but a script tag.
 Content :- I am paragraph
~~~
_**The data which is present between the opening and the closing tag is called as innerText or textContent.**_

### Example:-
~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Document</title>
</head>
<body>
    <h1 id="heading">Prepbytes</h1>
    <div> JS is easy to learn </div>
    <button id="button1" onclick="dummyFunction1()">Submit</button>
    <button id="button2" onclick="dummyFunction2()">Reset</button>
</body>
</html>


<script>
 
console.log(document.getElementById("button1").innerText);
console.log(document.getElementById("button2"));
</script>



Output :- 

Submit
<button id="button2" onclick="dummyFunction2()">Reset</button>

~~~




## innerText vs innerHTML

**innerText:-**
1. It display the data or set the data in the form of plain text

2. It ignores the space

3. It will print the text without considering the inner html


**innerHTML**
1. It display the data or set the data in the form of HTML 
2. It doesn’t ignores the space
3. It will display the content of the HTML after rendering the tag.  





## How to change the innerText of an element? 

We can access that element by the help of id, and then we can make necessary changes.  

Syntax:-    
document.getElementById(“ID_NAME”).innerText=”New Text”;

Any modification made in DOM will reflect in HTML page.

~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Document</title>
</head>
<body>
    <h1>The new WWE Champion is </h1>
    <h2 id="name"> Brock Lesnar</h2>
    <button id="button1"onclick="findTheNewChampion()">Find</button>
   
</body>
</html>


<script>
  function findTheNewChampion(){
    document.getElementById("name").innerText="Roman Reigns";
    document.getElementById("button1").innerText="Found the New Champion";
  }
</script>

~~~




## Forms ➖  
In forms you use the input tags.    
Form:-  
- Username     

When form is submitted I need the value of this 1 input field.

~~~
<input id=”ID_NAME” type=”text” value=”0”>
~~~
## How does reset works?

Example:- To show how to read the value from the form and reset it.  
~~~

<!DOCTYPE html>
<html lang="en">
<head>
     <title>Document</title>
</head>
<body>
   <input type="text" id="username" value=""/>
    <button onclick="validate()">Submit</button>
    <button onclick="reset()">Rest</button>
</body>
</html>


<script>
  function validate(){
    console.log(document.getElementById("username").value);
   
  }


  function reset(){
    document.getElementById("username").value="";
  }
</script>

~~~


## getElementsByClassName(Class_Name)

- It returns the list of elements which matches the class_name.  
-  It will return the data in the form of array.

**Syntax:-**  

document.getElementsByClassName(<class_name>)

_**Example:-**_  

~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Crickter</title>
</head>
<body>
     <p class="india" id="hitMan">Rohit</p>
     <p class="india" id="Jr360">SuryaKumar Yadav</p>


     <p class="australia" id="powerpack">David Warner</p>
     <p class="australia" id="champion">Ponting</p>
   
    <p>3</p>
</body>
</html>
<script>
    let arr= document.getElementsByClassName("india");
    console.log(arr);
    console.log("length : "+arr.length );
   
     
</script>

~~~


## getElementByTagName(<Tag_Name>)

**Syntax:-**  

document.getElementsByTagName(<class_name>)  

- It will return the array containing all the elements matching that tag.  

~~~

<!DOCTYPE html>
<html lang="en">
<head>
     <title>Crickter</title>
</head>
<body>
    <h1>India</h1>
     <p class="india" id="hitMan">Rohit</p>
     <p class="india" id="Jr360">SuryaKumar Yadav</p>
    <h1>Australia</h1>
     <p class="australia" id="powerpack">David Warner</p>
     <p class="australia" id="champion">Ponting</p>


</body>
</html>


<script>
    let arr= document.getElementsByTagName("p");
    console.log(arr);
    console.log("length : "+arr.length );
    
     
</script>

~~~



## Applying CSS with the help of DOM

- With the help of DOM you can apply inline CSS to the html element  
  
**Example:-** 
~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Crickter</title>
</head>
<body>
    <h1>India</h1>
     <p class="india" id="hitMan">Rohit</p>
     <p class="india" id="Jr360">SuryaKumar Yadav</p>
    <h1>Australia</h1>
     <p class="australia" id="powerpack">David Warner</p>
     <p class="australia" id="champion">Ponting</p>


     <button onclick="changeColor()">Color Change</button>


</body>
</html>


<script>
   function changeColor(){
        let indianPlayers= document.getElementsByClassName("india");
        for(let i=0;i<indianPlayers.length;i++){
        indianPlayers[i].style.color="blue";


        }
        //Change the color of Australian Cricket to yellow          
   }
     
</script>


~~~



## querySelector(CSS Selector) ➖

- It will return the first matching element and apply the effect on it. 
- Instead of using different method fot tagName,className & id. You can use the one method.   
- In order to fetch the id, before the idname use :- #
- In order to fetch the class, before the class name use :-  .
- For the tag simply pass the tag name.


**Example:-**
~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Crickter</title>
</head>
<body>
    <h1 class="heading">India</h1>
     <p class="india" id="hitMan">Rohit</p>
     <p class="india" id="Jr360">SuryaKumar Yadav</p>
    <h1 class="heading">Australia</h1>
     <p class="australia" id="powerpack">David Warner</p>
     <p class="australia" id="champion">Ponting</p>


     <button onclick="changeColor()">Color Change</button>


</body>
</html>


<script>
   function changeColor(){
    //Tag Name
        document.querySelector("p").style.backgroundColor="cyan";
        //Change the color of Australian Cricket to yellow    
    //Id Name
        document.querySelector("#powerpack").style.backgroundColor="red";
    //CLass Name
        document.querySelector(".heading").style.backgroundColor="pink";
   }
     
</script>


~~~



## querySelectorAll(<css_selector>)

- It return all the elements that matches the css_selector.
- It will return the elements in the form of array.

**Example:-**

~~~

<!DOCTYPE html>
<html lang="en">
<head>
     <title>Crickter</title>
</head>
<body>
    <h1 class="heading">India</h1>
     <p class="india" id="hitMan">Rohit</p>
     <p class="india" id="Jr360">SuryaKumar Yadav</p>
    <h1 class="heading">Australia</h1>
     <p class="australia" id="powerpack">David Warner</p>
     <p class="australia" id="champion">Ponting</p>


     <button onclick="changeColor()">Color Change</button>


</body>
</html>


<script>
   function changeColor(){
    //Tag Name
    let indianPlayers = document.querySelectorAll(".india");
        indianPlayers[0].style.backgroundColor = "blue";
        //If you want to apply to all the elements then you should use loop
       


   }
     
</script>

~~~

## addEventListener

<button onclick=”functionName()”></button>


- Whenever I write the above syntax I am mixing the HTML code with JS.
- Instead of that you should use the eventListener
~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Crickter</title>
</head>
<body>
    <h1 class="heading">India</h1>
     <p class="india" id="hitMan">Rohit</p>
     <p class="india" id="Jr360">SuryaKumar Yadav</p>
    <h1 class="heading">Australia</h1>
     <p class="australia" id="powerpack">David Warner</p>
     <p class="australia" id="champion">Ponting</p>


     <button id="button1">Color Change</button>


</body>
</html>


<script>


    document.querySelector("#button1").addEventListener("click",changeColor)
   function changeColor(){
    //Tag Name


    let indianPlayers = document.querySelectorAll(".india");
        indianPlayers[0].style.backgroundColor = "blue";
        //If you want to apply to all the elements then you should use loop




   }
     
</script>

~~~


## Can I add multiple event listner to the same element?

Yes, You can add multiple events to the same element.

**Example** 

~~~
<!DOCTYPE html>
<html lang="en">
<head>
     <title>Crickter</title>
</head>
<body>
    <h1 class="heading">India</h1>
     <p class="india" id="hitMan">Rohit</p>
     <p class="india" id="Jr360">SuryaKumar Yadav</p>
    <h1 class="heading">Australia</h1>
     <p class="australia" id="powerpack">David Warner</p>
     <p class="australia" id="champion">Ponting</p>


     <button id="button1">Color Change</button>


</body>
</html>


<script>


    document.querySelector("#button1").addEventListener("click",changeColor);
    document.querySelector("#button1").addEventListener("click",changeBackground);
   
   function changeBackground(){
    let austrailianPlayers = document.querySelectorAll(".australia");
        austrailianPlayers[0].style.backgroundColor = "yellow";
   }
   
    function changeColor(){
    //Tag Name


    let indianPlayers = document.querySelectorAll(".india");
        indianPlayers[0].style.backgroundColor = "blue";
        //If you want to apply to all the elements then you should use loop




   }
     
</script>

~~~


# Project:- (Guess The Number)

Ask the student to develop it as the hands-on exercise.