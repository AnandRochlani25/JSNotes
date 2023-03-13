# Array
Arrays are used to store multiple values in a single variable

## concat()

It is used to merge 2 array.
- It return the new Array
- It does not modified the existing array.

~~~
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// Expected output: Array ["a", "b", "c", "d", "e", "f"]
~~~

## filter()

The filter() method creates a shallow copy of a portion of a given array, filtered down to just the elements from the given array that pass the test implemented by the provided function

~~~
function isBigEnough(value) {
  return value >= 10;
}

const filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtered is [12, 130, 44]
~~~

## find()

The find() method returns the first element in the provided array that satisfies the provided testing function. If no values satisfy the testing function, undefined is returned.

~~~
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// Expected output: 12

~~~


## forEach()

The forEach() method executes a provided function once for each array element.

~~~

const array1 = ['a', 'b', 'c'];

array1.forEach(print);

function print(element){
  console.log(element);
}

// Expected output: "a"
// Expected output: "b"
// Expected output: "c"

~~~


## indexOf()
The indexOf() method returns the first index at which a given element can be found in the array, or -1 if it is not present.

~~~

const ar= [1,2,3,4,1];

let x= ar.indexOf(1); 

console.log(x); //0

const ar= [1,2,3,4,1];

let x= ar.indexOf(10); 

console.log(x); // -1

const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison'));
// Expected output: 1

// Start from index 2
console.log(beasts.indexOf('bison', 2));
// Expected output: 4

console.log(beasts.indexOf('giraffe'));
// Expected output: -1
~~~

## join()
The join() method creates and returns a new string by concatenating all of the elements in an array (or an array-like object), separated by commas or a specified separator string. If the array has only one item, then that item will be returned without using the separator.

~~~
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// Expected output: "Fire,Air,Water"

console.log(elements.join(''));
// Expected output: "FireAirWater"

console.log(elements.join('-'));
// Expected output: "Fire-Air-Water"

~~~

## pop()
The pop() method removes the last element from an array and returns that element. This method changes the length of the array.
~~~
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// Expected output: "tomato"

console.log(plants);
// Expected output: Array ["broccoli", "cauliflower", "cabbage", "kale"]

plants.pop();

console.log(plants);
// Expected output: Array ["broccoli", "cauliflower", "cabbage"]

~~~


## push()

The push() method adds one or more elements to the end of an array and returns the new length of the array.

~~~

const animals = ['pigs', 'goats', 'sheep'];
const count = animals.push('cows');
console.log(count);
// Expected output: 4
console.log(animals);
// Expected output: Array ["pigs", "goats", "sheep", "cows"]

animals.push('chickens', 'cats', 'dogs');
console.log(animals);
// Expected output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]

~~~

## shift()

The shift() method removes the first element from an array and returns that removed element. This method changes the length of the array.

~~~

const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// Expected output: Array [2, 3]

console.log(firstElement);
// Expected output: 1

~~~

## slice()
The slice() method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. The original array will not be modified.

~~~
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// Expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// Expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// Expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// Expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// Expected output: Array ["camel", "duck"]

console.log(animals.slice());
// Expected output: Array ["ant", "bison", "camel", "duck", "elephant"]
~~~

## unshift()
The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.

~~~
const array1 = [1, 2, 3];

console.log(array1.unshift(4, 5));
// Expected output: 5

console.log(array1);
// Expected output: Array [4, 5, 1, 2, 3]


~~~

## map()
The map() method creates a new array populated with the results of calling a provided function on every element in the calling array.

~~~
const array1 = [1, 4, 9, 16];

// Pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// Expected output: Array [2, 8, 18, 32]

~~~

## reduce()

The reduce() method executes a user-supplied "reducer" callback function on each element of the array, in order, passing in the return value from the calculation on the preceding element. The final result of running the reducer across all elements of the array is a single value.  

The first time that the callback is run there is no "return value of the previous calculation". If supplied, an initial value may be used in its place. Otherwise the array element at index 0 is used as the initial value and iteration starts from the next element (index 1 instead of index 0).  

Example:-1  
~~~
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  initialValue
);

console.log(sumWithInitial);
// Expected output: 10

~~~

**Syntax**
- reduce((accumulator, currentValue) => { /* … */ })
- reduce((accumulator, currentValue) => { /* … */ },0)  
  
**Parameters**  
- **callbackFn**  
A function to execute for each element in the array. Its return value becomes the value of the accumulator parameter on the next invocation of callbackFn. For the last invocation, the return value becomes the return value of reduce().

The function is called with the following arguments:

1. accumulator
The value resulting from the previous call to callbackFn. On first call, initialValue if specified, otherwise the value of array[0].

2. currentValue
The value of the current element. On first call, the value of array[0] if an initialValue was specified, otherwise the value of array[1].

- **initialValue**  
It an optional parameter.  

  A value to which accumulator is initialized the first time the callback is called.  
  If initialValue is specified, callbackFn starts executing with the first value in the array as currentValue.  
  If initialValue is not specified, accumulator is initialized to the first value in the array, and callbackFn starts executing with the second value in the array as currentValue.  
   In this case, if the array is empty (so that there's no first value to return as accumulator), an error is thrown.

   Example:-1

   ~~~
    const getMax = (a, b) => Math.max(a, b);

  // callback is invoked for each element in the array starting at index 0
  let ar=[5,10,100];
  ar.reduce(getMax,0); // 100
   ~~~

   Example:-2

   ~~~
    // friends - an array of objects
  // where object field "books" is a list of favorite books
  const friends = [
  {
    name: "Anna",
    books: ["Bible", "Harry Potter"],
    age: 21,
  },
  {
    name: "Bob",
    books: ["War and peace", "Romeo and Juliet"],
    age: 26,
  },
  {
    name: "Alice",
    books: ["The Lord of the Rings", "The Shining"],
    age: 18,
  },
  ];

  // allbooks - list which will contain all friends' books +
  // additional list contained in initialValue
  const allbooks = friends.reduce(
  (accumulator, currentValue) => [...accumulator, ...currentValue.books],
  ["Alphabet"],
  );
  console.log(allbooks);
  // [
  //   'Alphabet', 'Bible', 'Harry Potter', 'War and peace',
  //   'Romeo and Juliet', 'The Lord of the Rings',
  //   'The Shining'
  // ]


   ~~~

**Note:-The reduce function is helpful with the operations performed on the objects property**
## splice()
splice() method changes the contents of an array by removing or replacing existing elements

~~~
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// Inserts at index 1
console.log(months);
// Expected output: Array ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, 'May');
// Replaces 1 element at index 4
console.log(months);
// Expected output: Array ["Jan", "Feb", "March", "April", "May"]

~~~


