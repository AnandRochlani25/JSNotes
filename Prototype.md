# Prototype & Prototype Inheritance

## Prototype :- Prototypes are the mechanism by which JavaScript objects inherit features from one another.



**Whenever I create an object by default property name prototype is assigned to it.**

Try this particular piece of code.
~~~
let obj= {
    "x" : 10,
    printX : function(){
        console.log(this.x);
    }
}

obj.printX();
console.log(obj);
console.log(obj.toString()); //[Object Object]
~~~

We didn’t created a function name toString but Still I can access it because of property name prototype.

**prototype property holds an object.**

## Prototype Chaining :-
First the function is searched in the current object if not found, then that particular function will be searched in its prototype holding property object.The same process will continue unless you encounter null.
~~~
myObject
	-> prototype →prototypeObj

	prototypeObj
		->prototype→prototypeObj2
	
prototypeObj2
		->prototype→null
~~~
This concept is nothing but prototype chaining.

~~~
Example :- 

let date=new Date();


let proto1=Object.getPrototypeOf(date);
console.log(proto1);


let proto2=Object.getPrototypeOf(proto1);
console.log(proto2);


let proto3=Object.getPrototypeOf(proto2);
console.log(proto3);

date
	-> prototype →dateProto

	dateProto
		->prototype→finalProto
	
finalProto
		->prototype→null


~~~

Analogy in the Real World.  
Example of Prototype Chaining  


1. Aradhya  
	->Father : Abhishek

2.  Abhishek  
	->Father : Amitabh

3. Amitabh  
	->Father : Harivash 
4. Harivansh  
	->Father : null


Description About Prototpye:- 

~~~
Every object in JavaScript has a built-in property, which is called its prototype. The prototype is itself an object, so the prototype will have its own prototype , making what's called a prototype chain. The chain ends when we reach a prototype that has null for its own prototype.
~~~

~~~
When you try to access a property of an object: if the property can't be found in the object itself, the prototype is searched for the property. If the property still can't be found, then the prototype's prototype is searched, and so on until either the property is found, or the end of the chain is reached, in which case undefined is returned.
~~~


##  Date Object
If you carefully look into the date object, whenever you make the call to the getMonth function its not available in the date obj.

Still we get the result, this is because getMonth function is avialable in the obj which is under the property __*prototype*__ in the date obj.

### Explaination  

~~~
Date:-
	There is no function called getMonth
	Prototype : DateProto

DateProto
	->This date obj has a function called getMonth()

date.getMonth()
:- It will search in the date obj
:- Then it will search in the dateProto (found and executed);

~~~

**Note :- DateProto is jsut a name given to obj.Its not a official name**  

Here I am trying to add the getMonth function in the date object.

~~~
date.getMonth =function(){
    return "Tiger Zindha hai";
}

When this statement was executed.

getMonth function was created inside a date obj.

Date:-
	There is function called getMonth
	Prototype : DateProto

DateProto
	->This date obj has a function called getMonth()
date.getMonth()---> Yes and it will execute it.

I can override the default behaviour.

~~~

~~~
console.log("Date");
let date=new Date();
console.log(date.hasOwnProperty('getMonth'));//false
console.log(date.getMonth());//1-->Month Feb
date.getMonth =function(){
    return "Tiger Zindha hai";
}
console.log(date.getMonth());//Tiger Zindha hai

~~~

## Explaination :-   
This should be predictable, given the description of the prototype chain.  
When we call getMonth() the browser first looks in myDate for a property with that name, and only checks the prototype if myDate does not define it. So when we add getMonth() to myDate, the version in myDate is executed.  
This is called "shadowing" the property.


## myObj.hasOwnProperty('fnName') :- 

- This function return the boolean value as result.
- If the particular object has that method it will return true/false.

## How to create a prototype inheritance

One of the way is to use :-   
**Object.create():-**  
Example:-
~~~
let parent={
    greet : function(){
        console.log("Good Eveneing");
    }
}
let child=Object.create(parent);
//This statement will create a child inheritance
->prototype:-parent
console.log(child);
child.name="Shubham";
child.greet();
//Parent--> Proto(x)---> Proto(Obj)-->Null

~~~
child:-
    prototype : parent


parent:-
    protype : DefaultObj
   
defaultObj:-
    prototype :- null

