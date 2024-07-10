### Maximal Squares


## Given an m x n binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

 

Example 1:


Input: matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
Output: 4
Example 2:


Input: matrix = [["0","1"],["1","0"]]
Output: 1
Example 3:

Input: matrix = [["0"]]
Output: 0



### Memoizations solution 

```java
class Solution {
    public int maximalSquare(char[][] matrix) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return 0;
        }

        int n = matrix.length;
        int m = matrix[0].length;
        Integer globalMax = Integer.MIN_VALUE;
        int[][] dp = new int[n][m];

        for (int[] row : dp) {
            Arrays.fill(row, -1);
        }

        for (int r = 0; r < n; r++) {
            for (int c = 0; c < m; c++) {
                if (matrix[r][c] == '1') {
                    globalMax = Math.max(globalMax, max(r, c, n, m, matrix, dp));
                }
            }
        }

        return globalMax * globalMax; // Return the area of the largest square
    }

    public static int max(int i, int j, int n, int m, char[][] mat, int[][] dp) {
        if (i >= n || j >= m) {
            return 0;
        }
        if (mat[i][j] == '0') {
            return 0;
        }
        if (dp[i][j] != -1) {
            return dp[i][j];
        }
        
        dp[i][j] = 1 + Math.min(Math.min(max(i + 1, j, n, m, mat, dp), max(i, j + 1, n, m, mat, dp)), max(i + 1, j + 1, n, m, mat, dp));
        
        return dp[i][j];
    }
}

```