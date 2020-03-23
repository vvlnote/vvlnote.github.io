---
layout: post
title:      "What I know about JavaScript Closure - part I"
date:       2020-03-22 21:27:40 -0400
permalink:  what_i_know_about_javascript_closure
---


Recently, I am trying to work on the google map, to have google map display in my project. I used react-google-maps package. By reading the [spec](https://www.npmjs.com/package/react-google-maps) of react-google-maps, there is a term "**HOC**". It stands for **Higher-Order Component**. and the concept of it is derived from "**HOF**", it stands for **Higher-Order Function**.   I have heard this term before, and I would like to know what is it.  

### First class function
In JavaScript,  functions are first class functions, they can be treated like any oth er variables. 
A first class function can be:  
* passed as an argument to other functions => we call this function is a callback funtion.
* returned by another functions
* assgined as a value to a variable.

### Higher Order Function 
**It is a function that takes a function as an argument, or returns a function.**  
We already encoutered a lot of functions that take a function/functions as arguments to other functions.  

**Here, I would like to focus on returning a function. **   
The reason is that when I saw this statement, there was another word came up from my mind, closure. I did not know if this kind of connection is relevant or not. You are welcome to comment on this.

  
### Closure  
> What is a Closure?  
> A **closure** is the combination of a function bundled together (enclosed) with references to its surrounding state (the **lexical environment**).  
> In other words, a **closure** gives you access to an outer functions' scope from a inner function.   
>   


Closure defines how a function can maintain a record of the environment in which it was called. It means that a function can keep track of the arguments and variables it was initally called with, even when it's called outside fo that scope.


#### Why closure matters  
Closures are one of the most powerful features of JavaScript. JavaScript allows for the nesting of functions and grands the inner function full access to all the variables and functions defined inside the outer function, and all other variables and functions that the outer function has access to.  


```
function clickMe(msg) {
    let count = 0;
    return function(){
        count += 1;
        console.log(`${msg} has been click ${count}`);
    }
}


let click = clickMe(`clickMe button`);
click();
click();
click();
```   

when clickMe(msg) is called, it return anonymous function, which is assigned to click. so clck is presented as function name. click() to evoke the function delclared insdie function clickMe.

Output: 

```
clickMe button has been click 1
clickMe button has been click 2
clickMe button has been click 3
```  
From  the output, 1, 2, 3 are the value of count, and clicMe button is the parameter that I passed in when I call ClicMe. 
Even click is called outside of clickMe function, but it still can access count, and msg from it outer environment enclosed inside of its parent function (i.e. clickMe). 


#### use-cases for closures  
* In JavaScript, closures are the primary mechanism used to enable data privacy.  
Please refer to the code in the previous section. msg, and counter are the private variables, which can not be accessed by outside function, only click (which is presented the anonymous function) can access it, and display the result. 
* Closures can be used to create stateful functions whose return values may be influenced by their internal state.  
* In functional programming, closures are frequently used for partial application & curring. 




