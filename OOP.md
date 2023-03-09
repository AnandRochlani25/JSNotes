
# Object Oriented Programing

## Class:- It acts as a blueprint for the object.


~~~
To show the resemblance with the Object.

 //Account Class
//#balance
//function to print this #balance;
/*let obj={
    #balance :10,
    getBalance : function(){
        console.log("Balance ="+this.#balance);    
    }
    obj.getBalance();
}*/



class Bank{
    //It acts a property
    name;
    //It will only be executed oonce during object creation
    constructor(name){
        this.name=name;
    }
    //Its like function you create in a object
    getBankName(){
        console.log("The name of the bank is"+this.name);
    }
}

~~~

## Constructor :- 
1. It executes only once when the object is created.
2. In JS there is only 1 constructor possible.
3. It is used to initialize the value during the object creation.
   
## Super Keyword.

1. super keyword is used to pass the value from child class to the super class.
2. Even though if you don't want to pass any you can simply call super() with no argument.

##  Use of '#' Symbol

1. If you want to make the variable and the method as private you can use the '#' key infront of it. 
2. Private variable/function are not accessable outside the class. 
3. These are generally the helper function.
4. The access to the necessary variable is provided with the help of setter and getter method.

## Inheritance 

If you want to access the parent class variable and function in the child class we use the cocept of inheritance.

~~~

//In order to provide the inital value you have to use = instead of  :
class Account extends Bank{
    //If you want to declare property as private
    #balance;
    //Constructow with the default param value
    constructor(n,b=0){
        //Always super would be the first line inside the constructor,
        // it is used to pass value to be super class/parant constructor
        super(n);
        //it will update the property of balance variable.
        this.#balance=b;
    }
    deposit(amount){
        this.#balance+=amount;
        //this.#balance=this.balcne+amount;
    }
    withdraw(amount){
    if(this.#balance>=amount)
        this.#balance=this.#balance-amount;
    else
        console.log("Insufficient Balance");
    }
    getBalance(){
        console.log("Balance ="+this.#balance);                                          
    }
}

//This is how you create an object from the blueprint of a class

let acc1=new Account("SBI",1000);// getBalance()
//It display how protoype chaining works with inheritance
//Account-->Bank-->Object-->null
console.log(acc1);
//To show you can access super class function just like prototype chaining.
acc1.getBankName();
//What will be the value if prototype :- constructor/Object



~~~





