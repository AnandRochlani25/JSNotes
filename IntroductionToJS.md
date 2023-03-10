# JS - Fundamentals

## What is Javascript?

It is one of the most popular and widely used programming languages. 

List of Companies That Use JavaScript, Expanded
1. eBay
2. Facebook
3. Google
4. Groupon
5. LinkedIn
6. Microsoft

## What can you do with Javascript?

- Add interactivity to webpages
- Make full web/mobile application using  javascript

## Where does Javascript code run?

- In the browser with the help of JS Engine provided by the browser for example(V8 provided by the chrome)
- With the help of Node you can run the JS in the local machine as well. Node provide the runtime for the Javascript.




## Where to write JS Code?

You can use the script tag in the HTML file to write down the JS code.

```
<script>
console.log('Hello world!');
</script>
```

## Separation of concerns 

Its always suggest to write the code in the different file. 


**HTML** → Structure of the document

**CSS** → Styling or look of the document

**JS** → Behaviour & interactivity of the document


## Variables

Variable are nothing but a named memory location.  

You can declare the variable in 3 ways. More on this in the later in the course

1. let
2. var
3. const
   
Syntax

let/var/const <Variable_Name> = <Variable_Value>

- A JavaScript identifier usually starts with a letter, underscore (_), or dollar sign ($). 
- Subsequent characters can also be digits (0 – 9). 
- Because JavaScript is case sensitive, letters include the characters A through Z (uppercase) as well as a through z (lowercase).


## What are the data types a variable can store?

**Primitives**

1. string
2. number
3. boolean
4. undefined
5. null


**Non Primitives**

1. object
2. array
3. function



## Objects

- Object is used to club multiple values into a single unit.
- Objects stores value in the key value format.
- You can access the object either using dot notation or the bracket notation.

We will discuss more on the objects in the later article.

**Ways to access properties:**



## Array

An array is used to store a list of objects

We will discuss more on the arrays in the later article.

## Functions

In order to seperate the logic based on the functionality we use the concept of the functions.

We will discuss more on the functions in the later article.


# Operators
 
- Arithmetic
- Unary Operator
- Assignment
- Comparision
- logical


### Arithmetic - performing calculations

~~~
let x = 5;  
let y = 4;


console.log(x + y); // addition oprator
console.log(x * y);
console.log(x - y);
console.log(x / y);
console.log(x % y); // remainder of division
console.log(x ** y) // x to the power y (exponentiation)

~~~
### Unary Operator 


// increment operator (++)
console.log(x++);
console.log(++x);

// decrement operator (--)
console.log(x--);
console.log(--x);


Run the following code by taking the intial value of x=10 and understand the functionality by yourself.

```
### Assignment operators

Assignment operator are used to assign a value to a variable,
right side value is assigned to the left side operator.

```
let x = 5;

value 5 will be stored in the variable x
```

 

### Comparison operators

At the end it evaluate a expression either to be true or false.

```jsx
let x = 5;

// relational - comparison - operators
console.log(x > 5);
console.log(x >= 5);
console.log(x < 5);
console.log(x <= 5);

// equality - comparison - operators 
// strict equality (check type + value)
console.log(x === 5);
console.log(x !== 5); // strict in-equality comparision

// lose equality - converts the type of rhs to match the type of lhs before comparing 
console.log(x == "5");
console.log(x != 5); // loose in-equality comparision
```

### Ternary operator

```jsx
let status = marks > 50 ? 'pass' : 'fail';
```

Syntax: 

```jsx
condition ? exprIfTruthy : exprIfFalsy
``` 

### Logical operators [with booleans]

Logical operator are used to combine multiple condition
- logical AND (&&) - **true** if both (or all) operands are true
- logical OR (||) - **true** if one of the operands is true
- not (!) - true only if the operand is false;



### Logical operators with non booleans (falsey / truthy)

<aside>
💡 There are only six ***falsey*** values in JavaScript: undefined , null , NaN , 0 , "" (empty string), and false. Anything that is not falsey it truthy.

</aside>

***When we use logical OR (||) with non booleans, javascript looks for the first truthy value and returns it as soon as it finds it. If it does not find any truthy value, it returns the last falsy value it finds.***

```jsx
let a = false;
let b = 0;
let c = null;

let z = a || b || c;

console.log(z); // null
```

```jsx
let a = false;
let b = 'Vivek';
let c = 'Rishi';

let z = a || b || c;

console.log(z); // 'Vivek'
```

***When we use logical AND (&&) with non-booleans, Javascript either returns the first falsy value it finds, else if all the operands are truthy,  it returns the last truthy value.***

```jsx
let a = 'Prachi';
let b = 'Vivek';
let c = 'Rishi';

