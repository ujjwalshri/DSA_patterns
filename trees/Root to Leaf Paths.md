### Root to Leaf Paths


### Given a Binary Tree of nodes, you need to find all the possible paths from the root node to all the leaf nodes of the binary tree.

Example 1:

Input:
       1
    /     \
   2       3
Output: 
1 2 
1 3 
Explanation: 
All possible paths:
1->2
1->3
Example 2:

Input:
         10
       /    \
      20    30
     /  \
    40   60
Output: 
10 20 40 
10 20 60 
10 30 
Your Task:
Your task is to complete the function Paths() which takes the root node as an argument and returns all the possible paths. (All the paths are printed in new lines by the driver's code.)

Expected Time Complexity: O(n)
Expected Auxiliary Space: O(height of the tree)

Constraints:
1<=n<=104


```java
class Solution {
    public static ArrayList<ArrayList<Integer>> Paths(Node root) {
        // code here
         ArrayList<ArrayList<Integer>> allPaths = new ArrayList();
         helper(root, new ArrayList(),allPaths);
         return allPaths;
        
    }
    public static Node helper(Node root, ArrayList<Integer> path, ArrayList<ArrayList<Integer>> allPaths){
        if(root==null) return null;
        path.add(root.data);
        Node left = helper(root.left, path, allPaths);
        Node right = helper(root.right, path, allPaths);
        if(left==null && right==null){
            allPaths.add(new ArrayList(path));
        }
        path.remove(path.size()-1);
        return root;
    }
}
        

```