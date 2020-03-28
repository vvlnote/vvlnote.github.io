---
layout: post
title:      "What I know about JavaScript Closure - part II"
date:       2020-03-27 20:28:48 -0400
permalink:  what_i_know_about_javascript_closure_-_part_ii
---

This post is continual of [What I know about JavaScript Closure - part I](https://vvlnote.github.io/what_i_know_about_javascript_closure).  In this post, I will work on the use-cases for closure.  

### use-cases for closures  
#### *** In JavaScript, closures are the primary mechanism used to enable data privacy.  **
I would like to elabrate more detail about the how to keep tracking the click amout in the [What I know about JavaScript Closure - part I](https://vvlnote.github.io/what_i_know_about_javascript_closure)  

* When you tried to keep track some activities, in my example, I would like to track how many times that I have clicked on a button.  The first thing you will think is to create a variable for tracking the total amount of clicking. However, for a function, the most intuitive thinking is to have a globale variable count, then in the function clickMe to increase count by 1 when this function is called:   

```
let count = 0;
function clickMe(msg) {
    count += 1;
		console.log(`${msg} has been click ${count}`);
}
clickMe(`clickMe button`);
clickMe(`clickMe button`);
clickMe(`clickMe button`);

```   

Output:   
```
clickMe button has been click 1
clickMe button has been click 2
clickMe button has been click 3
```

It has the same result as in [my previouse post](https://vvlnote.github.io/what_i_know_about_javascript_closure). However, we all know, a global variable has a risk that anyone can access it, and change it unexpected. So the output may have unexpected result.   

*  OK, then I declare the variable count inside the function, so no one can access it unexpectedly, only when the clickMe() is called.  

```

function clickMe(msg) {
    let count = 0;
		console.log(`${msg} has been click ${count + 1}`);
}
```  

By looking at this code, everytime the function clickMe is called, count will be intialized to 0, so the output:  

`clickMe button has been click 1`

no matter how many times you call this function, the output is always displayed 1.  
* The next thing I can try is nested functions. A function is called nested when it is created inside another function. I can reorganize the code to as following:   

```
function clickMe(msg) {
    let count = 0;
		function clickCount() {
		    console.log(`${msg} has been click ${count + 1}`);
		}
		clickCount();
}
```

From above code, the result will be the same as mentioned before, since you are not able to access clickCount(), the only way to access clickCount() is from clickMe(), so everytime, you call clickMe(), the count is initialized to 0, so the result only display 
`clickMe button has been click 1`  

#### *  **Closure can resolve this issue, and also keep variable count as a private variable, no one outside the function can access it.  ** 

```
function clickMeWrap(msg) {
   let count = 0;
	 return function clickMe(){
	     console.log(`${msg} has been click ${++count}`);
	 }
}

let click = clickMeWrap('clickMe button ');
click();
click();
click();
```  
When clickMeWrap() is called, the function clickMe is returned and assigned to click. So everytime, click() is called, click() function can access varialbes msg, and count. So we can completed our goal, tracking how many times the button has been clicked, also keep the variables private.



* **Closures can be used to create stateful functions whose return values may be influenced by their internal state.**  

From the above function clickMeWrap(), I can modify it to return the value of count, so the count is modified by how many times the function is called. So it can return the state of clicking times. 

```
function clickMeWrap() {
   let count = 0;
	 return function clickMe(){
	     return ++count;
	 }
}
```  
So if your program needs to do the things based on the value of count, then in this case, you can have the value of the count to proceed your program to the next step.  

Normally the activation object of a function should be destroyed after the function is executed, however, closure keeps a reference to that object (in my example is count). So count is not destroyed after execution.


#### * **In functional programming, closures are frequently used for partial application & currying. **  

* **Partial application**: A function returning another function that might return another function, but each returned function can take serveral parameters. 

For example: I have a function that calculates the sum of 4 numbers.  
In general, I would code as following:  

```
function add4(a,b,c,d) {
    return a+b+c+d;
}

const result = add4(1,2,3,4);
```

I can convert this function into a partial function:     

```
function add4_partialFun(a) {
    return function add3(b,c,d){
        return a+b+c+d;
    }
}

const result = add4_parialFun(1)(2,3,4);
```



* **Currying**: A function returning another function that might return another function, but every returned function must take only one parameter at a time. Currying is a transformation of functions that translates a function from callable as f(a,b,c) into callable as f(a)(b)(c).  In other words, when a function, instead of taking all arguments at one time, thakes ther fist one and return a new function that takes the second one and returns a new function which takes the third one, and so forth, until all arguments have been fulfilled.  Please refer this post for the further information [Currying in JavaScript](https://codeburst.io/currying-in-javascript-ba51eb9778dc). 

I use the example above, and curry it:  

```
function add4_curry(a) {
    return function (b){
        return function(c) {
            return function(d){
                return a+b+c+d;
            }
        }
    }
}

const result = add4_curry(1)(2)(3)(4);
```  

**Reference**:   
[Understanding Closure in JavaScript](https://blog.bitsrc.io/a-beginners-guide-to-closures-in-javascript-97d372284dda)  
[Master the JavaScript Interview: What is a Closure?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36)
