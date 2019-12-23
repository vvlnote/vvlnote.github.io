---
layout: post
title:      "Basic implemention of Queue and Stack in Javascript"
date:       2019-12-22 17:59:56 -0500
permalink:  enter_your_title_here
---


In the linear data structure, there are 4 ways of implmentations:  
* Array:  this is a random access data structure, where each elemement inside this array can be accessed directly and in O(1) time.   
* Linked List:   this is a sequencial access data structure, where each element can be access only in particular order, i.e. strting from head of the linked list.   
* Queue structure:  is a container of objects that are inserted and removed an object according to first-in first-out (aka FIFO) principle.   
* Stack Structure:  is a container of objexts that are inserted and removed an object accoring to last-in first-out (aka LIFO) principle.  

Note: Queue and Stack are considered as sequencial access data structure. due to each element can be accessed only in a particulare order. Refer to [Stacks and Queues](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Stacks%20and%20Queues/Stacks%20and%20Queues.html)

In this post, I am going to provide the basic implemenations for Queue and Stack in JavaScript.  

### Queue  (a.k.a FIFO)
In real life, the line of checkout in the grocery store, fast food store, post office, etc... is considere as queue.  These scenario is that the person in the front of line would be served first, and new coming person would stand at the end of line and be served after the person in front was served. The Queue data structure is mimicking the  same scenario, the object inserted first, would be removed first.  
In general, there are five basic functions provided by Queue:  
  * enqueue: add the object in to the queue . add the object into the end of the queue
  * dequeue: remove the frist object from the queue.  
  * front: to peek the first item in the queue,but does not remove it.  
  * isEmpty: to check if the queue is empty (without any object in the container), or not.  
  * clear: empty the queue.   
  
The following queue class is implemented in Array in JavaScript.  

```
class Queue {
	constructor() {
		this.container = [];
	}

	enqueue(element) {
		this.container.push(element);
	}

	dequeue() {
		if (isEmpty()) {
			return null;
		}
		return this.container.shift();
	}

	front() {
		return this.container[0];
	}

	isEmpty() {
		if (this.container.length == 0) {
			return true;
		}
		return false;
	}

	clear() {
		this.container.length = 0;
	}
}

```  
 

 


### Stack  (a.k.a LIFO or FILO)
In real life, a pile of clean dish plates  in the cafeteria is considered as a stack. You get the toppest plate in this pile, and this topest plate is exactly the plate that was added most recently to the pile.  The Stack data structure is mimicking this same scenario, the obect insert last would be removed first.  
In general, there are 4 functions are provided by Stack:
  * push: add the object into the top of stack.  
  * pop: remove the object from the top of stack.  
  * peak: return the top most of object from the stack, but does not remove it from the stack.  
  * isEmpty: to check if the Stack is empty or not.  

The following Stack class is implmented in Array.  

```
class Stack {
	contructor() {
		this.container = [];
	}

	push(element) {
		this.container.push(element);
	}

	pop(){
		if (isEmpty()) {
			return null;
		}
		return this.container.pop();
	}

	peek() {
		return this.container[this.container.length - 1];
	}

	isEmpty() {
		if (this.container.length == 0) {
			return true;
		}
		return false;
	}
}
```




