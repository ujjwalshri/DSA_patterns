### Spirally traversing a matrix

### You are given a rectangular matrix, and your task is to return an array while traversing the matrix in spiral form.

Examples:

Input: matrix[][] = [[1, 2, 3, 4],
                  [5, 6, 7, 8],
                  [9, 10, 11, 12],
                  [13, 14, 15,16]]
Output: [1, 2, 3, 4, 8, 12, 16, 15, 14, 13, 9, 5, 6, 7, 11, 10]
Explanation:

Input: matrix[][] = [[1, 2, 3, 4],
                  [5, 6, 7, 8],
                  [9, 10, 11, 12]]
Output: [1, 2, 3, 4, 8, 12, 11, 10, 9, 5, 6, 7]
Explanation: Applying same technique as shown above, output for the 2nd testcase will be 1 2 3 4 8 12 11 10 9 5 6 7.
Expected Time Complexity: O(n2)
Expected Auxiliary Space: O(n2)

Constraints:
1 <= matrix.size(), matrix[0].size() <= 100
0 <= matrix[i][j]<= 100



### Optimized Approach:

```java
class Solution {
    // Function to return a list of integers denoting spiral traversal of matrix.
    public ArrayList<Integer> spirallyTraverse(int matrix[][]) {
        // code here
        int n = matrix.length;
        int m = matrix[0].length;
        int top = 0;
        int bottom = n-1;
        int left = 0;
        int right = m-1;
        int d = 0; // 0 means right // 1 means left // 2// means down // 3 means up
        ArrayList<Integer> spiralTraversal = new ArrayList();
        while(top <= bottom && left <= right){
            if(d==0){
                for(int i = left ;i<=right;i++){
                    spiralTraversal.add(matrix[top][i]);
                }
                d = 2;
                top++;
            }else if(d==2){
                for(int i =top ; i<=bottom;i++){
                    spiralTraversal.add(matrix[i][right]);
                }
                d = 1;
                right--;
            }else if(d==1){
                for(int i = right;i>=left;i--){
                    spiralTraversal.add(matrix[bottom][i]);
                }
                bottom--;
                d = 3;
            }else if(d==3){
                for(int i = bottom;i>=top;i--){
                    spiralTraversal.add(matrix[i][left]);
                }
                left++;
               d = 0;
            }
            
        }
        return spiralTraversal;
    }
}
```


