---
layout: post
title:      "Magic Square 3x3"
date:       2020-01-12 20:43:30 -0500
permalink:  magic_square_3x3
---


While I was practicing my coding with [HackerRank](https://www.hackerrank.com/domains), I encounter a JavaScript coding problem, it is [Forming a Magic Square](https://www.hackerrank.com/challenges/magic-square-forming/problem).  In the post, I will focus on the 3x3 Magic Square. This is the constrain of this coding problem. 


### Definition  
   A magic square is an N×N grid of distinct positive numbers (from 1 to n^2) in which the entries in each row, column and main diagonal sum to the same number (equal to N(N^2+1)/2).  And this number is called the **magic constant**.

For example: for a  3x3 magic square, the sum of each row, column and main diagonal is 15.  The numbers in this magic square is from 1 to 9, there is no duplicated numbers. 

![MagicSquare 3x3](https://www.101computing.net/wp/wp-content/uploads/magic-square-3x3.png)    

### Algorithm to create a Magic Square 3x3
So far, I have found 2 ways to create a 3x3 Magic Square by depeding on where to put 1 as a starting point in the Magic Square.

#### Place the number 1 at the center cell of top row (row = 0, colum = n/2)  
Algorithm:  
* Start at the middle of the top row, and with number 1.  
* Insert number n into the current grid position.  
* If the number is equal to 9 (3x3), this Magic Square is completed and stop. Otherwise increment number n.  
* Move diagonally up and right based on one of the following conditions:
    - wrapping to the first column if column of new position equals n, and row sitll within the Magic Square.
    - wrapping to the last row if row of new postion equals to -1, and column still within the Magic Square.
    - the row and column of new position are all out the Magic Square (row = -1, and column = n),  insert the next number into the cell under the current number.    
    - if the new position is already occupied with number, insert the next number into the cell under the current number.  
    - if the new position is empty, insert the next number into this position.  



Please refer to the following code:  
```
	let i = 1;
	let currentRow = 0;
	let currentCol = 1;
	while (i <= n*n) {
		if (i == 1) {
			//start to create a magicSquare 3x3
			//this starting number should be placed in the row = 0, column = 1
			magicSquare[currentRow][currentCol] = 1;
		} else {
			let nextRow = currentRow - 1;
			let nextCol = currentCol + 1;

			if (nextRow >= 0) {
				if (nextCol < n) {
					if (magicSquare[nextRow][nextCol] != 0) {
						//next cell is occupied
						currentRow += 1;
					} else {
						currentRow -= 1;
						currentCol += 1;
					}
				} else {
					currentCol = 0;
					currentRow -= 1;
				}
			} else if (nextRow < 0) {
				if (nextCol < n) {
					currentRow = n-1;
					currentCol += 1;
				} else {
					currentRow += 1;
				}
			}
			magicSquare[currentRow][currentCol] = i;
		}
		i += 1;
	}
```
#### Place the number 1 at the (n/2, n-1). In 3x3 Magic Square, place the number 1 at (row = 1, col = 2).
Algorithm:  
* Start at the position (n/2, n-1), and with number 1.  
* Insert number n into the current grid position.  
* If the number is equal to 9 (3x3), this Magic Square is completed and stop. Otherwise increment number n.  
* Move diagonally up and right based on one of the following conditions:
    - wrapping to the first column if column of new position equals n, and row sitll within the Magic Square.
    - wrapping to the last row if row of new postion equals to -1, and column still within the Magic Square.
    - the row and column of new position are all out the Magic Square (row = -1, and column = n),  insert the next number into the cell left side of  the current number.    
    - if the new position is already occupied with number, insert the next number into the cell lef side of  the current number.  
    - if the new position is empty, insert the next number into this position.  

Please refer to the following code:  

```
	//starting point (number 1) at position (n/2, n-1)
	let currentRow = Math.floor(n/2);
	let currentCol = n-1;
	let i = 1;

	while (i <= n*n) {
		if (i == 1) {
			magicSquare[currentRow][currentCol] = i;
		} else {
			let nextRow = currentRow - 1;
			let nextCol = currentCol + 1;

			if (nextRow >= 0) {
				if (nextCol < n) {
					if (magicSquare[nextRow][nextCol] != 0) {
						currentCol -= 1;
					} else {
						currentRow -= 1;
						currentCol += 1;
					}
				} else {
					currentRow -= 1;
					currentCol = 0;
				}
			} else if (nextRow < 0) {
				if (nextCol < n) {
					currentRow = n - 1;
					currentCol += 1;
				} else {
					currentCol -= 1;
				}
			}
			magicSquare[currentRow][currentCol] = i;
		}
		i += 1;
	}
```

If you are interested in the history of Magic Square, there is a Wiki Page [Magic Squrare](https://en.wikipedia.org/wiki/Magic_square) with detial information about what is Magic Square and the history of Magic Square. Hopefully, you can enjoy it.

