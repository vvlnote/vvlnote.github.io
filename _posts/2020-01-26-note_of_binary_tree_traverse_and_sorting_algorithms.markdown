---
layout: post
title:      "Note of binary tree traverse and sorting algorithms"
date:       2020-01-26 20:04:20 -0500
permalink:  note_of_binary_tree_traverse_and_sorting_algorithms
---



#### This summary is based on the following to lay out the most popular algorithms of traversing of binary tree, and sortings. 

 [https://levelup.gitconnected.com/must-know-algorithms-for-coding-interviews-937d807064e0](https://levelup.gitconnected.com/must-know-algorithms-for-coding-interviews-937d807064e0)


## Algorithms of Binary Tree Traversal

*   Tree traversal algorithm (for binary tree, and n-ary tree)

    A binary tree can be traversed in preorder, inorder, postorder or level-order.
    Among these traversal methods, preorder, postorder and level-order traversal are suitable for being extended to a N-ary tree.    

* Pre-order  
		
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

*  In-order

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
  
   *    Post-order  

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


## Search Algorithms  

* Binary Search  
    * Time Complexity:  
       Sorted tree => average is O(n)
       Sorted list is O(log(n))  
			 
```

function binarySearch(nums, targetedNum) {
	nums.sort((a, b) => a-b); //ensure the nums is sorted array
	let leftIndex = 0;
	let rightIndex = nums.length - 1;

	let middleIndex = Math.floor((leftIndex + rightIndex)/2);

	while (rightIndex > leftIndex) {
		if (nums[middleIndex] == targetedNum) {
			return middleIndex;
		} else {
			if (nums[middleIndex] > targetedNum) {
				rightIndex = middleIndex - 1;
			} else {
				leftIndex = middleIndex + 1;
			}
			middleIndex = Math.floor((leftIndex + rightIndex)/2);

		}
	}
	return -1;
}

```  

```

function binarySearch_recursive(nums, targetdNum) {
	nums.sort((a,b) => a-b);

	function bSearchHelper(nums, l, r, tNum) {
		if (r >= l) {
			let middleIndex = Math.floor((l + r)/2);
			if (nums[middleIndex] == tNum) return middleIndex;
			if (nums[middleIndex] > tNum) {
				r = middleIndex - 1;
			} else {
				l = middleIndex + 1;
			}
			return bSearchHelper(nums, l, r, tNum);			
		}

		return -1;
	}

	return bSearchHelper(nums, 0, nums.length-1, targetdNum);
}

```  

## Sorting Algorithms

### Bubble Sort  
* Space Complexity:   
   O(1), sorting in place  
* Time Complexity:  
   Best Case => O(n)  
	 Average / Worst Case => O(n^2)  
* Reference: [Bubble Sort](https://medium.com/javascript-algorithms/javascript-algorithms-bubble-sort-3d27f285c3b2)  
* Algorithm:  
     * It is the simplest sorting algorithm.
     * Repeatedly swapping the adjacent elements if they are in the wrong order.  


```
function bubbleSort(unsortedArr) {
	console.log(`unsorted Arr = ${unsortedArr}`);
	let swap = false;
	let iteration = 0;

	for (let i = 0; i < unsortedArr.length - 1; i ++) {
		for (let j = 0; j < unsortedArr.length; j ++) {
			if (unsortedArr[j] > unsortedArr[j+1]) {
				swap = true;
				let temp = unsortedArr[j];
				unsortedArr[j] = unsortedArr[j+1];
				unsortedArr[j+1] = temp;
			}			
		}
		iteration += 1;
	}
	console.log(`iteration = ${iteration}, sortedArr = ${unsortedArr}`);
}
```  

### Insertion Sort  
*  Space Complexity:
   O(1), sorting in place.  
*  Time complexity:  
    Best case is O(n). or linear, which occurs if the input array is already sorted.    
		Average/Worst case O(n2), not efficient, and not should be used for large lists or array.  
*  Because of insertion sort's low hidden constant value, however, it usually outperforms more advanced algorithms such as quick sort, or merge sort on smaller lists or array.  
*  In practice, insertion sort is also usually more efficient than other quadratic (O(n2)) sorting algorithms, such as bubble sort and selection sort.  
*  It is stable and adaptive.
    A stable sorting algorithm is any algorithm that won't change the relative order of items in a list that have the same value.
    Adaptive => it works well with arrays that are arleady partially or fully sorted.  
*  Algorithm:  
   Works by moving from left to right over the input list.
Scan the input array from left to right , select each element as you go and moving it to the position where the value of the element to it's left would be smaller or equal to the value of the element you select. After you move the element to the right, you'll be left with a set of elements that has been sorted in ascending order.   

```
function insertionSort(arr) {
	if (arr == null || arr.length <= 1) return arr;

	console.log(`unsorted array = ${arr}`);


	for (let i = 1; i < arr.length; i++){
		let currentIndex = i;
		let currentValue = arr[currentIndex];
		let j = i - 1;
		while(j >= 0 &&  arr[j] > currentValue){
			arr[j+1] = arr[j];
			j -= 1;
		}
		arr[j+1] = currentValue;
	}
	console.log(`sorted array = ${arr}`);
}
```   

### Selection Sort
* Space Complexity:
  O(1), sorting in place.  
* Time Complexity:  
   Best / Average /Worst Case is O(n^2).  
* Algorithm:
  This is very simple and easy to implement.  
	Loop through the input array linearly, selecting the first smallest element, and swap it to the first position
Then you loop through the array again using a linear scan and get the 2nd smallest element, swap it to the second position, and so on and so forth until your array is completely sorted.  

```

function selectionSort(arr) {
	console.log(`Unsorted Array = ${arr}`);
	let startingIndex = 0;
	while (startingIndex < arr.length){
		let minIndex = startingIndex;
		for (let i = startingIndex + 1; i < arr.length; i++){
			if (arr[minIndex] > arr[i]) {
				minIndex = i;
			}
		}
		if (minIndex != startingIndex) {
			console.log(`minValueIndex = ${minIndex}, 
				startingIndex = ${startingIndex} `);
			let temp = arr[startingIndex];
			arr[startingIndex] = arr[minIndex];
			arr[minIndex] = temp;
		}
		startingIndex += 1;
	}
	console.log(`Selection Sorting => ${arr}`);
}

```    

### Merge Sort
* Space Complextiry:
   O(n), sorting is not in place. 
	 The space complexity of this algorithm is actually greater than most, and are not commonly used in larger systems where space is at a premium 
* Time Complexity:  
   Best / Average / Worst Case : O(n log n)
* Reference: [Merge Sort]((https://medium.com/javascript-in-plain-english/javascript-merge-sort-3205891ac060)  
* Algorithm: this is a Divide and Conquer algorithm  
  It divides input array in two halves, call itself for the two halves and then merges the two sorted halves.
The merge function is used for merging two halves.   
  The merge function is the key process that assume the left halves and right halves are all sorted, and merges the two sorted sub-arrays into one.  


```
function mergeSort(unsortedArr) {
	if (unsortedArr == null || unsortedArr.length <= 1) return unsortedArr;

	let m = Math.floor(unsortedArr.length/2);

	let left = (unsortedArr.slice(0, m));
	let right = (unsortedArr.slice(m));

	let sortedArr =  merge(mergeSort(left), mergeSort(right));
	console.log(sortedArr);
	return sortedArr;

}

function merge(left, right) {
	let sortedArr = [];
	let leftIndex = 0;
	let rightIndex = 0;

	while(leftIndex < left.length && rightIndex < right.length) {
		if (left[leftIndex] < right[rightIndex]) {
			sortedArr.push(left[leftIndex]);
			leftIndex += 1;
		} else {
			sortedArr.push(right[rightIndex]);
			rightIndex += 1;
		}
	}
	return sortedArr.concat(left.slice(leftIndex)).concat(right.slice(rightIndex));
}
```  

### Quick Sort
* Space Complexity:  
   Not using addition storage
* Time Complexity: 
   Best / Average case: O(n log n)
	 Worst case: O(n^2)  
	 The O(n^2) run time can occur if the pivot element used in each iteration of quicksort is nowhere near the median value in the array that is being ordered.   
* In practice, Quick Sort will typically run 2-3x faster than merge sort when both are achieving their average run time. 
* Reference:  
* Algorithm:  
  
```

function quickSort_recursive(arr){
	if (arr == null || arr.length <= 1) return arr;

	let left = [];
	let right = [];
	let newArr = [];
	let pivot = arr.pop();

	for (let i = 0; i < arr.length; i++){
		if (arr[i] > pivot) {
			right.push(arr[i]);
		} else {
			left.push(arr[i]);
		}
	}

	return newArr.concat(quickSort_recursive(left), pivot, quickSort_recursive(right));
}

```


	
  
 
	 
	 
   

 
 








