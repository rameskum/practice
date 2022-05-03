# SET MATRIX ZERO

## [**PROBLEM**](https://leetcode.com/problems/set-matrix-zeroes/)

Given an `m x n` integer matrix `matrix`, if an element is `0`, set its entire row and column to `0`'s.

You must do it **in place**.

## SOLUTION

### APPROACH 1

Check with your interviewer if all numbers are positive then, while traversing the matrix if you encounter a 0, you can
mark all non 0's elements of columns and rows as some negative number.

### APPROACH 2

Use auxiliary space, an array representing if zero is present in column and another for row.

> **TIME:** O(n x m) x (n + m) <br>
> **SPCACE** O(1)

### APPROACH 3

Inplace solution, using first row, and column to represent the 0 found indicator. A catch would be to handel the
intersecting cell (0, 0).

> **TIME:** O(n x m) <br>
> **SPCACE** O(n + m)

```java
class Solution {
	public void setZeroes(int[][] mat) {
		int m = mat.length;
		int n = mat[0].length;
		int col = 1;
		for (int i = 0; i < m; i++) {
			if (mat[i][0] == 0)
				col = 0;
			for (int j = 1; j < n; j++) {
				if (mat[i][j] == 0) {
					mat[i][0] = mat[0][j] = 0;
				}
			}
		}

		for (int i = m - 1; i >= 0; i--) {
			for (int j = n - 1; j >= 1; j--) {
				if (mat[i][0] == 0 || mat[0][j] == 0) {
					mat[i][j] = 0;
				}
			}
			if (col == 0)
				mat[i][0] = 0;
		}
	}
}
```

> **TIME:** O(n x m) <br>
> **SPCACE** O(1)
