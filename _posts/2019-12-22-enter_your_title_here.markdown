---
layout: post
title:      "Enter your title here"
date:       2019-12-22 22:59:55 +0000
permalink:  enter_your_title_here
---


The content of your blog post goes here.

In the linear data structure, there are 4 ways of implmentations:  
* Array:  this is a random access data structure, where each elemement inside this array can be accessed directly and in O(1) time.   
* Linked List:   this is a sequencial access data structure, where each element can be access only in particular order, i.e. strting from head of the linked list.   
* Queue structure:  is a container of objects that are inserted and removed an object according to first-in first-out (aka FIFO) principle.   
* Stack Structure:  is a container of objexts that are inserted and removed an object accoring to last-in first-out (aka LIFO) principle.  

Note: Queue and Stack are considered as sequencial access data structure. due to each element can be accessed only in a particulare order. Refer to [Stacks and Queues](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Stacks%20and%20Queues/Stacks%20and%20Queues.html)

In this post, I am going to provide the basic implemenations for Queue and Stack in JavaScript.  

### Queue  (a.k.a FIFO)
In real life, the line of checkout in the grocery store, fast food store, post office, etc... is considere as queue.  These scenario is that the person in the front of line would be served first, and new coming person would stand at the end of line and be served after the person in front was served. The Queue data structure is mimicking the  same scenario, the object inserted first, would be removed first.  


### Stack  (a.k.a LIFO)
In real life, a pile of clean dish plates  in the cafeteria is considered as a stack. You get the toppest plate in this pile, and this topest plate is exactly the plate that was added most recently to the pile.  The Stack data structure is mimicking this same scenario, the obect insert last would be removed first.



