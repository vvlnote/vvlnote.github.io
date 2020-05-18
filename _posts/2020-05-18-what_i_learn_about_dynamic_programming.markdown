---
layout: post
title:      "What I learn about Dynamic Programming"
date:       2020-05-18 04:00:13 +0000
permalink:  what_i_learn_about_dynamic_programming
---


This article is my own summary about Dynamic Programming algorithm. The first time I heard bout this term is from [What is Dynamic Programming and Hot wo use it by YK Sugishita](https://www.youtube.com/watch?v=vYquumk4nWw). 
He started with Fibonacci squence. We all know to resolve it by using recursion.   
 
```
const fibRecursive = function(n){
    if (n <= 2) return 1;
    return (fibRecursive(n-1) + fibRecursive(n-2)); 
}
```    

It looks pretty straight forward, the drawbacks are using a lot of computing power, and memory space. 



