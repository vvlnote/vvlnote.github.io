---
layout: post
title:      "Note about Pure Function "
date:       2020-04-06 00:00:52 +0000
permalink:  note_about_pure_function
---


My last technical interview, the interviewer asked me about Pure Function. It have been a while, so I would like to review it, and refresh myself.

### What is a Pure Function?  
The same input arguments, the function should return the same output result.  
The basic requirements of Pure Function is: 
* Should have input arguments.
* Should have return value.
* The return value is only depend on the input arguments. 
* The function dose not produce any side effects. 

For example:  
```
let count = 0;
function callMe(greeting) {
    console.log(`${greeting}`);
		return ++count;
}
```  
The above function is not a pure function. Even, there is a input argument (greeting), and output value (++acount).  It meets the top 2 requirments that mention above of Pure Function.  
However, even you pass in the same greeting everytime, the return value will be increase by 1, so the output value is not depend on the input argument.    
And also, this function has an observable side effect, the global variable (count)  is increased by 1 every time callMe function is called.   
So callMe(greeting) is not a Pure Function.  We can refer it as an impure function. 

Side Note: I would like to summarize from [Eric Elliot](https://medium.com/@_ericelliott) about [what is Function](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976)   
> What is a Function?
A function is a process which takes some input, called arguments, and produces some output called a return value.   
> Functions may serve the following purposes:
* **Mapping**: Produce some output based on given inputs. A function maps input values to output values.
* **Procedures**: A function may be called to perform a sequence of steps. The sequence is known as a procedure, and programming in this style is known as **procedural programming**.  
* **I/O**: Some functions exist to communicate with other parts of the system, such as the screen, storage, system logs, or network.
 
 ### Why is Pure Function important?   
*  It is the fundation of **Function Programming** (i.e. FP).  
*  Easy to move aroud in the code. so it can be reused all the time if the function is needed.
*  It is easy to refactor the pure functions to adapt to the future changes. Since Pure Function is not depend on the outside variable. 
