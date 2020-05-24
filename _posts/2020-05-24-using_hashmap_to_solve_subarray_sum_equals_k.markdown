---
layout: post
title:      "Using Hashmap to solve Subarray Sum Equals K"
date:       2020-05-24 21:31:50 +0000
permalink:  using_hashmap_to_solve_subarray_sum_equals_k
---



This post is regarding to solve the LeetCode problem: Subarray Sum Equals K.

The problem is:  
Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

Example 1:

Input:nums = [1,1,1], k = 2
Output: 2
 

Constraints:

The length of the array is in range [1, 20,000].
The range of numbers in the array is [-1000, 1000] and the range of the integer k is [-1e7, 1e7].  

My first try is :

```
var subarraySum = function(nums, k) {
    let count = 0;
    let ans = 0;
    let index = 0; 
    let i = 0; 
    while (index < nums.length) {
        count += nums[i];
        if (count === k) {
            ans += 1;
            count = 0;
            index += 1;
            i = index;
        } else if (count < k) {
            i += 1;
        } else if ( count > k) {
            count = 0; 
            index += 1
            i = index;
        }
        if (i === nums.length ) {
            index += 1; 
            i = index;
            count = 0;
        }
    }
    return ans;
		}
```   

When I ran the code, the sample test case: nums = [1,1,1], k = 2.  The result is correct.

However, when I tried to run the full set of test cases, I failed at this test case:  nums = [28,54,7,-70,22,65,-6], k = 100.  

I reviewed my code one more time, my original assumptions are not right: 
* I expect the next number is always bigger than the current number, so when it reach count = k,  I  reset the count, and restart the starting point (i.e. index in the code)
* I did not expect there are negative number in the array.  
* I did not expect the nums array contains 0s (this is a conner case).   

By correcting my previous assumptions, I made the change to my code, the following is my second trail:

```
var subarraySum = function(nums, k) {
    let count = 0;
    let ans = 0;
    let index = 0; 
    let i = 0; 
    
    while (index < nums.length) {
        count += nums[i];
        if (count === k) {
            ans += 1;
        } 
        i += 1;
        if (i === nums.length) {
            index += 1;
            i = index;
            count = 0;
        }
    }
    return ans;
};
```  

From the above code, since I did not expect the next number is either bigger, smaller or 0 compared to current number, the code continued to run through all the remaining numbers from the starting (the index in the code) to the end. So this time, all the test cases are past. However, it ran 5% faster than other submitted code. This algorithm is not very effieicnt. The time complexity is O(n^2), space complexity  is O(1) constant space is used.   

Since this problem can be solved by using the Hashmap, I would try to convert my code into the Hashmap.  


```
var subarraySum = function(nums, k) {
    let numMap = new Map();
    let ans = 0;
    let count = 0;
    numMap.set(0, 1);
    for (let i = 0; i < nums.length; i++) {
        count += nums[i];

        let temp = numMap.get(count - k);
        if (temp !== undefined) {
            ans += temp;
        }
       if (numMap.get(count) === undefined) {
            numMap.set(count, 1);
        } else {
            numMap.set(count, numMap.get(count)  + 1);
        }
    }
    return ans;
```

The time complexity is O(n), space complexity is O(n).


