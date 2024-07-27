### Floyd Warshall

The Floyd Warshall algorithm is used to find the shortest path between all pairs of vertices in a weighted graph. The graph may have negative weight edges, but no negative weight cycles (if a cycle has negative weight, then the shortest path is undefined). The algorithm is based on dynamic programming, and is similar to Dijkstra's algorithm. The algorithm has a time complexity of O(V^3), where V is the number of vertices in the graph.

### Algorithm

1. Initialize a 2D array `dist` of size V x V, where V is the number of vertices in the graph.
2. Initialize the diagonal of the `dist` array to 0, and the other elements to infinity.
3. For each edge (u, v) in the graph, update `dist[u][v]` to the weight of the edge.
4. For each pair of vertices (i, j), check if the path from i to j through each vertex k is shorter than the current path. If it is, update the distance.
5. The final `dist` array will contain the shortest path between all pairs of vertices.

### Code

Here is an implementation of the Floyd Warshall algorithm in Java:


```java
class Solution
{
    public void shortest_distance(int[][] matrix)
    {
        // Code here 
        for(int i = 0;i<matrix.length;i++){
            for(int j = 0;j<matrix.length;j++){
                if(matrix[i][j]==-1){
                    matrix[i][j] = 10000;
                }
            }
        }
        for(int via = 0;via<matrix.length;via++){
            for(int row = 0;row<matrix.length;row++){
                for(int col = 0;col<matrix[0].length;col++){
                     
                           matrix[row][col] = Math.min(matrix[row][col], matrix[row][via] + matrix[via][col]);
                      
                }
            }
        }
        for(int i = 0;i<matrix.length;i++){
            for(int j= 0;j<matrix.length;j++){
              if(matrix[i][j] == 10000){
                  matrix[i][j] =  -1;
              }
            }
        }
    }
}
```