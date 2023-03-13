# String
# What is String?
The String object is used to represent and manipulate a sequence of characters.

## How to create a String?

1. const string1 = "A string primitive";  
2. const string2 = 'Also a string primitive';   
3. const string3 = `Yet another string primitive`;  
4. const string4 = new String("A String object");  

## How to access the character in the String?

~~~
let s="anand";
let ch =s[2];

//ch will store the "a" , as counting will start from 0.

~~~

# String property

## length
The length data property of a string contains the length of the string.

~~~
    const str = 'Life';

console.log(str.length);
// Expected output: 4

~~~

# String methods

## toLowerCase()
The toLowerCase() method returns the calling string value converted to lower case.

~~~
const sentence = 'The quick brown fox jumps over the lazy dog.';

console.log(sentence.toLowerCase());
// Expected output: "the quick brown fox jumps over the lazy dog."

~~~

## toUpperCase()
The toUpperCase() method returns the calling string value converted to uppercase (the value will be converted to a string if it isn't one).

~~~
const sentence = 'The quick brown fox jumps over the lazy dog.';

console.log(sentence.toUpperCase());
// Expected output: "THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG."

~~~

## trim()
The trim() method removes whitespace from both ends of a string and returns a new string, without modifying the original string.

~~~

const greeting = '   Hello world!   ';

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trim());
// Expected output: "Hello world!";

~~~

## substring()
The substring() method returns the part of the string from the start index up to and excluding the end index, or to the end of the string if no end index is supplied.

~~~
const str = 'Mozilla';

console.log(str.substring(1, 3));
// Expected output: "oz"

console.log(str.substring(2));
// Expected output: "zilla"
~~~

## split()
The split() method takes a pattern and divides a String into substrings by searching for the pattern, puts these substrings into an array, and returns the array.

~~~
const str = 'The quick brown fox jumps over the lazy dog.';

const words = str.split(' ');
console.log(words[3]);
// Expected output: "fox"


const chars = str.split('');//if you do not pass any argument it will seprate each character.
console.log(chars[8]);
// Expected output: "k"
~~~