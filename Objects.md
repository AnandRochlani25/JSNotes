# JS - Objects in depth

It stores the value in the form of key value pair, value can be any datatype. 

Properties names are generally string.  


#1 **Grouping related variables** 
Example:- To show that it groups multiple value into the single group.

```
// grouping related variables
let account = {
  name: 'Vivek',
  type: 'Simple Saving',
  balance: 100000,
  active: true,
}
```

#2 **Adding & Removing Properties and Methods after creating an object [Dynamic objects]**

```jsx
account.reference = 'Some one';
account['new_property'] = 'Yet some value';
console.log(account);

delete account.reference;
console.log(account);
```

#3 **Passing into a function as an Argument**

```jsx
// can be passes to a function as an argument
function printAccountDetails(obj) {
  console.log('Name: ', obj.name, 'Type: ' ,obj.type, 'Active: ' , obj.active, 'Bal: ' , obj.balance);
}

printAccountDetails(account);
```

#4 **You can **

```jsx
let account = {
  name: 'Vivek',
  type: 'Preffered Savings',
  balance: 100000,
  active: true,
  print: function () {
    console.log('Name: ', this.name, 'Type: ', this.type, 'Active: ', this.active, 'Bal: ', this.balance);
  }
};

account.print()
```

**As our application grows, we need different ways to create Objects. How to create multiple accounts? for example.**

#5 **Factory functions:**

```jsx
function createAccount(accountName, accountType, accountBalance, isActive) {
  let account = {
    name: accountName,
    type: accountType,
    balance: accountBalance,
    active: isActive,
    print: function () {
      console.log('Name: ', this.name, 'Type: ', this.type, 'Active: ', this.active, 'Bal: ', this.balance);
    }
  };

  return account;
}

const acc1 = createAccount('Vivek', 'Saving', 100000, true);
acc1.print();

const acc2 = createAccount('Akash', 'Premium', 200000, true);
acc2.print();
```

convention: camelCase

Problems with this factory function: 

- if we have 5000 user objects, we have 5000 copies of the print() function.

**Factory function Using Object.setPrototypeOf():**

```
let sharedAccountFucntions = {
  print: function () {
    console.log(this);
    console.log('Name: ', this.name, 'Type: ', this.type, 'Active: ', this.active, 'Bal: ', this.balance);
  }   
}

function createAccount(accountName, accountType, accountBalance, isActive) {
  let account = {}
  Object.setPrototypeOf(account, sharedAccountFucntions);

  account.name = accountName;
  account.type = accountType;
  account.balance = accountBalance;
  account.active = isActive;  

  return account;
}

const acc1 = createAccount('Vivek', 'Saving', 100000, true);
console.log(acc1);
acc1.print();

const acc2 = createAccount('Akash', 'Premium', 200000, true);
console.log(acc2);
acc2.print();
```

**Factory function** **Using Object.create() :** 

```jsx
let sharedAccountFucntions = {
  print: function () {
    console.log(this);
    console.log('Name: ', this.name, 'Type: ', this.type, 'Active: ', this.active, 'Bal: ', this.balance);
  }   
}

function createAccount(accountName, accountType, accountBalance, isActive) {
  let account = Object.create(sharedAccountFucntions);
    
  account.name = accountName;
  account.type = accountType;
  account.balance = accountBalance;
  account.active = isActive;  

  return account;
}

const acc1 = createAccount('Vivek', 'Saving', 100000, true);
console.log(acc1);
acc1.print();

const acc2 = createAccount('Akash', 'Premium', 200000, true);
console.log(acc2);
acc2.print();
```



## Value vs Reference

**Value Types:** Number, String, Boolean, undefined, null, Symbol

**Reference Types:** Object, Function & Array

```jsx
let x = 10;
let y = x; // value copied by value

x = 20;

console.log('x: ', x); // 20
console.log('y: ', y); // 10

let a = {value: 10};
let b = a; // Object copied by reference

b.value = 20;

console.log('a: ', a); // {value: 20}
console.log('b: ', b); // {value: 20}
```

Primitives are copied by their value & Objects are copied by their reference.



## Methods of Object constructor

`Object.keys` give us an array of all the properties of an object.

```jsx
console.log(Object.keys({x: 1, y:2})); // ["x","y"]
```

`Object.entries` gives us an array of key value array of an object

```jsx
console.log(Object.entries({x: 1, y:2})); 
//[['x', 1],['y', 2]]
```

Check if a property exists in an object using the `in` keyword

```jsx
if ('x' in {x: 1, y:2}) {
  console.log('yes x is a propery of the object')
}
```



`Object.assign` gives us a way to clone properties and members (properties & methods) of an object into another object.

```jsx
// Old way
// let clonedAccount = {};

// for (let key in account) {
//   clonedAccount[key] = account[key];
// }

// console.log(clonedAccount); // you may not see the method in codepen, open actual console.

let clonedAccount = Object.assign({}, account);
console.log(clonedAccount);
```

Cloning can also be done using the `...` spread operator:

```jsx
let clonedAccount = { ...account };
```


## Built-in Objects in Javascript

### Math

Common math functions 

```jsx
Math.floor( 45.95); //  45
console.log(Math.ceil(7.004)); // 8
console.log(Math.max(1, 3, 2)); // 3
console.log(Math.min(2, 3, 1)); // 1



### String

**constructor**.

The sequence of characters is termed as string. 



```jsx
string1.length;
string1[0];
string1.indexOf('or');
string1.toUpperCase();
string1.toLowerCase();
string1.trim();
string1.split(' ');
```


