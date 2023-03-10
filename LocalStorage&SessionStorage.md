# Local Storage

## What is local storage?

- The property allows JS sites and its application to store the information in the form of key-value pairs.

- So data stored in the local storage will be present even if you restart your browser.

## How Does Local Storage Work?

So To work with local storage:-
You are provided with 4 Functions.   
1. setItem() :- 
   - It keeps the data in the local storage in the form of key-value pair.
   - To Store String
     - let name =”Sujit”;
     - localStorage.setItem(“firstName”,name);
   - To Store Number
        - let mobile = 883965482;
        - localStorage.setItem(“mobileNo”,mobile);

   - To Store Array

     - You cannot store the array directly, If you want to store the array, you have to convert array into String.

### How to Convert Array into String?

- You have to use a function called JSON.stringify()

### How to convert String into Array?

- You have to use the function JSON.parse()



2. getItem(<key>) :- 
   - This function is used to retrieves the information from the localStorage. 
   - It Retrieve the information based on key
3. removeItem(<key>) :-
   - It will remove the particular key value pair from the localStorage.
4. clear() :- 
   - It will remove the all items in the local Storage.


## JSON( Javascript Object Notation) ➖

### What exactly is JSON?
- Its an data interchange format.
- Its based on JS Literals.(Number,String)
- Whenever you make the API call you get the data in most of the cases in the form of JSON.


###  Why should I use JSON?

It supports 6 data type:- 
String
Number
Array
Boolean
Null
Object
It also consist of key-value pair.


It helps us to interact with one application with another.
JS Map → Python X
JS→JSON→Python


“Students” : [{“id” : “PB101”, “name” : “Subhash Yadav” , “class” : “2nd Standard”} , {“id” : “PB201”, “name” : “Aniket Bhalerao” , “class” : “3rd Standard”}]

To convert from a JavaScript Object to a JSON string we can use the JSON.stringify method.
To convert from a JSON string to a JavaScript Object we can use the JSON.parse method.

~~~
<!DOCTYPE html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <form>
    <input id="name" type="text">
    <input id="score" type="number" min="1" max="5">
    <button id="submit">Submit</button>
  </form>
  <table>
    <thead>
      <th>
        Name
      </th>
      <th>
        Score
      </th>
    </thead>
    <tbody>
     
    </tbody>
  </table>


</body>
</html>


<script>
   document.querySelector("#submit").addEventListener("click",handleSubmit);
//5 times
//local storage will have the array with 5 object
   function handleSubmit(event){
      event.preventDefault();


      // To get the value from the form by passing id
      let name= document.querySelector("#name").value;
      let score= document.querySelector("#score").value;
      //truth value and the false value
     
      let arr=JSON.parse(localStorage.getItem("students")) || [];
      let obj={
        n : name,
        s : score
      }
      arr.push(obj);
      //store the value into the local Storage
      localStorage.setItem("students", JSON.stringify(arr));


     //Display the result
      displayData(arr);
     
   }


   function displayData(arr){
    document.querySelector("tbody").innerHTML="";
    for(let i=0;i<arr.length;i++){
      //create a row
    let row=document.createElement("tr");
      // Created 2 columns
      let col1=document.createElement("td");
      let col2=document.createElement("td");
      //I have added the data of the form to the column
      col1.innerText=arr[i].n;
      col2.innerText=arr[i].s;
      // I have linked row with these 2 columns
      row.append(col1,col2);
      console.log(row);
      //I linked the tbody with the row.
      document.querySelector("tbody").appendChild(row);
    }
   }
</script>
~~~


# Session Storage

sessionStorage is similar to localStorage; the difference is that while data in localStorage doesn't expire, data in sessionStorage is cleared when the page session ends.

## What is page session?

A page session lasts as long as the tab or the browser is open, and survives over page reloads
