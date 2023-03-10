# Intersection API

## What is intersection API?

It provides a way to asynchronously observe changes in the intersection of a target element with an ancestor element or with a viewport.  

### What is a viewport?
It refers to the part of the document you're viewing which is currently visible on the screen.  


## What is the use of Intersection API?

- Lazy-loading of images or other content as a page is scrolled.
- Implementing "infinite scrolling" web sites, where more and more content is loaded and rendered as you scroll, so that the user doesn't have to flip through pages.
- Deciding whether or not to perform tasks or animation processes based on whether or not the user will see the result.

## Why not to use window object for the infinite scroll?

When you use  
 window.addEventListner('scroll', callback);

The call back function is called everytime you scroll, which can have a effect in the performace of the application.

## How Intersection API solves the above problem?

Intersection API will execute the call back function only if the element they wish to monitor enters or exits another element (or the viewport).  
Hence reduce the number of execution of the function. 

## How to create the Intersection API Object?

let observer = new IntersectionObserver(callback, options);

### What is options?

THe option is an object which contains multiple properties, which helps us to control when to make call to the callback function.

The list of properties are:- 
1. **root**
The element that is used as the viewport for checking visibility of the target. Must be the ancestor of the target. Defaults to the browser viewport if not specified or if null.

2. **rootMargin**  
Margin around the root. Can have values similar to the CSS margin property, e.g. "10px 20px 30px 40px" (top, right, bottom, left). The values can be percentages. This set of values serves to grow or shrink each side of the root element's bounding box before computing intersections. Defaults to all zeros.

- If I do not pass this particular property. The output will look something like this. The header will be locked and displayed when there is sufficent space for header, such that it doesn't overlap with the content.  
- [![image](https://www.linkpicture.com/q/Screenshot-456_1.png)](https://www.linkpicture.com/view.php?img=LPic6409c751bdf871655387014)
- But if I add the rootmargin :"100px"
- I will be able to view the heading after "100px" of invisibility.
- [![image](https://www.linkpicture.com/q/Screenshot-457_2.png)](https://www.linkpicture.com/view.php?img=LPic6409ca8997f4f608051480)
  
3. **threshold**  
Either a single number or an array of numbers which indicate at what percentage of the target's visibility the observer's callback should be executed. If you only want to detect when visibility passes the 50% mark, you can use a value of 0.5. If you want the callback to run every time visibility passes another 25%, you would specify the array [0, 0.25, 0.5, 0.75, 1]. The default is 0 (meaning as soon as even one pixel is visible, the callback will be run). A value of 1.0 means that the threshold isn't considered passed until every pixel is visible.


## How to pass target to the observer?

By calling ovserve(target) function and passing target element as an argument.  
