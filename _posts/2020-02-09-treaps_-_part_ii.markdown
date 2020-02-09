---
layout: post
title:      "Treaps ?! - Part II"
date:       2020-02-09 18:48:36 -0500
permalink:  treaps_-_part_ii
---


## Treap = Tree + Heap  
As suggested by name, Treap is the combination of Tree and Heap.  Teap is a ***Self-balancing Binary Search Tree*** or a ***Randomized Binary Search Tree***.  

Treap is a data structure which combines binary tree and binary heap.

#### Binary Search Tree  
A binary serach tree has the following properties:
* It is a binary tree, so each parent node has no more than 2 child nodes.  
* The value of root is less or equal to its right subtree, and is bigger than its left subtree. 

However, when we inserting / deleting nodes on the tree can make the tree unbalanced. The tree could be one subtree containing the most of  tree nodes, then the search may turn out to be a linear search (which is O(n)) instead of average case O(log n).  Then it defect the purpose of Binary Search tree.  

#### Binary Heaps 
A binary heap has the following properties:  
* It is a complete binary tree which satisfies the heap ordering property.  
* The ordering can be of following two types:  
    + The *min-heap property*: the value of each node is greater than or equal to the value of its parent, with the minimum-value element at the root.  
    + The *max-heap property*: the value of each node is less than or equal to the value of its parent, with the maximum-value element at the root.  
* A heap *is not a sorted structure* . There is no particulare relationship among nodes on any given level, even among the siblings.  
* A heap with N nodes always has O(log N) height due to it is a complete binary tree.  
* A common use of a heap is to implement a priority queue.  



Note:  
**Priority Queue**   
It is an extension of Queue having the following properties:
* Each element of the priority queue has an proprty associated with it.  
* Elements are added to teh queue as per the priority.  
* Lowest priority elements are removed first. (it is min-heap property).  


For more detail, please refer to : [Binary Heaps](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Binary%20Heaps/heaps.html)


#### Treap  
Treap is a data structure that stores pairs (B, H) in a binary tree in such a way that it is a binary search tree by B, which is the data value of each node, and a binary heap by H, which is a unique numberical priority that is assigned at random to this node.  

If some node of the tree contains values (B0, H0), all nodes in the left subtree have B < B0, all nodes in the right subtree have B > B0, and all nodes in both left and right subtree have H < H0.  With this kind of assignment, the expected htight of the resulting tree is O(log N). This is main idea behind Treaps.!

![Node in Treap](https://qph.fs.quoracdn.net/main-qimg-feec686c2f7acad33a7a5e143cc3f4f2.webp)  



