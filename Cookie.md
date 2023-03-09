# Cookie

## What is cookie?

- A cookie is a small text file that a website saves on your computer or mobile device when you visit the site. 
-  login status, and browsing behavior.
-  Cookies can also be used to track your activity in the multiple website.

## Types of cookie :-

1. Session cookie :- This type of cookie will expire once the session is expired.
2. Persistant/Permanent cookie :- This type of cookie remain persistant in the user computer until the expiry time or being deleted.
   
## How to read the cookie?

let allcookie = document.cookie;

## How to create a new cookie?

document.cookie = newCookie

### What is the data type of newCookie?

Ans:- String

### How does newCookie stores the information?
   
Ans :- It stores the information in the form of key value pair.

Syntax :- document.cookie = "cookieName=cookieValue";  

**Example:-1**

_Step-1_ :- Write the following code

document.cookie="name=Anand";  

Run the code
_Step-2_ :- Replace the previous code with

console.log(document.cookie);  

_Step-3_ :- Run the code

In the console you will get the output as:-  
name=Anand  

You will ge the output as name="Anand"

### Can I store the multiple cookie?

Ans:- Yes, you can store the multiple cookie, but make sure to provide them different name. The name of the key is unique not the value.

_Step-1_ :- Write the following code

document.cookie="name=Anand";  
document.cookie="company=Prepbytes";
document.cookie="position=Executive"; 

Run the code
_Step-2_ :- Replace the previous code with

console.log(document.cookie);  

_Step-3_ :- Run the code


## Attribute in the cookie

There are multiple attribute you can set to the cookie. All of these attribute are optional.  

1. max-age=max-age-in-seconds: The maximum age of the cookie in seconds after which you cannot access the cookie.

**Example:-2**

_Step-1_ :- Write the following code  

document.cookie="name=Anand; max-age=120";


_Step-2_ :- Replace the previous code with

console.log(document.cookie);  

_Step-3_ :- Run the code

In the console you will get the output as:-  
name=Anand  

_Step-3_ :- Run the code after 2 minutes

The console will be empty.

2. path=path:-
- Indicates the path that must exist in the requested URL for the browser to send the Cookie header.
- Example:- (e.g., '/', '/mydir').
-  If not specified, it defaults to the current path of the current document location.

**Example:-**
~~~
// Set a cookie with a path of "/"
document.cookie = "username=Anand; path=/";

This cookie would be send to the browser for the url starts with '/'.

// Set a cookie with a path of "/products"
document.cookie = "username=John; path=/products";

This cookie would be send to the browser for the url starts with '/products'.


~~~

**Try this particular example after learning react routing**