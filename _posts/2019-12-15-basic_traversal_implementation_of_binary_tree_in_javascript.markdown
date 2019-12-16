---
layout: post
title:      "Basic Traversal implementation of Binary Tree in Javascript"
date:       2019-12-16 01:31:21 +0000
permalink:  basic_traversal_implementation_of_binary_tree_in_javascript
---



In this post, I would like to demonstrate about the basic traveral implement of a binary tree.
The followings are the topics that I would like to covert in the post.

1.  Why Binary Tree
2.  Terminology of Binary Tree
3.  The basic implemention of Binary Tree Traversal


## Why Binary Tree  
In general, we most deal with linear data structure, i.e. array, string, linked list, stack, queue, etc...  
Tree is considered as a non-linear data structure. And binary tree is a simple form of N-ary tree.  
  
Linear Data Structure :   
   * the data elements construct a sequence of a linear list.  
   * the data elements are adjacently attached to each other and in a speficied order.  
   * the memory to store linear data structure needs to be allocate in advance.
     
Non-linear Data Structure:  
  * it does not arrange the data consequtively, rather it is arraged in sorted order.  
  * that data elements can be attached to more than one element, and display as a hierarchical tree structure
  * memory utilzation is more efficiently than linear data structure, it does not require to declare memory in advance.
  