let z = a && b && c;

console.log(z); // Rishi
```

```jsx
let bankbalance = 100;
let accountactive = true;

(bankbalance > 0) && (accountactive) && console.log('good balance and active');
// if first and the second expression will return a truth value only then the third expression will 
```

```jsx
let a = 0;
let b = 'Vivek';
let c = 'Rishi';

let z = a && b && c;

console.log(z); //0
```

```jsx
let a = 'Saikat';
let b = false;
let c = 'Rishi';

let z = a && b && c;

console.log(z); //false
```

```jsx

false || 'Vivek' // 'Vivek' is a truthy value
0 || 1 || 2 // 2 is sort circuited
!(undefined) // true
```

```jsx
let minimumBalance = 60000;
// 'saving account' // default
// 'classic account' // min-bal 50000
// 'premium account; // min-bal 100000

let accountType;
// identify the type of account
// use logical operators with falsy or truthy values
```



## Control flow

***Conditionals:* if .. else / switch .. case**

### if .. else

```jsx
if (condition) {
  statement
} else if (anotherCondition) {
  statement
} else if (anotherCondition) {
  statement
} else {
  statement
}
```

```jsx
let marks = 85;

/*
Example:- 
  marks < 50 : fail
  marks 51 - 70 : C
  marks 71 - 80 : B
  marks 81 - 100 : A
*/

if (marks < 50) {
  console.log('fail');
} else if (marks >= 50 && marks <= 70) {
  console.log('C Grade');
} else if (marks >= 71 && marks <= 80) {
  console.log('B Grade');
} else {
  console.log('A Grade');
}
```

### switch .. case

```jsx
switch (varaible) {
  case value:
    statement
    break;
  case value:
    statement
    break; 
  default:
    statement
}
```

```jsx
let skillLevel = "beginner" // beginner, intermediate, advanced, expert 

switch (skillLevel) {
  case 'beginner':
    console.log(45000);
    break;
  
  case 'intermediate':
    console.log(75000);
    break;
  
  case 'advanced':
    console.log(100000);
    break;
  
  default:
    console.log(150000);
}
```

## Loops

***Loops*** : If certain piece of code is repeated multiple times then we use the concept of the loops.

```jsx
console.log('Hello World');
console.log('Hello World');
console.log('Hello World');
console.log('Hello World');
console.log('Hello World');
```

**for / while / do .. while / for .. in / for .. of**

```jsx
// For loop
for(initialExpression; conditionExpression; incrementExpression){
  statements
}
```

```jsx
for (let i = 0; i < 5; i++) {
  console.log('Hello world')
}
```

The statements would keep running as long as the condition remains true; 

In the first iteration, the value of the loop counter is the one set in the initial expression; The condition is checked and if it returns true; the statement is run;

from the second iteration, the value of the loop counter is changed using the increment expression. The condition is checked and if it returns true; the statement is run;

.. this keeps repeating until the condition expression returns true.

```jsx
// While loop
let i = 0; // external loop counter

while (condition) {
  statement
  incrementExpression
}
```

```jsx
let i = 0;
while ( i < 5) {
	console.log('Hello world');
  i++;
}
```

**Exercise:** In the console, log all odd numbers in between 1 - 10

```jsx
for (let i = 1; i <= 10; i++) {
  if (i % 2 !== 0) {
    console.log(i)
  }
}
```

```jsx
// do...while loop

let i = 0; // external loop counter

do {
  if (i % 2 !== 0) { console.log(i) } // Statement executed at least once
  i++; // increment expression
} while (i <= 10); // condition expression

```

Being aware of ***infinite loop 😲***; if you forget to place an increment expression in a while or do..while loop; if you write an infinite condition in for loop;

`**for...in**`

**Iterating** over the **properties of an object** or **elements in an array**

```html
for (let propertyVariable in ObjectOrArray){
  // statement
} 
```

```jsx
const student = {
  firstName: 'Vivek',
  rank: 1,
  age: 36
}

for (let key in student) {
  console.log(key);
  console.log(student[key]);
}

const subjects = ['javascript', 'html', 'css'];

for (let index in subjects) {
  console.log(index);
  console.log(subjects[index]);
}
```

`**for...of**` 
Iterating over **arrays** & not concerned about index

```jsx
for (let subject of subjects) {
  console.log(subject);
}
```

```jsx
let movie = {
  title: 'movie title',
  releaseYear: 2020,
  rating: 4.5,
  director: 'director name',
}
```

`**break**` & `**continue**`