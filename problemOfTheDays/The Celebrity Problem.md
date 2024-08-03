### The Celebrity Problem

### A celebrity is a person who is known to all but does not know anyone at a party. A party is being organized by some people.  A square matrix mat is used to represent people at the party such that if an element of row i and column j is set to 1 it means ith person knows jth person. You need to return the index of the celebrity in the party, if the celebrity does not exist, return -1.

### Note: Follow 0-based indexing.

Examples:

Input: mat[][] = [[0 1 0],
                [0 0 0], 
                [0 1 0]]
Output: 1
Explanation: 0th and 2nd person both know 1. Therefore, 1 is the celebrity. 
Input: mat[][] = [[0 1],
                [1 0]]
Output: -1
Explanation: The two people at the party both know each other. None of them is a celebrity.
Expected Time Complexity: O(n2)
Expected Auxiliary Space: O(1)

Constraints:
1 <= mat.size()<= 3000
0 <= mat[i][j]<= 1

### Solution

```java
//{ Driver Code Starts
// Initial Template for Java

import java.io.*;
import java.util.*;

class GFG {
    public static void main(String args[]) throws IOException {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t > 0) {
            int N = sc.nextInt();
            int M[][] = new int[N][N];
            for (int i = 0; i < N; i++) {
                for (int j = 0; j < N; j++) {
                    M[i][j] = sc.nextInt();
                }
            }
            System.out.println(new Solution().celebrity(M));
            t--;
        }
    }
}
// } Driver Code Ends


// User function Template for Java

class Solution {
    // Function to find if there is a celebrity in the party or not.
    public int celebrity(int mat[][]) {
        // code here
        boolean containsZero=false;
        for(int[]e : mat){
             int numberOfZero = 0;
            for(int ele : e){
                if(ele == 0) numberOfZero++;
            }
            if(numberOfZero == e.length) containsZero = true; 
        }
        if(!containsZero) return -1;
        int n = mat.length;
        int m = mat[0].length;
        for(int i = 0;i<n;i++){
            boolean containsAllZero = true;
            for(int col = i;col<m;col++){
                if(mat[i][col] != 0) containsAllZero = false;
            }
            boolean everyBodyKnow =true;
            if(containsAllZero){
                // check for the each row but the coulum as i 
                for(int row =0; row < n; row++){
                    if(row!=i && mat[row][i] != 1){
                       everyBodyKnow = false;
                    } 
                }
            }
            if(containsAllZero== true && everyBodyKnow == true) return i;
            
        }
        return -1;
    }
    
}
```