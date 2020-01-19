---
layout: post
title:      "Experience of solving the Count Triplets coding challenge in JavaScript"
date:       2020-01-19 17:58:50 +0000
permalink:  experience_of_solving_the_count_triplets_coding_challenge_in_javascript
---



### This post is inspired by [How to solve the Sherlock and Anagrams coding challenge in JavaScript by Mihail Gaberov](https://www.freecodecamp.org/news/how-to-solve-the-sherlock-and-anagrams-coding-challenge-in-javascript-a80baa908637/). I would like to share my experience about how to construct my thoughts, and optimized my code to pass the time constraints. This coding challenge is called “[Count Triplets.](https://www.hackerrank.com/challenges/count-triplets-1?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=dictionaries-hashmaps)”  


## Problem

You are given an array and you need to find number of tripets of indices **_(i, j, k)_ **such that the elements at those indices are in [geometric progression](https://en.wikipedia.org/wiki/Geometric_progression) for a given common ratio **_r_** and **_i < j < k_**.

For example, **_arr = [1,4,16, 64]_**. If **_r = 4_**, we have**_ [1, 4, 16] _**and **_[4, 16, 64]_** at indices **_(0, 1, 2)_** and **_(1, 2, 3)_**.


#### Input Parameters



*   arr : an array of integers
*   r: an integer, the common ratio


#### Constrains



*   1 ≤ n ≤ 10<sup>5    </sup>n is the size of arr
*   1 ≤ r ≤ 10<sup>9  </sup>  r is the ratio
*   1 ≤ arr[i] ≤ 10<sup>9 </sup> the each number inside array is between 1 to 10<sup>9</sup>


#### Output Format  

   Return the count of triplets that form a geometric progression.  




## Analyze

In order for myself to have a better understanding, I need to have the following information:



*   What is geometric progression
*   Is the array sorted or not

What I know from the description of problem, and the constraints: 



*   From the constraints, the performance of your algorithm needs to put into consideration. O(n<sup>3</sup>) won’t pass the testing.
*   From the output, we do not need to list all the combinations that result from the program, we only need to have a count of all the combination. So original index of each element does not need to be kept. So we can sort the array if that is needed.


#### Geometric Progression

"In [mathematics](https://en.wikipedia.org/wiki/Mathematics), a **geometric progression**, also known as a **geometric sequence**, is a [sequence](https://en.wikipedia.org/wiki/Sequence) of [numbers](https://en.wikipedia.org/wiki/Number) where each term after the first is found by multiplying the previous one by a fixed, non-zero number called the _common ratio_. For example, the sequence 2, 6, 18, 54, ... is a geometric progression with common ratio 3. Similarly 10, 5, 2.5, 1.25, ... is a geometric sequence with common ratio 1/2.

Examples of a geometric sequence are [powers](https://en.wikipedia.org/wiki/Exponentiation) _r<sup>k</sup>_ of a fixed number _r_, such as [2k](https://en.wikipedia.org/wiki/Power_of_two) and 3<sup><em>k</em></sup>. The general form of a geometric sequence is  

 *ar*,  *ar<sup>2</sup>*,  *ar<sup>3</sup>*,* ar<sup>4</sup>*.....  

	


where _r_ ≠ 0 is the common ratio and _a_ is a [scale factor](https://en.wikipedia.org/wiki/Scale_factor), equal to the sequence's start value."

 

#### How does it work in our problem?

From the example:

arr = [1, 3, 9, 9, 27, 81], r = 3 (this is "common ratio" that indicates in the quote above)

We start from the first element: 1, in order to form a geometric sequence with 3 elements, we need to do

1st element of the geometric sequence is 1

2nd element of the geometric sequence is 1 * r = 1 * 3 = 3

3rd element of the geometric sequence is 2nd element * r = 1*r*r = 1*3*3 = 1 * 3<sup>2</sup> (this is ar<sup>2 </sup> in   *ar*,  *ar<sup>2</sup>*,  *ar<sup>3</sup>*,* ar<sup>4</sup>*.....  ) . 


The first geometric sequence is [1, 3, 9], this combination can be formed by indices [0, 1, 2] and [0, 1, 3]. 

And we need to go through each element until the element at the last 3th one. 


#### Is the arr sorted or not ?

In the description of Problem, it does not mentioned, so we can assume that the arr is not sorted. Also we can not sort the arr due to the requirement **_i < j < k. _**If we sort the arr, then **_i < j < k _** can not be a guarantee. 


## Solution



1. Build a hashMap. Key is the element in the array, and value is an array to keep the index of this number shown in the array. Go through each element in this array, and store the index of this element in the right place in hashMap. 
2. A for loop to go through each key in the hashMap  
    a. The current element is the first number in the geometric sequence.  
    b. The 2nd number in the geometric sequence is current element * ratio.  
    c. The 3rd number in the geometric sequence is the 2nd number in the geometric * ratio.  
    d. Locate these 3 numbers in the hashMap, and get the index array of each number.    
    e. Use these 3 arrays to calculate the total of geometric sequences.  
3. Return the total amount after loop through all the elements.  


#### Build HashMap

This is a helper function to have the same number is located in the position in the hashMap as a key, and the index indicates this number will be kept in the index of array of the number.`  `


```
   let hashMap = {};
   for (let i = 0; i < arr.length; i ++){
       let num = arr[i];
       if (hashMap[num]){
           hashMap[num].push(i);
       } else {
           hashMap[num] = [];
           hashMap[num].push(i);
       }
   }
   return hashMap;
```


Go through each element of the array, and put each element in the hashMap, it is O(N).

Look up / retrieve a particular  element in hashMap is it O(1).


#### A for loop to go through each key in the hashMap


```
   let count = 0;

   for (const numKey in numIndices) {
       let num1 = parseInt(numKey);
       let num2 = num1 * r;
       let num3 = num2 * r;
       let num1Arr = numIndices[num1];
       let num2Arr = numIndices[num2];
       let num3Arr = numIndices[num3];
      
       if (num2Arr && num3Arr) {
           for (let i = 0; i < num1Arr.length; i ++){
               if (num1Arr[i] < num2Arr[num2Arr.length - 1]){
                   for (let j = 0; j < num2Arr.length; j++) {
                       if (num2Arr[j] < num3Arr[num3Arr.length - 1]){
                           if (num2Arr[j] > num1Arr[i]){
                               let index = -1;
                               for (let k = 0; k < num3Arr.length; k++){
                                   if (num3Arr[k] > num2Arr[j]) {
                                       index = k;
                                       break;
                                   }
                               }
                               if (index > -1) {
                                   count += num3Arr.slice(index).length;
                               }
                           }
                       }
                   }
               }
           }
       }
   }
```


Note: numIndices is the hashMap that we built before.

When I run my code against the test cases, there are 3 out of 12 are failed. The failure is due to time out. So I know that the algorithm is OK, but not efficient enough. 

Even we use hashMap, but we still need to go through 3 layer of loops, which is O(N<sup>3</sup>), this algorithm is not optimized. So Google search is a good friend, you can find all kinds of information from it. 

Please refer [APPROACHES TO THE HACKERRANK COUNT TRIPLETS PROBLEM](https://brokensandals.net/hackerrank-count-triplets/). it has a solution of O(N). 

## Conclusion
There is alsways better solution than what you  expected. However, each coding challenge is not only practice the skill of using this languase, it also help you to analyze the problem in logic way, and based on the information you can get from the description, input paraments, output requirements, and constrains you can figure out what assumptions that you can make, and what needs to watch out while yo plot your algorithm. Even though I did not pass all the test cases, it could mean I need to use more efficient way to solve problem, or it could be there were corner cases that I did not put into consideration. And refer to other developers' code or blog, it is still a good way to teach yourself can think different approach. Do not be afraid of failure, you can learn from the failure, and make that experience for advancing yourself.
