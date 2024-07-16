### Rat in a Maze Problem - I

### Consider a rat placed at (0, 0) in a square matrix of order N * N. It has to reach the destination at (N - 1, N - 1). Find all possible paths that the rat can take to reach from source to destination. The directions in which the rat can move are 'U'(up), 'D'(down), 'L' (left), 'R' (right). Value 0 at a cell in the matrix represents that it is blocked and rat cannot move to it while value 1 at a cell in the matrix represents that rat can be travel through it.
### Note: In a path, no cell can be visited more than one time. If the source cell is 0, the rat cannot move to any other cell.


Input:
N = 4
m[][] = {{1, 0, 0, 0},
         {1, 1, 0, 1}, 
         {1, 1, 0, 0},
         {0, 1, 1, 1}}
Output:
DDRDRR DRDDRR
Explanation:
The rat can reach the destination at 
(3, 3) from (0, 0) by two paths - DRDDRR 
and DDRDRR, when printed in sorted order 
we get DDRDRR DRDDRR.
Example 2:
Input:
N = 2
m[][] = {{1, 0},
         {1, 0}}
Output:
-1
Explanation:
No path exists and destination cell is 
blocked.



### Optimized recursive solution 

```java
class Solution {
    public static int N;
    public static ArrayList<String> findPath(int[][] m, int n) {
        // Your code here
        N= n;
        if(m[n-1][n-1] != 1 ){
            ArrayList<String> list = new ArrayList();
            list.add("-1");
            return list;
        }
        
        ArrayList<String> outer = new ArrayList();
        
        helper(m, 0, 0, outer, new StringBuilder());
        return outer;
        
    }
    public static void helper(int[][] m, int row, int col, ArrayList<String> outer, StringBuilder path){
        if(row == N-1 && col== N-1 ) {
            outer.add(path.toString());
            return;
        }
        if(row < 0 || row >= N || col < 0 || col>= N) return;
        // call left
        if( col-1 >= 0 && m[row][col-1]==1){
            helper(m, row, col-1, outer,path.append('L'));
        }
        if(col+1 < N && m[row][col+1]==1){
            helper(m, row, col+1, outer,path.append('R'));
        }
        if(row+1 < N && m[row+1][col]==1){
            helper(m, row+1, col, outer,path.append('D'));
        }
        if( row-1 >=0 && m[row-1][col]==1){
            helper(m, row-1, col, outer,path.append('U'));
        }
        path.
       
    }
}
```