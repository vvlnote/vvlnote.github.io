---
layout: post
title:      "Note of binary tree traverse and sorting algorithms"
date:       2020-01-27 01:04:19 +0000
permalink:  note_of_binary_tree_traverse_and_sorting_algorithms
---



#### This summary is based on the following to lay out the most popular algorithms of traversing of binary tree, and sortings. 

#### [https://levelup.gitconnected.com/must-know-algorithms-for-coding-interviews-937d807064e0](https://levelup.gitconnected.com/must-know-algorithms-for-coding-interviews-937d807064e0)


## Algorithms of Binary Tree Traversal

*   Tree traversal algorithm (for binary tree, and n-ary tree)

    A binary tree can be traversed in preorder, inorder, postorder or level-order.
    Among these traversal methods, preorder, postorder and level-order traversal are suitable for being extended to a N-ary tree.    

    - Pre-order  
		
```

function displayPreOrderRecursive(root) {
	function preOrderHelper(node){
		if (node != null) {
			console.log(`node = ${node.val}`);
			preOrderHelper(node.left);
			preOrderHelper(node.right);
		}
	}
	if (root == null){
		console.log(`this is an empty tree`);
	} else {
		preOrderHelper(root);
	}
}

```  

```

	 function displayPreOrderIterative() {
		//this will print out the root first, then left child, and right child
		// 1. Create an empty Stack
		// 2. Push the root into Stack
		// 3. Loop until Stack is empty
		// 4. Pop the last node and print its value
		// 5. Push right and left node if they are not null
		// 6. Repeat from step 4 to 6 again.

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

-  In-order

```
	function displayInOrderRecursive() {
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

```
	function displayInOrderIterative() {
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
  
- Post-order  

```
	function displayPostOrderRecursive() {
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

```
	function displayPostOrderIterative() {
		let stack1 = [];
		let stack2 = [];
		stack1.push(this.root);

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

		while (stack2.length > 0) {
			console.log(`node = ${stack2.pop().val}`);
		}
	}

```  

## Graph Search Algorithms
* Depth First Search (DFS)  
Reference: https://www.hackerearth.com/practice/algorithms/graphs/depth-first-search/tutorial/
* Breadth First Search(BFS)  
Reference: https://www.hackerearth.com/practice/algorithms/graphs/breadth-first-search/tutorial/






