---
layout: post
title:      "Magic Square 3x3"
date:       2020-01-13 01:43:29 +0000
permalink:  magic_square_3x3
---


While I was practicing my coding with [HackerRank](https://www.hackerrank.com/domains), I encounter a JavaScript coding problem, it is [Forming a Magic Square](https://www.hackerrank.com/challenges/magic-square-forming/problem).  In the post, I will focus on the 3x3 Magic Square. This is the constrain of this coding problem. 


### Definition  
   A magic square is an N×N grid of distinct positive numbers (from 1 to n^2) in which the entries in each row, column and main diagonal sum to the same number (equal to N(N^2+1)/2).  And this number is called the **magic constant**.

For example: for a  3x3 magic square, the sum of each row, column and main diagonal is 15.  The numbers in this magic square is from 1 to 9, there is no duplicated numbers. 

![MagicSquare 3x3](https://www.101computing.net/wp/wp-content/uploads/magic-square-3x3.png)    

### Algorithm to create a Magic Square 3x3
So far, I have found 2 ways to create a 3x3 Magic Square by depeding on where to put 1 in the Magic Square.

#### Place the number 1 at the center cell of top row (row = 0)  

#### Place the number 1 at the (n/2, n-1). In 3x3 Magic Square, place the number 1 at (row = 1, col = 2).

There are three conditions that need to be held:  
*  The postion of next number is moving diagonally up and right (i.e. decrementing row number of previous number by 1, and incrementing the column number of previous number by 1.)
*  If the position of next number is already contains a number, then move this next number to the row below current number (i.e the row number is row number of current number incremented by 1, and the col number of current number maintained unchanged.)
*  If the position of next number is out of the magic square (i.e. row number is -1, then move the next number 


