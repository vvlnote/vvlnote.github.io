---
layout: post
title:      "Treaps ?! - Part 1"
date:       2020-02-02 19:49:31 -0500
permalink:  treaps_-_part_1
---


### What is Treaps?  
> In short, Treap is simply a Self-balancing binary search tree., but of  course, much cooler. 

### Why should I get into this topic?  
I have continued practice code challenge of algorithms and data structure on .  
I practice them on [Hackerrank](https://www.hackerrank.com/dashboard). The following coding problem was what I encounter : [Array and simple queries](https://www.hackerrank.com/challenges/array-and-simple-queries/problem).  

### Problem  

Given two numbers N and M . N indicates the number of elements in the arrayA[] (1-indexed)  and  M indicates number of queries. You need to perform two types of queries on the array .

You are given  M queries. Queries can be of two types, type 1 and type 2.

Type 1 queries are represented as 1* i j* : Modify the given array by removing elements from *i* to *j* and adding them to the front.

Type 2 queries are represented as 2* i j* : Modify the given array by removing elements from *i* to *j* and adding them to the back.

Your task is to simply print the absolute value of  A[1] - A[N] of the resulting array after the execution of M queries followed by the resulting array.

Note While adding at back or front the order of elements is preserved.  

#### Analyze  
* You will be given an array of size N.  
* The array is 1-based (instead of 0-based).  
* There are 2 type of implemenations:  
    *  query type is 1, you need to add the subarray that indicated in the query in the front of array.  
    *  query type is 2, you need to add the subarray that indicated in the query at the end of the array.  

It is very clear.

#### My code  

```
function processData(input) {
    //Enter your code here
    let iArr = input.split('\n');
    for (let i = 0; i < iArr.length; i ++) {
        let temp = iArr[i].split(' ');
        iArr[i] = temp;
    }
    let n = iArr[0][0];
    let ans = iArr[1];
    for (let i = 2; i < iArr.length; i ++) {
        let start = iArr[i][1] - 1;
        let end = iArr[i][2];
        let length = end - start;
        let subArr = ans.splice(start, length);
        switch (iArr[i][0]){
            case '1':
            ans.unshift(...subArr);
            break;
            case '2':
            ans.push(...subArr);
            break;
        }
    }
    console.log(Math.abs(ans[0] - ans[n-1]));
    console.log(ans.join(' '));
} 
```

#### Result  
There are total 26 test cases, and only 15 test cases are passed, and 11 test cases are time out. 
The time complexity is O(n) for the for loop. however, since I used Array.splice(), the time complexity is O(n). 
Sicne Array.splice() is inside the for loop. so the time complexity is O(n^2).  

And based on the Constraints:
N, M can be 10^5

For the big numbers to be processed, O(n^2) is very hard to complete the implementation within the time liminted. 
So I need to optimize my code.   

Sicne this coding problem is under Data Structures > Balanced Tree. How can I utilize balanced tree to optimize my code? By reading dicussion. Some smart people suggested use implicity Treaps. 

What is Treaps? And how can I utilize this data structure to optimize my code. 
Will be continued. 