note: for the detail comparison between Linear data structure and Non-linear data structure - [Difference between Linear and Non-Linear Data Structure]((https://techdifferences.com/difference-between-linear-and-non-linear-data-structure.html)


## Terminology of Binary Tree
### Binary Tree
  A binary tree is a tree data structure. Each node contains max 2 child nodes associate with.  

  * **node:**  contain a data or value, and it has 2 branches, one connects to right child node (right), and the other connects to left child node (left).  
```
		let node = {
			val: val,
			left: null,
			right: null
		};
```
		
* In genel, there is no duplicate value in a binary tree
* **root node**: the toppest node of a tree is called the root node.  
* l**leaf node**: the node without child node connecting to it, it also can be called as **external node.**
* **internal node**: a node has at least one child node.
* **size of a binary tree:** refer to the number of nodes it has
* **level of a node**: the distance from a specific node to the root node is the level of that specific node.  
   i.e. the root is at level 0, the child nodes of root are at level 1, and so on.  
* **height of a binary tree**: the number of nodes on its longest branch (a path from the root to a leaf).
	 

### Type of Binary Tree  
* **Full Binary Tree**:   
     *     every node has 0 or 2 child nodes.  
     *     all nodes except leaf nodes has two child nodes.  
     *     the number of leaf nodes is internal nodes + 1.  
  
* **Complete Binary Tree**:  
     *    all levels, except possible the last level, have the maximu number of nodes.  
     *    all the nodes at the last level are filled from left to right.  
* **Balanced Binary Tree**:  
     *   the difference between heights of left and right sbutree is at most 1.  
* **Perfect Binary Tree**:  
    *  all internal nodes have two child nodes, and all leaf nodes are at the same level.  
    *  a hight h of a Perfect Binary tree has 2^h -1 nodes.   
* **Degenerate (or pathological) Tree**:
   *  every internal node has one child node.  
   *  the performance of this kind of tree is the same as linked list.  
     
## Binary Tree Traversal  
There are two types of traversal:   

  * 	Breadth first (Level Order).   
  * 	Depth first: preorder, inorder, and postorder.
  note: for better understanding each of the above methodologies, please refer to 
	[Binary tree traversal](https://leetcode.com/explore/learn/card/data-structure-tree/134/traverse-a-tree/992/)
	

  ### Preorder traversal
  Visit root node first, then left subtree, and right subtree.
   *   Recursive way:  
   ```
	displayPreOrderRecursive() {
		function preOrderHelper(node){
			if (node != null) {
				console.log(`node = ${node.val}`);
				preOrderHelper(node.left);
				preOrderHelper(node.right);
			}
		}
		if (this.root == null){
			console.log(`this is an empty tree`);
		} else {
			preOrderHelper(this.root);
		}
	}
```  

  
*  Iterative way: (with stack) .  
   Implementation:  
  1.  create an empty stack to store the nodes in the tree. stack is FILO procedure.
  2.  push the root node into the stack.
  3.  loop through the stack to process each node in the stack until the stack is empty.  
       Inside the while loop.  
     a. 	pop up the lastest node which was pushed into the stack. print out its value.  		
     b. 	push the right child of popped node into the stack. since we need to process the left child node then right child node (due to the nature of Stack).  
     c. 	push the left child of popped node into the stack.  	 

```
displayPreOrderIterative() {
    let stack = [];   
		stack.push(this.root);    
		while (stack.length > 0) {     
			let currentNode = stack.pop();   
			                                                                   
			console.log(`node = ${currentNode.val}`);  
			if (currentNode.right != null) {     
				stack.push(currentNode.right);     
			}
			if (currentNode.left != null) {      
				stack.push(currentNode.left);
			}
		}
	}
```

 ### Inorder Traversal  
 Visit left subtree first, then root node, the last is the right subtree.
 
*  Recursive way  

```
	displayInOrderRecursive() {
		function inOrderHelper(node) {
			if (node != null) {
				inOrderHelper(node.left);
				console.log(`node = ${node.val}`);
				inOrderHelper(node.right);
			}
		}
		if (this.root == null) {
			console.log(`empty tree`);
			return;
		} else {
			inOrderHelper(this.root);
		}
	};
```  
*  Iterative way (with stack)  
    Implemenation  
    1.  Create an empty stack.  
    2.  Initialize currentNode as root.  
    3.  push the currentNode into the stack.
    4.  Set the currentNode to the currentNode left child.
    5.  loop through if currentNode is not null or stack is not empty (the loop will be ended when currentNode is null and stack is empty).  
         a.  loop through left subtree of currentNode, until hit the leaf node. (the 2nd while loop).  
         b.  Pop the lastest item in the stack.  
         c.  Print the value of currentNode.   
         d.  Set the currentNode to the child node of currentNode.   
				 

```
	displayInOrderIterative() {
		let stack = [];
		let currentNode = this.root;
		stack.push(currentNode);
		currentNode = currentNode.left;

		while (stack.length > 0 || currentNode) {
			while(currentNode) {
				stack.push(currentNode);
				currentNode = currentNode.left;
			}

			currentNode = stack.pop();
			console.log(`node = ${currentNode.val}`);
			currentNode = currentNode.right;
		}
	}
```

### PostOrder Traversal 
Vist the left subtree first, then the right subtree, the last one visited is the root node.

* Recursive way:  

```
	displayPostOrderRecursive() {
		function postOrderHelper(node) {
			if (node != null) {
				postOrderHelper(node.left);
				postOrderHelper(node.right);
				console.log(`node = ${node.val}`);
			}
		}
		if (this.root == null){
			console.log(`this is an empty tree`);
		} else {
			postOrderHelper(this.root);
		}
	}
```
* Iterative way easy way (with 2 stacks)  
   Implementation
   1.  Push roo to first stack.  
   2.  Loop through the first stack until it is empty.  
       a.  Pop a node  from the first stack and push it to second stack.  
       b.  Push left and right child nodes to the popped node to first stack.   
   3. Loop through the second stack, and pop up each node in the second stack, and print out the value of  popped node until the second stack is empty.   
   
	Note: for detail information, please refer to [Iterative Postorder Traversal | Set 1 (Using Two Stacks](https://www.geeksforgeeks.org/iterative-postorder-traversal/)

```
	displayPostOrderIterative() {
		let stack1 = [];
		let stack2 = [];
		stack1.push(this.root);

		console.log(`    ===================Before push into 2nd stack====================`);
		while(stack1.length > 0) {
			let currentNode = stack1.pop();
			console.log(`node = ${currentNode.val}`);
			stack2.push(currentNode);
			if (currentNode.left != null){
				stack1.push(currentNode.left);
			}
			if (currentNode.right != null){
				stack1.push(currentNode.right);
			}
			
		}
		console.log(`    ==================After push into 2nd stack====================`);
		while (stack2.length > 0) {
			console.log(`node = ${stack2.pop().val}`);
		}
	}
```
### Level Order Traversal is the same as Breadth-first Traversal
This traversal starts at the root , and explores all of the nodes at the same level, then moving to the next level.

* Iterative way (use queue)  
   Implementation 
   1. Create an empty queue. (queue is FIFO process).  
   2. Push the root node into the queue (root node is at level 0).  
   3. Loop through the queue until it is an empty queue.  
       a.  Dequeue a node from queue.   
       b.  Print out the value of the dequeued node.  
       c.  Equeue the left child noe and right child noe of the dequeued node.   			 
			 

```
	displayLevelOrderIterative(){
		let queue = [];
		queue.push(this.root);
		while (queue.length > 0) {
			let currentNode = queue.shift();
			console.log(`node = ${currentNode.val}`);
			if (currentNode.left){
				queue.push(currentNode.left);
			}
			if (currentNode.right) {
				queue.push(currentNode.right);
			}

		}
	}
```
Note: for reference the code [github code](https://github.com/vvlnote/Practice)

